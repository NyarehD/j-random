<template>
  <div class="col-4">
    <div class="input-group justify-content-center">
      <div class="input-group">
        <div class="input-group-text">
          <input v-model="isInline" aria-label="Checkbox for following text input zuzu" class="form-check-input mt-0"
                 type="checkbox">
        </div>
        <input v-model.number="times" aria-label="Text input with checkbox" class="form-control" type="text"
               @keypress.enter="randomizer">
      </div>
    </div>
  </div>
  <div class="col-6">
    <WordType v-model="wordType" :is-checked="true" type="romaji">Romaji</WordType>
    <WordType v-model="wordType" type="hiragana">Hiragana</WordType>
    <WordType v-model="wordType" type="katakana">Katakana</WordType>
  </div>
  <div class="col-12">
    <div v-if="isInline">
          <span v-for="(item, i) in currentRandom" :key="i" :class="{ 'text-break': isInline }"
                class="text-big">{{ item }}</span>
    </div>
    <div v-else>
      <p v-for="(item, i) in currentRandom" :key="i" class="text-center text-big">{{ item }}</p>
    </div>
  </div>
</template>

<script setup>
import {onMounted, ref} from "vue";
import hiragana from "../words/hiragana.json";
import WordType from "../components/WordType.vue"

const currentRandom = ref([]);
const isInline = ref(true);
const times = ref(5);
const wordType = ref("romaji")

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

<style scoped>

</style>