<script setup>
import { ref, onMounted } from 'vue'
import RecipeList from './components/RecipeList.vue'

const recipeData = ref([])
const newRecipe = ref({ title: '', durationMinutes: '', category: '' })

const baseUrl = import.meta.env.VITE_BACKEND_BASE_URL

async function loadRecipes() {
  const response = await fetch(`${baseUrl}/api/v1/recipes`)
  recipeData.value = await response.json()
}

async function saveRecipe() {
  await fetch(`${baseUrl}/api/v1/recipes`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(newRecipe.value)
  })
  newRecipe.value = { title: '', durationMinutes: '', category: '' }
  await loadRecipes()
}

onMounted(loadRecipes)
</script>

<template>
  <header>
    <h1>Recipe Web App</h1>
  </header>

  <main>
    <form class="recipe-form" @submit.prevent="saveRecipe">
      <h2>Neues Rezept</h2>
      <input v-model="newRecipe.title" placeholder="Titel" required />
      <input v-model.number="newRecipe.durationMinutes" type="number" placeholder="Dauer in Minuten" required />
      <input v-model="newRecipe.category" placeholder="Kategorie" required />
      <button type="submit">Speichern</button>
    </form>

    <RecipeList :recipes="recipeData" />
  </main>
</template>

<style scoped>
header {
  text-align: center;
  margin-top: 2rem;
}

.recipe-form {
  max-width: 600px;
  margin: 2rem auto;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-family: Arial, sans-serif;
}

.recipe-form input,
.recipe-form button {
  padding: 0.6rem;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 1rem;
}

.recipe-form button {
  background-color: #2c3e50;
  color: white;
  cursor: pointer;
}
</style>