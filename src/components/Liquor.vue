<template>
  <div class="bourbon-container">
      <h1>{{ spirit.name }}</h1>
      <div class="nameline"></div>
      <div class="citrusgroup">
        <h3 class="subcategory citrus">Citrus</h3>
        <div class="drinklist">
          <template v-for="drink in spirit.drinkList.citrus">
            <h3> {{drink.name}}</h3>
            <p>{{drink.ingredients}}</p>
          </template>
        </div>
      </div>
      <div class="spiritgroup">
        <h3 class="subcategory">Spirits</h3>
        <div class="drinklist">
          <template v-for="drink in spirit.drinkList.spirits">
            <h3> {{drink.name}}</h3>
            <p>{{drink.ingredients}}</p>
          </template>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    spirit: Object
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
    background-color: rgb(48, 48, 48);
    color: rgb(225, 225, 225);  
}

.bourbon-container {
    margin: 1rem;
    text-align: left;
}

h1 {
  font-family: 'Antonio', sans-serif;
  margin: 40px 0 20px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-left: 2.3rem;

}

h3 {
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
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.spiritgroup {
  float: right;
  display: block;
}

.subcategory {
  margin-top: 2rem;
  display: block;
  float: left;
  font-size: 0.6em;
  transform: rotate(-90deg);
}

.drinklist {
  display: block;
  /* width: 45%; */
  margin-left: 2.3rem;
}

.nameline {
  width: 220px;
  height: 0.5px;
  background-color: white;
  margin-left: 2.3rem;
}

.citrus {
  color: rgb(67, 242, 67);
  letter-spacing: 0.05em;
}
</style>
