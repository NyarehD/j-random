<script setup>
import { ref, computed } from 'vue'
const currentRandom = ref([]);
const hiragana = ref([
  "a",
  "i",
  "u",
  "e",
  "o",
  "ka",
  "ki",
  "ku",
  "ke",
  "ko",
  "sa",
  "shi",
  "su",
  "se",
  "so",
  "ta",
  "chi",
  "tsu",
  "te",
  "to",
  "na",
  "ni",
  "nu",
  "ne",
  "no",
  "ha",
  "hi",
  "fu",
  "he",
  "ho",
  "ma",
  "mi",
  "mu",
  "me",
  "mo",
  "ya",
  "yu",
  "yo",
  "ra",
  "ri",
  "ra",
  "re",
  "ro",
  "wa",
  "wo",
  "n",
]);
function randomizer() {
  currentRandom.value = [];
  Math.random(...hiragana.value);
}
</script>

<template>
  <button @click.prevent="randomizer">Generate random</button>
  <p v-for="item in currentRandom" :key="item">{{item}}</p>
</template>

<style scoped>
</style>
