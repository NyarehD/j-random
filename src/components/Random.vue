<template>
  <div class="col-4">
    <div class="input-group mb-3 justify-content-center">
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

const currentRandom = ref([]);
const isInline = ref(true);
const times = ref(5);
const hiragana = ["a", "i", "u", "e", "o", "ka", "ki", "ku", "ke", "ko", "sa", "shi", "su", "se", "so", "ta", "chi", "tsu", "te", "to", "na", "ni", "nu", "ne", "no", "ha", "hi", "fu", "he", "ho", "ma", "mi", "mu", "me", "mo", "ya", "yu", "yo", "ra", "ri", "ra", "re", "ro", "wa", "wo", "n", "ga", "gi", "gu", "ge", "go", "za", "ji", "zu", "ze", "zo", "da", "ji", "zu", "de", "do", "ba", "bi", "bu", "be", "bo", "pa", "pi", "pu", "pe", "po", "kya", "kyu", "kyo", "sha", "shu", "sho", "cha", "chu", "cho", "nya", "nyu", "nyo", "hya", "hyu", "hyo", "mya", "myu", "myo", "rya", "ryu", "ryo", "gya", "gyu", "gyo", "ja", "ju", "jo", "bya", "byu", "byo", "pya", "pyu", "pyo"
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

<style scoped>

</style>