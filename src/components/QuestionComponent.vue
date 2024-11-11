<template>
  <div class="bg-blue-200 flex items-center justify-center min-h-screen">
    <div class="bg-white rounded-lg shadow-lg p-6 w-full max-w-2xl">
      <h2 class="text-gray-800 text-lg mb-4">{{ question.text }}</h2>
      <div class="bg-blue-100 text-blue-600 p-3 rounded mb-6">
        {{ question.subtitle }}
      </div>

      <div class="space-y-4">
        <label v-for="(option, index) in question.options" :key="index" class="flex items-center space-x-3">
          <input
            type="radio"
            :value="option.value"
            v-model="selectedOption"
            name="response"
            class="form-radio h-8 w-8 text-pink-600 bg-pink-300 border-pink-600 focus:ring-pink-500 peer"
          />
          <span class="text-gray-700">{{ option.label }}</span>
        </label>
      </div>

      <button
        @click="submitAnswer"
        :disabled="!selectedOption"
        class="mt-6 bg-blue-500 text-white px-4 py-2 rounded disabled:opacity-50"
      >
        Soumettre
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  question: Object,
});
const emit = defineEmits(['submit-answer']);

const selectedOption = ref(null);

const submitAnswer = () => {
  emit('submit-answer');
  selectedOption.value = null;
};
</script>
