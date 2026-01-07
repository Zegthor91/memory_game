<script setup>
import { ref, computed, onMounted } from 'vue'
import Card from './Card.vue'

const props = defineProps({
  difficulty: {
    type: Object,
    required: true
  }
})

// État du jeu
const cards = ref([])
const flippedCards = ref([])
const matchedPairs = ref([])
const attempts = ref(0)
const timer = ref(0)
const gameInterval = ref(null)

// Créer le jeu
function createGame() {
  const symbols = ['🍎', '🍌', '🍇', '🍊', '🍓', '🍉', '🍒', '🍑', 
                   '🥝', '🥑', '🍍', '🥭', '🍋', '🥥', '🫐', '🍈', 
                   '🍐', '🥬']
  
  const numberOfPairs = props.difficulty.pairs
  const selectedSymbols = symbols.slice(0, numberOfPairs)
  
  // Créer les paires
  const cardPairs = [...selectedSymbols, ...selectedSymbols]
  
  // Mélanger les cartes
  cards.value = cardPairs
    .map((symbol, index) => ({
      id: index,
      symbol: symbol,
      isFlipped: false,
      isMatched: false
    }))
    .sort(() => Math.random() - 0.5)
}

// Retourner une carte
function flipCard(card) {
  // Ne rien faire si la carte est déjà retournée ou appariée
  if (card.isFlipped || card.isMatched || flippedCards.value.length === 2) {
    return
  }
  
  // Retourner la carte
  card.isFlipped = true
  flippedCards.value.push(card)
  
  // Si 2 cartes sont retournées, vérifier si elles correspondent
  if (flippedCards.value.length === 2) {
    attempts.value++
    checkMatch()
  }
}

// Vérifier si les cartes correspondent
function checkMatch() {
  const [card1, card2] = flippedCards.value
  
  if (card1.symbol === card2.symbol) {
    // C'est une paire !
    card1.isMatched = true
    card2.isMatched = true
    matchedPairs.value.push(card1.symbol)
    flippedCards.value = []
    
    // Vérifier si le jeu est terminé
    if (matchedPairs.value.length === props.difficulty.pairs) {
      endGame()
    }
  } else {
    // Pas une paire, retourner les cartes après un délai
    setTimeout(() => {
      card1.isFlipped = false
      card2.isFlipped = false
      flippedCards.value = []
    }, 1000)
  }
}

// Démarrer le chronomètre
function startTimer() {
  gameInterval.value = setInterval(() => {
    timer.value++
  }, 1000)
}

// Terminer le jeu
function endGame() {
  clearInterval(gameInterval.value)
  setTimeout(() => {
    const username = prompt('Bravo ! Entrez votre pseudo :')
    if (username) {
      alert(`Félicitations ${username} !\nTemps : ${formatTime.value(timer.value)}\nEssais : ${attempts.value}`)
    }
  }, 500)
}

// Formater le temps
const formatTime = computed(() => {
  return (seconds) => {
    const mins = Math.floor(seconds / 60)
    const secs = seconds % 60
    return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`
  }
})

// Initialiser le jeu au montage du composant
onMounted(() => {
  createGame()
  startTimer()
})
</script>

<template>
  <div class="game-container">
    <div class="game-header">
      <h2>Memory Game - {{ difficulty.label }}</h2>
      <div class="game-stats">
        <div class="stat">
          <span class="stat-label">Temps:</span>
          <span class="stat-value">{{ formatTime(timer) }}</span>
        </div>
        <div class="stat">
          <span class="stat-label">Essais:</span>
          <span class="stat-value">{{ attempts }}</span>
        </div>
        <div class="stat">
          <span class="stat-label">Paires:</span>
          <span class="stat-value">{{ matchedPairs.length }}/{{ difficulty.pairs }}</span>
        </div>
      </div>
    </div>

    <div 
      class="game-board" 
      :style="{ 
        gridTemplateColumns: `repeat(${difficulty.size}, 1fr)`,
        gridTemplateRows: `repeat(${difficulty.size}, 1fr)`
      }"
    >
      <Card
        v-for="card in cards"
        :key="card.id"
        :card="card"
        @flip="flipCard"
      />
    </div>
  </div>
</template>

<style scoped>
.game-container {
  width: 100%;
  max-width: 800px;
  padding: 20px;
}

.game-header {
  margin-bottom: 2rem;
  text-align: center;
}

.game-header h2 {
  color: white;
  font-size: 2rem;
  margin-bottom: 1rem;
}

.game-stats {
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.stat {
  background: rgba(255, 255, 255, 0.2);
  padding: 0.8rem 1.5rem;
  border-radius: 10px;
  backdrop-filter: blur(10px);
}

.stat-label {
  color: rgba(255, 255, 255, 0.9);
  font-size: 0.9rem;
  margin-right: 0.5rem;
}

.stat-value {
  color: white;
  font-size: 1.1rem;
  font-weight: bold;
}

.game-board {
  display: grid;
  gap: 10px;
  max-width: 600px;
  margin: 0 auto;
  aspect-ratio: 1;
}
</style>