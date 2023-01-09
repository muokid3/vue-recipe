<template>
  <h3>Saved Recipes</h3>
  <br />
  <ul>
    <li v-for="(recipe, index) in recipes" :key="recipe.id">
      <div>Name: {{ recipe.name }}</div>

      <div>
        Ingredients <br />
        {{ recipe.ingredients }}
      </div>

      <div>
        Steps:<br />
        {{ recipe.steps }}
      </div>

      <div>
        <button type="button" @click="deleteRecipe(index)">delete</button>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["recipes"],
  emits: ["deleteRecipe"],
  methods: {
    deleteRecipe(index) {
      this.$emit("deleteRecipe", index);
    },
  },
};
</script>