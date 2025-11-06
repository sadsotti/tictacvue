<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    value: {
        type: String,
        required: true
    },
    rowIndex: {
        type: Number,
        required: true
    },
    colIndex: {
        type: Number,
        required: true
    },
    isWinning: {
        type: Boolean,
        default: false
    }
});

const emit = defineEmits(['click-cell']);
const handleClick = () => {
    emit('click-cell', props.rowIndex, props.colIndex);
};
</script>

<template>
    <div
        class="square-modern"
        @click="handleClick"
        :class="{
            'x-mark-modern': value === 'X',
            'o-mark-modern': value === 'O',
            'winning-cell': isWinning
        }"
    >
        {{ value }}
    </div>
</template>