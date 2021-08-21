<template>
  <div class="container">
    <button class="button-spirit"
            :data-target="'#collapseTarget' + spirit.name" 
            :href="'#collapseTarget' + spirit.name" 
            data-toggle="collapse">
      <h1>{{ spirit.name }}</h1>
    </button>
    <i class="bi bi-chevron-down"></i>
    <div class="nameline"></div>
    <div class="collapse show" :id="'collapseTarget' + spirit.name">
        <div class="row"> 
          <div class="citrusgroup col-6">
            <h3 class="subcategory citrus">Citrus</h3>
            <div class="drinklist">
              <template v-for="drink in spirit.drinkList.citrus">
                <h3 :class="{'inactive' : !drink.active }" class="drinktitle" >{{drink.name}} </h3>
                <i :class="{'inactive' : !drink.active }" class="bi bi-star-fill" v-if="drink.favorite == true"></i>
                <p :class="{'inactive' : !drink.active }" style="margin-bottom: 1.75rem;">{{drink.ingredients.join(', ')}}</p>
              </template>
            </div>
          </div>
        
          <div class="spiritgroup col-6">
            <h3 class="subcategory spirits" v-if="spirit.drinkList.spirits">Spirits</h3>
            <div class="drinklist">
              <template v-for="drink in spirit.drinkList.spirits">
                <h3 :class="{'inactive' : !drink.active }" class="drinktitle"> {{drink.name}}</h3>
                <i :class="{'inactive' : !drink.active }" class="bi bi-star-fill" v-if="drink.favorite == true"></i>
                <p :class="{'inactive' : !drink.active }" style="margin-bottom: 1.75rem;">{{drink.ingredients.join(', ') }}</p>
              </template>
            </div>
          </div>
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
  },
  methods: {

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
    background-color: rgb(40, 40, 40);
    color: rgb(225, 225, 225);  
}

.container {
    margin: 1rem auto;
    text-align: left;
    /* border: 5px solid blue; */

}

.button-spirit {
  margin-top: 3rem;
  background-color: rgb(55, 55, 55);
  border: none;
  color: rgb(225, 225, 225);
  cursor: pointer;
}

.button-spirit:focus {
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

.drinktitle{ 
  cursor: hover;
}

h1:hover, .drinktitle:hover {
  color: white;
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
  /* float: right; */
  /* display: block; */
}


.bi-chevron-down {
  display: inline-block;
  margin-left: 1rem;
  font-size: 0.8em;
  vertical-align: 12px;
}

.bi-star-fill {
  display: inline;
  color: #FF522E;
  margin-left: 0.75rem;
  /* margin-bottom: 0.25rem; */
  font-size: 0.8em;
  vertical-align: 6px;
}

.subcategory {
  margin-top: 2rem;
  display: block;
  float: left;
  font-size: 0.6em;
  font-weight: 600;
  transform: rotate(-90deg);
  letter-spacing: 0.05em;
}

.drinklist {
  display: block;
  /* width: 45%; */
  margin: 1rem auto auto 2.3rem;
}

.drink {
  margin-bottom: 5rem;
}

.inactive {
  color: rgb(99, 99, 99);
}

.nameline {
  width: 220px;
  height: 0.5px;
  background-color: white;
  margin-left: 2.3rem;
}

.citrus {
  color: rgb(67, 242, 67);
}

.spirits {
  color: rgb(57, 186, 255);
}
</style>
