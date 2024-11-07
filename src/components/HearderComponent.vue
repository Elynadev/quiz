<template>
  <div class="flex items-center justify-center mt-10">
     <!-- Barre avec les chiffres de 1 à 20 -->
     <div class="relative flex items-center w-full max-w-4xl bg-gray-200 h-12 rounded-full">
      <div v-for="i in 20" :key="i" class="relative flex-1">
        <button
          @click="moveCircle(i)"
          :class="{
            'bg-pink-500 text-white': selectedNumber === i, 
            'bg-pink-300 text-gray-600': selectedNumber !== i
          }"
          class="w-full h-full flex items-center justify-center text-lg hover:bg-pink-200 rounded-full"
        >
          {{ i }}
        </button>
      </div>
      <!-- Cercle qui se déplace -->
      <div
        :style="{ left: `${(selectedNumber - 1) * (100 / 20)}%` }"
        class="absolute top-0 bottom-0 left-0 transform -translate-x-1/2 bg-pink-500 w-6 h-6 rounded-full transition-all"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Déclaration de la variable pour gérer le numéro sélectionné
const selectedNumber = ref(1);

// Fonction pour déplacer le cercle en fonction du chiffre sélectionné
const moveCircle = (number) => {
  selectedNumber.value = number;
};
</script>

<style scoped>
/* Vous pouvez ajouter des styles supplémentaires si nécessaire */
</style>
