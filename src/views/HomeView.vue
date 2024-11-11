<template>
  <div>
    <HeaderComponent
      :selectedNumber="currentQuestionIndex + 1"
      :questions="questions"
      @change-question="changeQuestion"
    />

    <QuestionComponent
      :question="questions[currentQuestionIndex]"
      @submit-answer="nextQuestion"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import HeaderComponent from '../components/HearderComponent.vue';
import QuestionComponent from '../components/QuestionComponent.vue';

const questions = ref([
  {
    text: "I found it hard to wind down",
    subtitle: "In the PAST WEEK, how often have you been bothered by the above statement?",
    options: [
      { label: "a. Never", value: "never" },
      { label: "b. Sometimes", value: "sometimes" },
      { label: "c. Often", value: "often" },
      { label: "d. Almost always", value: "almost_always" }
    ]
  },
  {
    text: "I felt tired after waking up",
    subtitle: "In the PAST WEEK, how often have you felt like this?",
    options: [
      { label: "a. Never", value: "never" },
      { label: "b. Sometimes", value: "sometimes" },
      { label: "c. Often", value: "often" },
      { label: "d. Almost always", value: "almost_always" }
    ]
  },
  {
    text: "I had trouble concentrating",
    subtitle: "In the PAST WEEK, how often have you had trouble concentrating?",
    options: [
      { label: "a. Never", value: "never" },
      { label: "b. Sometimes", value: "sometimes" },
      { label: "c. Often", value: "often" },
      { label: "d. Almost always", value: "almost_always" }
    ]
  },
  {
    text: "I felt down-hearted and blue",
    subtitle: "In the PAST WEEK, how often have you felt down-hearted and blue?",
    options: [
      { label: "a. Never", value: "never" },
      { label: "b. Sometimes", value: "sometimes" },
      { label: "c. Often", value: "often" },
      { label: "d. Almost always", value: "almost_always" }
    ]
  },
  {
    text: "I felt down-hearted and blue",
    subtitle: "In the PAST WEEK, how often have you felt down-hearted and blue?",
    options: [
      { label: "a. Never", value: "never" },
      { label: "b. Sometimes", value: "sometimes" },
      { label: "c. Often", value: "often" },
      { label: "d. Almost always", value: "almost_always" }
    ]
  }
]);

const currentQuestionIndex = ref(0);

const changeQuestion = (number) => {
  currentQuestionIndex.value = number - 1;
};

const nextQuestion = () => {
  if (currentQuestionIndex.value < questions.value.length - 1) {
    currentQuestionIndex.value++;
  }
};
</script>
