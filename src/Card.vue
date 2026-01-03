<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  card: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['flip'])

function handleClick() {
  emit('flip', props.card)
}
</script>

<template>
  <div 
    class="card"
    :class="{ 
      'flipped': card.isFlipped || card.isMatched,
      'matched': card.isMatched 
    }"
    @click="handleClick"
  >
    <div class="card-inner">
      <div class="card-front">
        <span class="card-symbol">{{ card.symbol }}</span>
      </div>
      <div class="card-back">
        <span>?</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  position: relative;
  aspect-ratio: 1;
  cursor: pointer;
  perspective: 1000px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.card.flipped .card-inner {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  font-size: 2rem;
  font-weight: bold;
}

.card-front {
  background: white;
  transform: rotateY(180deg);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.card-back {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.card:hover:not(.flipped) .card-inner {
  transform: scale(1.05);
}

.card.matched .card-front {
  background: #d4edda;
  border: 3px solid #28a745;
}

.card-symbol {
  font-size: 3rem;
}

@media (max-width: 600px) {
  .card-symbol {
    font-size: 2rem;
  }
}
</style>