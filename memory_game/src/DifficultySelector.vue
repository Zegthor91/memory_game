<script setup>
import { ref } from 'vue'
import Game from '../views/Game.vue'

const selectedDifficulty = ref(null)
const gameStarted = ref(false)

const difficulties = [
  { level: '4x4', size: 4, pairs: 8, label: 'Facile' },
  { level: '5x5', size: 5, pairs: 12, label: 'Moyen' },
  { level: '6x6', size: 6, pairs: 18, label: 'Difficile' }
]

function selectDifficulty(difficulty) {
  selectedDifficulty.value = difficulty
  gameStarted.value = true
}
</script>

<template>
  <div v-if="!gameStarted" class="difficulty-container">
    <h2 class="difficulty-title">Choisissez la difficulté</h2>
    
    <div class="difficulty-grid">
      <div 
        v-for="difficulty in difficulties" 
        :key="difficulty.level"
        @click="selectDifficulty(difficulty)"
        class="difficulty-card"
      >
        <h3>{{ difficulty.label }}</h3>
        <p class="grid-size">{{ difficulty.level }}</p>
        <p class="pairs-count">{{ difficulty.pairs }} paires</p>
      </div>
    </div>
  </div>

  <Game 
    v-else 
    :difficulty="selectedDifficulty" 
  />
</template>

<style scoped>
.difficulty-container {
  width: 100%;
  max-width: 600px;
}

.difficulty-title {
  color: white;
  font-size: 2rem;
  margin-bottom: 2rem;
  text-align: center;
}

.difficulty-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1.5rem;
}

.difficulty-card {
  background: rgba(255, 255, 255, 0.2);
  border: 2px solid white;
  border-radius: 12px;
  padding: 2rem 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  text-align: center;
}

.difficulty-card:hover {
  background: rgba(255, 255, 255, 0.3);
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
}

.difficulty-card h3 {
  color: white;
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.grid-size {
  color: white;
  font-size: 2rem;
  font-weight: bold;
  margin: 0.5rem 0;
}

.pairs-count {
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.9rem;
  margin: 0;
}
</style>
