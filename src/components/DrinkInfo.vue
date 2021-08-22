<template>
  <div class="container">
    <ul class="nav">
        <li class="nav-item">
            <a class="nav-link text-light">History</a>
        </li>
        <li class="nav-item">
            <a class="nav-link">Recipe</a>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'DrinkInfo',
  props: {
    drinkHistory: String, 
    drinkRecipe: Array
  },
  methods: {}
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
}


.nav-tabs {
    border-bottom: 1px solid rgb(91, 91, 91);
}

.nav-link.active{
    border-bottom: none !important;
}

.nav-link:hover {

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






</style>
