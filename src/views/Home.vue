<script setup>
import { ref } from "vue"

const blueScore = ref(0)
const redScore = ref(0)

const resetScore = () => {
  blueScore.value = 0
  redScore.value = 0
}
</script>

<template>
  <main class="board-container">
    <nav>
      <button class="control-btn" @click="blueScore > 0 ? blueScore-- : blueScore = 0">
        <font-awesome-icon icon="minus" />
      </button>

      <button class="control-btn" @click="resetScore">
        <font-awesome-icon icon="rotate-left" @click="teste"/>
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
  </main>
</template>

