<template>
  <ul class="list-unstyled">
    <li v-for="movie in movies" :key="movie.id">
      <div class="card text-center custom_card">
        <div class="card-body row">
          <div class="col col-8">
            <h4 class="card-title">{{ movie.name }}</h4>
            <p class="text-subtitle mb-2 text-muted">
              {{ formatedDate(movie.date) }}
            </p>
          </div>
          <div class="col col-4">
            <a
              :href="movie.url"
              target="_blank"
              class="btn btn-primary btn-sm btn-block mb-2"
              >Watch</a
            >
            <button
              class="btn btn-danger btn-sm btn-block"
              @click="deleteMovie(movie.id)"
            >
              Delete
            </button>
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
import moment from "moment";
export default {
  name: "MoviesList",
  props: ["movies", "deleteMovie"],
  methods: {
    formatedDate: function (date) {
      return moment(date).format("MMMM Do YYYY, [at] h:mm:ss a");
    },
  },
};
</script>

<style>
.custom_card {
  background-color: #1a1a1a;
  color: #fff;
  max-width: 600px;
  margin: 0 auto;
  width: 100%;
  height: 100%;
  margin-top: 10px;
}

a {
  width: 100%;
}

button {
  width: 100%;
}
</style>
