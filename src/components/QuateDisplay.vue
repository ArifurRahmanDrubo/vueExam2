<template>
    <div class="quote-container bg-gray-100 p-8 rounded-lg shadow-lg">
      <div v-if="loading" class="text-center">Loading...</div>
      <div v-else>
        <p class="text-lg font-bold mb-4">Quote:</p>
        <p class="text-xl">{{ quote }}</p>
        <p class="text-lg font-bold mt-4">Anime: <span class="italic">{{ anime }}</span></p>
        <p class="text-lg font-bold">Character: <span class="italic">{{ character }}</span></p>
      </div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  
  export default {
    setup() {
      const quote = ref('');
      const anime = ref('');
      const character = ref('');
      const loading = ref(true);
  
      const fetchData = async () => {
        try {
          const response = await fetch('https://animechan.xyz/api/random');
          const data = await response.json();
          quote.value = data.quote;
          anime.value = data.anime;
          character.value = data.character;
          loading.value = false;
        } catch (error) {
          console.error('Error fetching data:', error);
        }
      };
  
      onMounted(() => {
        fetchData();
      });
  
      return { quote, anime, character, loading };
    }
  };
  </script>
  
  <style scoped>
  .quote-container {
    max-width: 400px;
    margin: 0 auto;
  }
  
  .italic {
    font-style: italic;
  }
  </style>
  
  