<template>
  <main class="container">
    <div class="card p-3 mt-5 custom_card">
      <form @submit.prevent="onSubmit" class="text-center">
        <input
          placeholder="Enter Movie name"
          name="name"
          class="form-control mb-2"
          v-model="name"
          type="type"
        />
        <input
          placeholder="Enter Movie URL"
          name="url"
          class="form-control mb-2"
          v-model="url"
          type="url"
        />

        <button type="'submit'" class="btn btn-info btn-block">
          Add Movie
        </button>
      </form>
    </div>
  </main>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "MoviesForm",
  data() {
    return {
      name: "",
      url: "",
    };
  },
  props: {
    addMovie: Function,
  },
  methods: {
    onSubmit: function () {
      this.addMovie({
        name: this.name,
        url: this.url,

        id: uuidv4(),
        date: Date.now(),
      });
      // this.$emit("addMovie", this.name, this.url);
      this.name = "";
      this.url = "";
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
}
</style>
