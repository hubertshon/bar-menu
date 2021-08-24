<template>
  <div class="container">
    <h5>{{ drink }} </h5>
    <ul class="nav">
        <li class="nav-item" v-on:click="clickTab('history')">
            <a class="nav-link" :class="{ 'text-light' : this.selectTab ==='history'}">History</a>
        </li>
        <li class="nav-item" v-on:click="clickTab('recipe')">
            <a class="nav-link" :class="{ 'text-light' : this.selectTab ==='recipe'}">Recipe</a>
        </li>
    </ul>

    <div class="history" v-if="this.selectTab==='history'">
      <p>{{ drinkHistory }}</p>
    </div>

    <div class="recipe" v-if="this.selectTab==='recipe'">
      <ul>
        <li v-for="step in drinkRecipe" v-html="step">{{ step }}</li>
      </ul>
    </div>


  </div>
</template>

<script>
import encyclopedia from '../static/drink_information.js'

export default {
  name: 'DrinkInfo',
  props: {
    drink: String,
    tab: String 
  },
  data: () => ({
    drinkHistory: null,
    drinkRecipe: null,
    drinkTab: null,
    selectTab: null
  }),
  created() {
  },
  mounted() {
    // this.startTab();
    this.findDrink(this.drink);
    this.selectTab = this.tab;
  },
  methods: {
    findDrink(drink) {
      let drinkArray = encyclopedia.encyclopedia;
      let foundEntry = drinkArray.find((item) => {
        return item.name === drink;
      });
      this.drinkHistory = foundEntry.history;
      this.drinkRecipe = foundEntry.recipe;
    },
    clickTab(clickedTab) {
      if (clickedTab === 'history') {
        this.selectTab = 'history';
      } else if (clickedTab === 'recipe') {
        this.selectTab = 'recipe';
      }
    }
  },
  
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
    text-align: center;
}

.nav {
    border-bottom: none;
    margin-bottom: 1rem;
}


.nav-tabs {
    border-bottom: 1px solid rgb(91, 91, 91);
}


.nav-link {
  padding-left: 0 !important;
}

.nav-link.active{
    border-bottom: none !important;
}

.nav-item  {
  border-color: gray;
  text-transform: uppercase;
  font-size: 0.8em;
  cursor: pointer;
}

.nav-link:hover {
  border: unset;
}


a {
    color: rgb(167, 167, 167);
}

a:hover {
    color: rgb(201, 201, 201);
}

.history > p {
  line-height: 1.5em;

}

.recipe ul li {
  line-height: 1.75em;
  font-size: 1.1em;
}




</style>
