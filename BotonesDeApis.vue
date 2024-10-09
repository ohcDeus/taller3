<template>
  <div>
    <button @click="getPaisesPobla">Obtener Población de Países</button>
    <button @click="getAnimeRecomendaciones">Recomendaciones de Anime</button>
    <button @click="getAnimeRandom">Anime Aleatorio</button>
    <button @click="getMangaRandom">Manga Aleatorio</button>

    <div v-if="data">
      <p>{{ data }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      data: null,
    };
  },
  methods: {
    async getPaisesPobla() {
      try {
        const response = await axios.get('https://countriesnow.space/api/v0.1/countries/population');
        this.data = response.data;
      } catch (error) {
        console.error('Error al obtener la población:', error);
      }
    },
    async getAnimeRecomendaciones() {
      try {
        const response = await axios.get('https://api.jikan.moe/v4/recommendations/anime');
        this.data = response.data;
      } catch (error) {
        console.error('Error al obtener las recomendaciones de anime:', error);
      }
    },
    async getAnimeRandom() {
      try {
        const response = await axios.get('https://api.jikan.moe/v4/random/anime');
        this.data = response.data;
      } catch (error) {
        console.error('Error al obtener el anime aleatorio:', error);
      }
    },
    async getMangaRandom() {
      try {
        const response = await axios.get('https://api.jikan.moe/v4/random/manga');
        this.data = response.data;
      } catch (error) {
        console.error('Error al obtener el manga aleatorio:', error);
      }
    }
  }
};
</script>


