<template>
  <div class="container">
    <div class="row justify-content-center py-4">
      <div class="col-4">
        <div class="input-group mb-3 justify-content-center">
          <div class="input-group">
            <div class="input-group-text">
              <input class="form-check-input mt-0" type="checkbox" v-model="isInline"
                aria-label="Checkbox for following text input">
            </div>
            <input type="text" class="form-control" aria-label="Text input with checkbox" v-model.number="times"
              @keypress.enter="randomizer">
          </div>
        </div>
      </div>
      <div class="col-12">
        <div v-if="isInline">
          <span v-for="(item, i) in currentRandom" :key="i" class="text-big"
            :class="{ 'text-break': isInline }">{{ item }}</span>
        </div>
        <div v-else>
          <p v-for="(item, i) in currentRandom" :key="i" class="text-center text-big">{{ item }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue"
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
const currentRandom = ref([]);
const isInline = ref(true);
const times = ref(5);
const hiragana = [
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
];
function randomizer() {
  currentRandom.value = [];
  for (let i = 0; i < times.value; i++) {
    currentRandom.value.push(hiragana[Math.round(Math.random() * (hiragana.length - 1))])
  }
}
onMounted(() => {
  randomizer();
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.text-big {
  font-size: 80px;
}
</style>
