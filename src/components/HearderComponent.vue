<template>
  <div class="flex items-center justify-center mt-10">
    <div class="relative flex items-center w-full max-w-4xl bg-gray-200 h-12 rounded-full shadow-lg">
      <div v-for="(question, index) in questions" :key="index" class="relative flex-1">
        <button
          @click="moveCircle(index + 1)"
          :class="{
            'bg-pink-500 text-white scale-110': selectedNumber === index + 1,
            'bg-pink-300 text-gray-600 hover:bg-pink-400': selectedNumber !== index + 1
          }"
          class="w-full h-full flex items-center justify-center text-lg rounded-full transition-all duration-300 ease-in-out"
        >
          {{ index + 1 }}
        </button>
      </div>
      <div
        :style="{ left: `${(selectedNumber - 1) * (100 / questions.length)}%` }"
        class="absolute top-0 bottom-0 left-0 transform -translate-x-1/2 bg-pink-500 w-8 h-8 rounded-full shadow-xl transition-all duration-300 ease-in-out"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue';

const props = defineProps({
  selectedNumber: Number,
  questions: Array,
});
const emit = defineEmits(['change-question']);

const moveCircle = (number) => {
  emit('change-question', number);
};
</script>
