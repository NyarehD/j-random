<template>
  <div class="form-check form-check-inline">
    <input :id="type" :checked="isChecked" :value="type" class="form-check-input" name="wordType"
           type="radio" @input="$emit('update:modelValue',$event.target.value)">
    <label :for="type" class="form-check-label">
      <slot></slot>
    </label>
  </div>
</template>

<script setup>
import {defineProps} from "vue";

const props = defineProps({
  "modelValue": {
    required: true,
    type: String
  },
  "type": {
    required: true,
    type: String
  },
  "isChecked": {
    required: false,
    type: Boolean,
    default: false
  }
})
</script>

<style>
label {

}
</style>