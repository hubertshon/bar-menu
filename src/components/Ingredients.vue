<template>
  <div class="container">
    <ul>
        <li v-for="ingredient in ingredients" v-on:click="toggleIngredient($event, ingredient)" :class="{'inactive' : ingredient.active === false }">{{ ingredient.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    spirit: Object
  },

  data:()=> ({
    ingredients: [
      {name: "lemon juice", active: true },
      {name: "lime juice", active: true },
      {name: "sweet vermouth", active: true },
      {name: "Campari", active: true },
      {name: "maraschino", active: true },
      {name: "mint", active: true },
      {name: "ginger beer", active: true },
      {name: "s.syrup", active: true }
    ],
  }),

  methods: {
    toggleIngredient(e, ingredient) {
      ingredient.active = !ingredient.active;
      this.$emit('toggle', { ingredient: e.target.innerHTML, active: ingredient.active, ingredientList: this.ingredients });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
    background-color: rgb(48, 48, 48);
    color: rgb(167, 167, 167); 
}

.container {
    margin: 1rem auto;
    text-align: left;
}

.button-ingredient {
  background-color: none; 
  border: none;
  color: rgb(225, 225, 225);  

}

.button-ingredient:focus {
    outline: 0 !important;
}

h1 {
  font-family: 'Antonio', sans-serif;
  /* margin: 40px 0 20px; */
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-left: 2.3rem;

}

h3 {
  display: inline-block;
  margin-bottom: 0.25rem;
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

p {
  margin-top: 0;
  font-family: "Merriweather", serif;
  font-size: 0.8em;
}

ul {
  width: 80%;
  list-style-type: none;
  padding: 0;
  margin: 0 auto;
}

li {
  font-family: "Lato", sans-serif;
  display: inline-block;
  margin: 0 10px;
  font-size: 0.8em;
  text-align: center;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  cursor: pointer;
}

.inactive {
  color: rgb(80, 80, 80) !important;
}

a {
  color: #42b983;
}

.spiritgroup {
  /* float: right; */
  /* display: block; */
}


.bi-star-fill {
  display: inline-block;
  color: #FF522E;
  margin: auto auto 1rem 0.75rem;
  font-size: 0.7em;
  vertical-align: middle;
}


</style>
