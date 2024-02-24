
<script setup>
import { ref, onMounted } from 'vue';

const id = ref('');
const quote = ref('');
const anime = ref('');
const character = ref('');
const loading = ref(true);

const fetchQuote = async () => {
    try {
        const response = await fetch('https://animechan.xyz/api/random');
        const data = await response.json();
        if (!response.ok) throw new Error('Failed to fetch data');
        id.value = data.id;
        quote.value = data.quote;
        anime.value = data.anime;
        character.value = data.character;
        loading.value = false;
    } catch (error) {
        console.error('Error fetching quote:', error);
    }
};

onMounted(fetchQuote);
</script>

<template>
    <div class="max-w-lg mx-auto p-6 bg-green-100 shadow-lg rounded-lg mt-10">
        <h2 class="text-3xl font-bold text-center text-gray-800 mb-6">Random Anime Quote</h2>
        <div v-if="loading" class="flex items-center justify-center">
            <svg class="animate-spin h-8 w-8 mr-3 text-gray-600" xmlns="http://www.w3.org/2000/svg" fill="none"
                viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor"
                    d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 4.418 3.582 8 8 8v-4zm2-2.582a3.001 3.001 0 005.765-.936l-1.5-.866a1.5 1.5 0 11.964-2.817l3 1.732a1.5 1.5 0 11-1.464 2.598l-1.5-.866a3.001 3.001 0 00-3.765-1.732z">
                </path>
            </svg>
            <p class="text-gray-600">Loading...</p>
        </div>
        <div v-else>
            <p class="text-lg font-semibold text-gray-800 mb-2"><strong>Quote:</strong> {{ quote }}</p>
            <p class="text-lg font-semibold text-gray-800 mb-2"><strong>Anime:</strong> {{ anime }}</p>
            <p class="text-lg font-semibold text-gray-800"><strong>Character:</strong> {{ character }}</p>
        </div>
    </div>
</template>



