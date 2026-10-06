<script setup>
defineProps({
  recipes: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <div class="recipe-container">
    <h2>Unsere Rezepte</h2>
    <div v-for="recipe in recipes" :key="recipe.id" class="recipe-card">
      <h3>{{ recipe.title }}</h3>
      <p><strong>Kategorie:</strong> {{ recipe.category }}</p>
      <p><strong>Dauer:</strong> {{ recipe.durationMinutes }} Minuten</p>
    </div>
  </div>
</template>

<style scoped>
.recipe-container {
  max-width: 600px;
  margin: 2rem auto;
  font-family: Arial, sans-serif;
}

.recipe-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
  margin-bottom: 1rem;
  background-color: #fafafa;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

.recipe-card h3 {
  margin-top: 0;
  color: #2c3e50;
}
</style>