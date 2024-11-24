<script setup>
import { ref } from "vue"

const blueScore = ref(0)
const redScore = ref(0)
const isFullScreen = ref(false)

const resetScore = () => {
  blueScore.value = 0
  redScore.value = 0
}

const toggleFullscreen = () => {
  const element = document.getElementById("fullscreen-content");

  // Check if fullscreen is currently active
  if (!document.fullscreenElement) {
    // Request fullscreen for the element
    element.requestFullscreen().then(() => {
      isFullScreen.value = true
    }).catch((err) => {
      console.error("Error attempting to enable fullscreen mode:", err);
    });
  } else {
    // Exit fullscreen mode
    document.exitFullscreen().then(() => {
      isFullScreen.value = false
    }).catch((err) => {
      console.error("Error attempting to exit fullscreen mode:", err);
    });
  }
}
</script>

<template>
  <main class="board-container" id="fullscreen-content">
    <nav>
      <button class="control-btn" @click="blueScore > 0 ? blueScore-- : blueScore = 0">
        <font-awesome-icon icon="minus" />
      </button>

      <button class="control-btn" @click="resetScore">
        <font-awesome-icon icon="rotate-left"/>
      </button>
      
      <button class="control-btn" @click="redScore > 0 ? redScore-- : redScore = 0" >
        <font-awesome-icon icon="minus" />
      </button>
    </nav>

    <button @click="blueScore++" class="score-btn blue-btn">
      {{blueScore}}
    </button>
    <!-- <div>clock</div> -->
    <button @click="redScore++" class="score-btn red-btn">
      {{redScore}}      
    </button>

    <button 
      class="floating-btn"
      @click="toggleFullscreen"
    >
      <font-awesome-icon :icon=" isFullScreen ? 'minimize': 'expand'" />
    </button>
  </main>
</template>

