<template>
  <div class="row justify-content-center py-4">
    <div class="col-5">
      <div class="input-group justify-content-center">
        <div class="input-group">
          <span id="inputGroup-sizing-default" class="input-group-text">Number of Words</span>

          <input v-model.number="times" aria-label="Text input with checkbox" class="form-control" type="text"
            @keypress.enter="randomizer">
            <button class="btn btn-primary" @click="randomizer">Generate</button>
        </div>
      </div>
    </div>
    <div class="col-3">
      <div class="form-check">
        <input id="isInline" v-model="isInline" class="form-check-input" type="checkbox">
        <label class="form-check-label" for="isInline">Inline Text</label>
      </div>
    </div>
  </div>
  <div class="row justify-content-center  ">
    <div class="col-4">
      <WordType v-model="wordType" :is-checked="true" type="romaji">Romaji</WordType>
      <WordType v-model="wordType" type="hiragana">Hiragana</WordType>
      <WordType v-model="wordType" type="katakana">Katakana</WordType>
    </div>
  </div>
  <div class="row">
    <div class="col-12">
      <div v-if="isInline" class="text-center">
        <span v-for="(item, i) in currentRandomWords" :key="i" :class="{ 'text-break': isInline }"
          class="text-big">{{ item }}</span>
      </div>
      <div v-else>
        <p v-for="(item, i) in currentRandomWords" :key="i" class="text-center text-big">{{ item }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import hiragana from "../words/hiragana.json";
import katakana from "../words/katakana.json";
import WordType from "../components/WordType.vue"

const currentRandomIndexes = ref([]);
const isInline = ref(true);
const times = ref(5);
const wordType = ref("romaji");
const testing = ref("What is this testing?")
const conpuTesting = computed(() => {
  return testing;
})
function randomizer() {
  currentRandomIndexes.value = [];
  for (let i = 0; i < times.value; i++) {
    currentRandomIndexes.value.push(randomArrayKey(hiragana.length))
  }
}

function randomArrayKey(length) {
  return Math.round(Math.random() * (length - 1));
}

onMounted(() => {
  randomizer();
});

const currentRandomWords = computed(() => {
  return currentRandomIndexes.value.map(item => wordType.value === "hiragana" ? hiragana[item].kana : wordType.value === "katakana" ? katakana[item].kana : hiragana[item].romaji)
})
</script>

<style scoped>
.text-big {
  font-size: 70px;
}
</style>