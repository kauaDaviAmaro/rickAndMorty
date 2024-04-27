<script setup>
import { onMounted, reactive, ref } from 'vue';
import PersonagemList from '../components/PersonagemList.vue'

const url = 'https://rickandmortyapi.com/api/character/'
const personagens = reactive(ref());
const page = ref(1)

const fetchPage = (pageNumber) =>
  fetch(`${url}?page=${pageNumber}`)
    .then(response => response.json())

const carregarPagina = async (pageNumber) => {
  personagens.value = (await fetchPage(pageNumber)).results
}

const anterior = () => {
  if (page.value <= 1) return
  page.value--
  carregarPagina(page.value)
}

const proxima = () => {
  if (page.value >= 42) return
  page.value++
  carregarPagina(page.value)
}

const search = ref('')

const pesquisarPersonagem = async () => {
  const response = await fetch(`${url}?name=${search.value}`)
  personagens.value = await response.json().then(response => response.results)
}

onMounted(async () => {
  personagens.value = (await fetchPage(1)).results
})
</script>

<template>
  <div class="container">
    <h1 class="mb-4">Lista de personagem:</h1>
    <div class="search">
      <form @submit.prevent="pesquisarPersonagem">
        <input type="text" v-model="search" class="form-control mb-4" placeholder="Pesquisar...">
      </form>
    </div>
    <div class="btn-group mb-4" aria-label="Basic example">
      <button type="button" class="btn btn-secondary" :disabled="page <= 1" @click="anterior()">
        <- Página Anterior </button>
          <button type="button" class="btn">{{ page }}</button>
          <button type="button" class="btn btn-secondary" :disabled="page >= 42" @click="proxima()">
            Proxima Página ->
          </button>
    </div>
    <div v-if="personagens" class="row row-cols-1 row-cols-md-2">
      <PersonagemList v-for="personagem in personagens" :key="personagem.id" :personagem="personagem" />
    </div>
    <div v-else class="text-center">
      <h3>Nenhum personagem encontrado</h3>
    </div>
  </div>
</template>