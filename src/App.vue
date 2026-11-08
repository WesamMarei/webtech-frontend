<script setup>
import { ref, onMounted } from 'vue'
import RecipeList from './components/RecipeList.vue'

const recipeData = ref([])

onMounted(async () => {
  const response = await fetch(`${import.meta.env.VITE_BACKEND_BASE_URL}/api/v1/recipes`)
  recipeData.value = await response.json()
})
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