<template>
  <main class="bg-dark text-light">
    <NavBar />
    <div class="container mt-3">
      <div class="row">
        <div class="offset-md-3 col-lg-6 p-2">
          <div>
            <MoviesForm :addMovie="addMovie"></MoviesForm>
          </div>
          <MoviesList :movies="movies" :deleteMovie="deleteOne"></MoviesList>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import NavBar from "./components/Layout/NavBar.vue";
import MoviesForm from "./components/MoviesForm.vue";
import MoviesList from "./components/MoviesList.vue";

export default {
  name: "App",
  components: { NavBar, MoviesForm, MoviesList },
  data() {
    return {
      movies: [],
    };
  },
  methods: {
    addMovie: function (movie) {
      console.log(movie);
      this.movies.push(movie);
      localStorage.setItem("@movies", JSON.stringify(this.movies));
    },
    deleteOne: function (id) {
      console.log(id);
      this.movies = this.movies.filter((movie) => movie.id !== id);
      localStorage.setItem("@movies", JSON.stringify(this.movies));
    },
  },

  mounted() {
    if (localStorage.getItem("@movies")) {
      try {
        this.movies = JSON.parse(localStorage.getItem("@movies"));
      } catch (e) {
        localStorage.removeItem("@movies");
      }
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

main {
  width: 100%;
  /* min-height: 100vh; */
  height: 100%;
}
</style>
