<template>
    <div class="bg-blue-200 flex items-center justify-center min-h-screen">
      <div class="bg-white rounded-lg shadow-lg p-6 w-full max-w-2xl">
        <!-- Progress Bar -->
        <div class="flex items-center justify-between mb-4">
          <div class="w-full bg-gray-200 rounded-full h-2.5">
            <div class="bg-pink-500 h-2.5 rounded-full" :style="{ width: progress + '%' }"></div>
          </div>
          <span class="ml-2 text-gray-500 text-sm">{{ progress }}%</span>
        </div>
  
        <!-- Question Section -->
        <h2 class="text-gray-800 text-lg mb-4">I found it hard to wind down</h2>
        <div class="bg-blue-100 text-blue-600 p-3 rounded mb-6">
          In the PAST WEEK, how often have you been bothered by the above statement?
        </div>
  
        <!-- Radio Button Options -->
        <div class="space-y-4">
          <label v-for="(option, index) in options" :key="index" class="flex items-center space-x-3">
            <input
              type="radio"
              :value="option.value"
              v-model="selectedOption"
              name="response"
              class="form-radio h-8 w-10 text-pink-600 bg-pink-300 peer"
            />
            <span class="text-gray-700">{{ option.label }}</span>
          </label>
        </div>
  
        <!-- Navigation Links -->
        <div class="mt-6 text-right">
          <a href="#" class="text-blue-400">BACK</a>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Définition des variables réactives avec `ref`
  const progress = ref(30);
  const selectedOption = ref(null);
  const options = [
    { label: "a. Never", value: "never" },
    { label: "b. Sometimes", value: "sometimes" },
    { label: "c. Often", value: "often" },
    { label: "d. Almost always", value: "almost_always" }
  ];
  </script>
  
  <style scoped>
  /* Ajout de style personnalisé pour changer la couleur du bouton radio */
  input[type="radio"]:checked {
    border-color: #EC4899; /* Couleur rose */
    background-color: #EC4899; /* Fond rose pour le bouton radio sélectionné */
  }
  
  input[type="radio"]:focus {
    outline: none; /* Pour éviter l'effet de contour de focus par défaut */
  }
  </style>
  