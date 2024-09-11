<template>
    <div class="container">
      <div class="game">
        <h1>Tic-Tac-Toe Game</h1>
        <div class="board">
          <div
            v-for="(cell, index) in board"
            :key="index"
            class="cell"
            @click="makeMove(index)"
          >
            {{ cell }}
          </div>
        </div>
        <p v-if="winner">{{ winner }} wins!</p>
        <p v-else-if="isDraw">It's a draw!</p>
        <button @click="resetGame">Reset Game</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        board: Array(9).fill(""),
        currentPlayer: "X",
        winner: null,
        isDraw: false,
      };
    },
    methods: {
      makeMove(index) {
        if (!this.board[index] && !this.winner) {
          this.$set(this.board, index, this.currentPlayer);
          this.checkWinner();
          if (!this.winner) {
            this.switchPlayer();
          }
        }
      },
      switchPlayer() {
        this.currentPlayer = this.currentPlayer === "X" ? "O" : "X";
      },
      checkWinner() {
        const winningCombinations = [
          [0, 1, 2],
          [3, 4, 5],
          [6, 7, 8],
          [0, 3, 6],
          [1, 4, 7],
          [2, 5, 8],
          [0, 4, 8],
          [2, 4, 6],
        ];
  
        for (const combination of winningCombinations) {
          const [a, b, c] = combination;
          if (this.board[a] && this.board[a] === this.board[b] && this.board[a] === this.board[c]) {
            this.winner = this.board[a];
            return;
          }
        }
  
        if (!this.board.includes("")) {
          this.isDraw = true;
        }
      },
      resetGame() {
        this.board = Array(9).fill("");
        this.currentPlayer = "X";
        this.winner = null;
        this.isDraw = false;
      },
    },
  };
  </script>
  
  <style>
  /* Center the game in the middle of the page */
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  
  .game {
    text-align: center;
  }
  
  .board {
    display: grid;
    grid-template-columns: repeat(3, 100px);
    grid-gap: 5px;
    margin: 20px auto;
  }
  
  .cell {
    width: 100px;
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2em;
    border: 1px solid black;
    cursor: pointer;
  }
  </style>
  