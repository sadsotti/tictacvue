<script setup>
import Game from './components/Game.vue';
import './assets/style.css'; 
</script>

<template>
  <main>
    <Game />
  </main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap');

:root {
    --bg-color-light: linear-gradient(135deg, #f0e6fa, #c5d8f2);
    --bg-color-dark: linear-gradient(135deg, #1e272e, #34495e);
}

body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh; 
  background: var(--bg-color-dark); 
  font-family: 'Permanent Marker', cursive; 
  color: #ecf0f1;
  overflow-x: hidden;
  transition: background 0.3s ease;
}

body.light-theme {
    background: var(--bg-color-light);
    color: #2c3e50;
}

#app {
  width: 100%;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

main {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>