<template>
  <div id="app">
    <header>
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <a class="navbar-brand" href="#">Movie Search</a>
      </nav>
    </header>
    <main class="container mt-2">
      <form @submit.prevent="getResults">
        <fieldset class="form-group">
          <label for="searchTerm">Search</label>
          <input v-model="searchTerm" type="text" class="form-control" id="searchTerm" placeholder="Enter a movie title.">
        </fieldset>
        <button type="submit" class="btn btn-primary">GO</button>
      </form>
      <section>
        <section class="row movies-area">
          <section class="mt-2 col-9 row" id="results">
            <div v-if="error" class="alert alert-danger col" role="alert">
              {{error}}
            </div>
            <movie
              class="col-4"
              v-for="movie in results"
              :movie="movie">
              </movie>
          </section>
          <section class="mt-2 col-9 row" id="results">
            <div v-if="error" class="alert alert-danger col" role="alert">
              {{error}}
            </div>
          </section>
        </section>
        </section>
        
    </main>
  </div>
</template>

<script>
import Movie from '@/components/Movie';

const API_URL = 'http://www.omdbapi.com/?apikey=faf7e5bb&/?type=movie&s=';

export default {
  name: 'app',
  components: {
    Movie,
  },
  data: () => ({
    error: '',
    searchTerm: '',
    results: []
  }),
  methods: {
    async getResults() {
      const url = `${API_URL}${this.searchTerm}`;
      const response = await fetch(url);
      const data = await response.json();
      if (data.Error) {
        this.results = [];
        this.error = data.Error;
      } else {
        this.results = data.Search;
        this.error = '';
      }
    },
   mounted() {

      }
    }
};
</script>

<style>
.movies-area {
  justify-content: space-around;
  align-items: flex-start;
}
</style>
