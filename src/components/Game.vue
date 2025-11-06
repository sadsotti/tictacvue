<script setup>
import { ref } from 'vue';
import Board from './Board.vue';

const board = ref([
    ['', '', ''],
    ['', '', ''],
    ['', '', '']
]);
const currentPlayer = ref('X');
const winner = ref(null);
const winningCells = ref([]); 

const currentTheme = ref('dark'); 

const toggleTheme = () => {
    currentTheme.value = currentTheme.value === 'dark' ? 'light' : 'dark';
};

const checkWin = () => {
    const b = board.value;
    const p = currentPlayer.value;
    
    const winningSequences = [
        [[0, 0], [0, 1], [0, 2]], [[1, 0], [1, 1], [1, 2]], [[2, 0], [2, 1], [2, 2]],
        [[0, 0], [1, 0], [2, 0]], [[0, 1], [1, 1], [2, 1]], [[0, 2], [1, 2], [2, 2]],
        [[0, 0], [1, 1], [2, 2]], [[0, 2], [1, 1], [2, 0]]
    ];
    
    for (const sequence of winningSequences) {
        const [[r1, c1], [r2, c2], [r3, c3]] = sequence;
        
        if (b[r1][c1] === p && b[r2][c2] === p && b[r3][c3] === p && p !== '') {
            winningCells.value = sequence; 
            return true;
        }
    }
    
    return false;
};

const checkDraw = () => {
    return !winner.value && board.value.flat().every(cell => cell !== '');
};

const makeMove = (row, col) => {
    if (board.value[row][col] === '' && !winner.value) {
        board.value[row][col] = currentPlayer.value;
        
        if (checkWin()) {
            winner.value = currentPlayer.value;
        } else if (checkDraw()) {
            winner.value = 'Draw';
        } else {
            currentPlayer.value = currentPlayer.value === 'X' ? 'O' : 'X';
        }
    }
};

const resetGame = () => {
    board.value = [['', '', ''], ['', '', ''], ['', '', '']];
    currentPlayer.value = 'X';
    winner.value = null;
    winningCells.value = []; 
};
</script>

<template>
  <div class="tic-tac-toe-modern" :class="currentTheme">
    
    <div class="header-controls">
        <h1 class="game-title">
            <span class="tictactoe-text">tictac</span>
            <span class="vue-v">v</span>
            <span class="vue-u">u</span>
            <span class="vue-e">e</span>
        </h1>
        <button @click="toggleTheme" class="theme-toggle-button">
            {{ currentTheme === 'dark' ? '☀️ Light Mode' : '🌙 Dark Mode' }}
        </button>
    </div>

    <h2 class="game-status" v-if="winner && winner !== 'Draw'">
      🎉 Winner is: <span :class="{'x-player': winner === 'X', 'o-player': winner === 'O'}">{{ winner }}</span>!
    </h2>
    <h2 class="game-status" v-else-if="winner === 'Draw'">It's a Draw! 🤝</h2>
    <h2 class="game-status" v-else>Turn for: <span :class="{'x-player': currentPlayer === 'X', 'o-player': currentPlayer === 'O'}">{{ currentPlayer }}</span></h2>

    <Board
        :board="board"
        :winning-cells="winningCells"
        :winner="winner"
        @cell-clicked="makeMove"
    />

    <button @click="resetGame" class="reset-button-modern">New Game</button>
  </div>
</template>