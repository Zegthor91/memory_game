<script setup>

import { ref } from 'vue'
import DifficultySelector from './DifficultySelector.vue'

const showDifficultySelector = ref(false)

function startNewGame() {
  showDifficultySelector.value = true
}

function showHistory() {
  alert('Historique - à implémenter plus tard')
}
</script>

<template>
  <div class="home-container">
    <div class="fruit-background">
      <!-- Gros fruits -->
      <span class="fruit fruit-big fruit-1">🍎</span>
      <span class="fruit fruit-big fruit-2">🍊</span>
      <span class="fruit fruit-big fruit-3">🍋</span>
      <span class="fruit fruit-big fruit-4">🍇</span>
      <span class="fruit fruit-big fruit-5">🍓</span>
      <span class="fruit fruit-big fruit-6">🍉</span>
      <span class="fruit fruit-big fruit-7">🍌</span>
      <span class="fruit fruit-big fruit-8">🍑</span>
      
      <!-- Petits fruits -->
      <span class="fruit fruit-small fruit-9">🍒</span>
      <span class="fruit fruit-small fruit-10">🍎</span>
      <span class="fruit fruit-small fruit-11">🍊</span>
      <span class="fruit fruit-small fruit-12">🍇</span>
      <span class="fruit fruit-small fruit-13">🍓</span>
    </div>

    <h1 class="game-title">Memory Game</h1>

    <div v-if="!showDifficultySelector" class="menu">
      <button @click="startNewGame" class="menu-button">
        Nouvelle Partie
      </button>
      <button @click="showHistory" class="menu-button">
        Historique
      </button>
    </div>

    <DifficultySelector v-else />
  </div>
</template>

<style scoped>
.home-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 20px;
  position: relative;
  overflow: hidden;
}

.fruit-background {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

.fruit {
  position: absolute;
  opacity: 0.4;
  animation: float 20s infinite ease-in-out;
}

.fruit-big {
  font-size: 8rem;
}

.fruit-small {
  font-size: 3rem;
  opacity: 0.3;
}

/* Gros fruits */
.fruit-1 {
  top: 10%;
  left: 10%;
  animation-delay: 0s;
}

.fruit-2 {
  top: 20%;
  right: 15%;
  animation-delay: -3s;
}

.fruit-3 {
  top: 60%;
  left: 5%;
  animation-delay: -6s;
}

.fruit-4 {
  top: 70%;
  right: 10%;
  animation-delay: -9s;
}

.fruit-5 {
  top: 40%;
  left: 20%;
  animation-delay: -12s;
}

.fruit-6 {
  top: 80%;
  left: 50%;
  animation-delay: -15s;
}

.fruit-7 {
  top: 15%;
  left: 50%;
  animation-delay: -18s;
}

.fruit-8 {
  top: 50%;
  right: 5%;
  animation-delay: -21s;
}

/* Petits fruits */
.fruit-9 {
  top: 5%;
  left: 30%;
  animation-delay: -2s;
}

.fruit-10 {
  top: 25%;
  left: 5%;
  animation-delay: -5s;
}

.fruit-11 {
  top: 55%;
  right: 25%;
  animation-delay: -8s;
}

.fruit-12 {
  top: 85%;
  left: 20%;
  animation-delay: -11s;
}

.fruit-13 {
  top: 30%;
  right: 8%;
  animation-delay: -14s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
  }
  25% {
    transform: translateY(-20px) rotate(5deg);
  }
  50% {
    transform: translateY(0) rotate(0deg);
  }
  75% {
    transform: translateY(20px) rotate(-5deg);
  }
}

.game-title {
  color: white;
  font-size: 3rem;
  margin-bottom: 3rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  position: relative;
  z-index: 1;
}

.menu {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  width: 100%;
  max-width: 300px;
  position: relative;
  z-index: 1;
}

.menu-button {
  padding: 1rem 2rem;
  font-size: 1.2rem;
  font-weight: bold;
  color: white;
  background: rgba(255, 255, 255, 0.2);
  border: 2px solid white;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.menu-button:hover {
  background: rgba(255, 255, 255, 0.3);
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.menu-button:active {
  transform: translateY(0);

}

</style>