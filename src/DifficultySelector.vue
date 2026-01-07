<script setup>
import { ref } from 'vue'
import Game from './Game.vue'

const selectedDifficulty = ref(null)
const gameStarted = ref(false)

const difficulties = [
  { level: '4x4', size: 4, rows: 4, cols: 4, pairs: 8, label: 'Facile' },
  { level: '4x5', size: 4, rows: 4, cols: 5, pairs: 10, label: 'Moyen' },
  { level: '6x6', size: 6, rows: 6, cols: 6, pairs: 18, label: 'Difficile' }
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
  color: #2c3e50;
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
  background: white;
  border: 2px solid #3498db;
  border-radius: 12px;
  padding: 2rem 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-align: center;
}

.difficulty-card:hover {
  background: #3498db;
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(52, 152, 219, 0.3);
}

.difficulty-card:hover h3,
.difficulty-card:hover .grid-size,
.difficulty-card:hover .pairs-count {
  color: white;
}

.difficulty-card h3 {
  color: #2c3e50;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  transition: color 0.3s ease;
}

.grid-size {
  color: #3498db;
  font-size: 2rem;
  font-weight: bold;
  margin: 0.5rem 0;
  transition: color 0.3s ease;
}

.pairs-count {
  color: #7f8c8d;
  font-size: 0.9rem;
  margin: 0;
  transition: color 0.3s ease;
}
</style>