<template>
  <form @submit.prevent="addRecipe">
    <div>
      <label>Name</label><br />
      <input type="text" v-model.trim="name" />
    </div>

    <div>
      <label>Ingredients</label><br />
      <textarea rows="5" v-model.trim="ingredients"></textarea>
    </div>

    <div>
      <label>Steps</label><br />
      <textarea rows="5" v-model.trim="steps"></textarea>
    </div>

    <button>Save</button>
  </form>
  <recipe-list :recipes="recipes" @deleteRecipe="deleteRecipe"></recipe-list>
</template>

<script>
import RecipeList from "./components/RecipeList.vue";

export default {
  name: "App",
  components: {
    RecipeList,
  },
  data() {
    return {
      name: null,
      ingredients: null,
      steps: null,
      recipes: [],
    };
  },
  methods: {
    addRecipe() {
      if (this.validate()) {
        const recipe = {
          id: new Date().toString,
          name: this.name,
          ingredients: this.ingredients,
          steps: this.steps,
        };

        this.recipes.push(recipe);

        this.name = null;
        this.ingredients = null;
        this.steps = null;
      } else {
        return;
      }
    },
    validate() {
      if (this.name === null) {
        return false;
      }

      if (this.ingredients === null) {
        return false;
      }

      if (this.steps === null) {
        return false;
      }

      return true;
    },
    deleteRecipe(index) {
      this.recipes.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: start;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
