<script setup>
import { ref } from 'vue'
import DifficultySelector from '../DifficultySelector.vue'

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
}

.game-title {
  color: white;
  font-size: 3rem;
  margin-bottom: 3rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.menu {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  width: 100%;
  max-width: 300px;
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
