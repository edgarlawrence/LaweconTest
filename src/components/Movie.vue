<template lang="html">
   <div class="card">
       <b-button v-b-modal.my-modal>
      <img class="card-img-top" :src="movie.Poster" :alt="movie.Title">
       </b-button>
    <div class="card-body">
      <h5 class="card-title">{{movie.Title}}</h5>
      <p class="card-text">{{movie.Year}}</p>
    </div>

    <b-modal id="my-modal">
          <img class="card-img-top" :src="movie.Poster" :alt="movie.Title">
        </b-modal>
  </div>


</template>

<script>
export default {
  props: ['movie'],
};
</script>
