<template>
    <div class="box5">
    <div class="progress-container">
        <q-circular-progress
            show-value
            font-size="16px"
            :value="progress"
            
            :thickness="0.2"
            color="primary"
            track-color="grey-3"
            class="q-ma-md"
        >
        <q-spinner-oval slot="internal-unbounded" />
      </q-circular-progress>
      <p v-if="progress === 100">Song generation complete!</p>
    </div>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const props = defineProps({
    isGenerating: Boolean
  })
  
  const progress = ref(0)
  const timer = ref(null)
  
  watch(
    () => props.isGenerating,
    (isGenerating) => {
      if (isGenerating) {
        startProgressBar()
      } else {
        stopProgressBar()
      }
    }
  )
  
  const startProgressBar = () => {
    progress.value = 0
    timer.value = setInterval(() => {
      progress.value += 10
      if (progress.value >= 100) {
        stopProgressBar()
      }
    }, 500)
  }
  
  const stopProgressBar = () => {
    clearInterval(timer.value)
    progress.value = 100
  }
  </script>
  
  <style lang="scss" scoped>
  .q-circular-progress{
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100%;
    }
    .progress-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100%;
    }
  </style>