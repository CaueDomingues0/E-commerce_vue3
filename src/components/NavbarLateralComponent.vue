<template>
  <div class="fixed left-0 top-0 h-screen bg-gray-100 shadow-lg 
               w-24 md:w-72 p-4 transition-all duration-300 ease-in-out">
    <div class="mb-6">
      <h2 class="text-2xl font-bold text-indigo-800 hidden md:block">C&J E-commerce</h2>
      <div class="text-2xl font-bold text-indigo-800 block md:hidden text-center">C&J</div>
    </div>

    <div class="mb-6">
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Pesquise por produtos..."
        class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:border-transparent text-sm"
      />
      <div v-if="isSearching" class="text-xs text-gray-500 mt-2 px-1">Buscando...</div>
      <div v-if="searchResults.length > 0 && searchQuery.length > 0" class="mt-2 bg-white border border-gray-300 rounded-md shadow-sm max-h-60 overflow-y-auto">
        <ul>
          <li v-for="product in searchResults" :key="product.id"
              class="px-4 py-2 hover:bg-gray-50 border-b border-gray-200 last:border-b-0">
            <router-link
              :to="{ name: 'ProdutoDetalhe', params: { id: product.id } }"
              @click="clearSearchAndClose"
              class="text-xs text-gray-700 hover:text-indigo-600 block truncate"
              :title="product.title"
            >
              {{ product.title }}
            </router-link>
          </li>
        </ul>
      </div>
      <div v-else-if="searchQuery.length > 0 && !isSearching && !searchError && searchAttempted" class="text-xs text-gray-500 mt-2 px-1">
        Nenhum produto encontrado.
      </div>
      <div v-if="searchError" class="text-xs text-red-500 mt-2 px-1">
        {{ searchError }}
      </div>
    </div>

    <nav class="space-y-4">
      <router-link to="/" @click="clearSearch" class="sidebar-link flex items-center justify-center md:justify-start md:space-x-3 p-4 rounded-lg hover:bg-gray-200 text-gray-700">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M12 21V3m0 18l-9-9m9 9l9-9" />
        </svg>
        <span class="hidden md:inline">Página Inicial</span>
      </router-link>
      
      <router-link to="/fragancia" @click="clearSearch" class="sidebar-link flex items-center justify-center md:justify-start md:space-x-3 p-4 rounded-lg hover:bg-gray-200 text-gray-700">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 3.104v5.714a2.25 2.25 0 0 1-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 0 1 4.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0 1 12 15a9.065 9.065 0 0 0-6.23-.693L5 14.5m14.8.8 1.402 1.402c1.232 1.232.65 3.318-1.067 3.611A48.309 48.309 0 0 1 12 21c-2.773 0-5.491-.235-8.135-.687-1.718-.293-2.3-2.379-1.067-3.61L5 14.5" />
        </svg>

        <span class="hidden md:inline">Fragâncias</span>
      </router-link>

      <router-link to="/mobilia" @click="clearSearch" class="sidebar-link flex items-center justify-center md:justify-start md:space-x-3 p-4 rounded-lg hover:bg-gray-200 text-gray-700">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M3 10a3 3 0 016 0v1h6v-1a3 3 0 116 0v7H3v-7z" />
        </svg>
        <span class="hidden md:inline">Mobílias</span>
      </router-link>

      <router-link to="/notebook" @click="clearSearch" class="sidebar-link flex items-center justify-center md:justify-start md:space-x-3 p-4 rounded-lg hover:bg-gray-200 text-gray-700">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M9 17.25v1.007a3 3 0 0 1-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0 1 15 18.257V17.25m6-12V15a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 15V5.25m18 0A2.25 2.25 0 0 0 18.75 3H5.25A2.25 2.25 0 0 0 3 5.25m18 0V12a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 12V5.25" />
        </svg>

        <span class="hidden md:inline">Notebooks</span>
      </router-link>

      <router-link to="/moto" @click="clearSearch" class="sidebar-link flex items-center justify-center md:justify-start md:space-x-3 p-4 rounded-lg hover:bg-gray-200 text-gray-700">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M9 16a3 3 0 11-6 0 3 3 0 016 0zm0 0h6m0 0a3 3 0 116 0 3 3 0 01-6 0zM12 16l-3-6h4l2-3h2l1 2" />
        </svg>
        <span class="hidden md:inline">Motos</span>
      </router-link>
    </nav>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';
import axios from 'axios';

const searchQuery = ref('');
const searchResults = ref([]);
const isSearching = ref(false);
const searchError = ref(null);
const searchAttempted = ref(false);
let debounceTimer = null;

const performSearch = async () => {
  if (searchQuery.value.trim().length < 2) {
    searchResults.value = [];
    searchError.value = null;
    searchAttempted.value = false;
    return;
  }
  isSearching.value = true;
  searchError.value = null;
  searchAttempted.value = true;
  try {
    const response = await axios.get(`https://dummyjson.com/products/search?q=${searchQuery.value.trim()}`);
    searchResults.value = response.data.products;
  } catch (error) {
    console.error("Erro ao buscar produtos:", error);
    searchError.value = "Falha ao buscar.";
    searchResults.value = [];
  } finally {
    isSearching.value = false;
  }
};

watch(searchQuery, (newValue) => {
  clearTimeout(debounceTimer);
  searchAttempted.value = false;
  if (newValue.trim() === '') {
    searchResults.value = [];
    searchError.value = null;
    isSearching.value = false;
    return;
  }
  debounceTimer = setTimeout(performSearch, 500);
});

const clearSearch = () => {
  searchQuery.value = '';
  searchResults.value = [];
  searchError.value = null;
  searchAttempted.value = false;
};

const clearSearchAndClose = () => {
  clearSearch();
};
</script>
