<script setup>
import { defineProps, defineEmits } from 'vue';
import Cell from './Cell.vue';

const props = defineProps({
    board: { 
        type: Array,
        required: true
    },
    winningCells: { 
        type: Array,
        default: () => []
    },
    winner: { 
        type: [String, null],
        default: null
    }
});

const emit = defineEmits(['cell-clicked']);
const isWinningCell = (row, col) => {
    return props.winningCells.some(coord => coord[0] === row && coord[1] === col);
};

const handleCellClick = (rowIndex, colIndex) => {
    emit('cell-clicked', rowIndex, colIndex);
};
</script>

<template>
    <div class="board-modern">
        <template v-for="(row, rowIndex) in board" :key="rowIndex">
            <Cell
                v-for="(cellValue, colIndex) in row"
                :key="colIndex"
                :value="cellValue"
                :row-index="rowIndex"
                :col-index="colIndex"
                :is-winning="isWinningCell(rowIndex, colIndex)"
                @click-cell="handleCellClick"
            />
        </template>
    </div>
</template>