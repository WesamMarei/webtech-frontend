<script setup>
import { ref } from 'vue'
import RecipeList from './components/RecipeList.vue'

const recipeData = ref([
  { id: 1, title: 'Spaghetti Bolognese', durationMinutes: 30, category: 'Pasta' },
  { id: 2, title: 'Kürbissuppe', durationMinutes: 45, category: 'Suppen' },
  { id: 3, title: 'Pancakes', durationMinutes: 15, category: 'Frühstück' }
])
</script>

<template>
  <header>
    <h1>Recipe Web App</h1>
  </header>

  <main>
    <RecipeList :recipes="recipeData" />
  </main>
</template>

<style scoped>
header {
  text-align: center;
  margin-top: 2rem;
}
</style>