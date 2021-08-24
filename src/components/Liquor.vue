<template>
  <div class="container">
    <button class="button-spirit"
            :data-target="'#collapseTarget' + spirit.name" 
            :href="'#collapseTarget' + spirit.name" 
            data-toggle="collapse"
            v-on:click="expandSpirit(spirit.name)">
      <h1>{{ spirit.name }}</h1>
      <i class="bi bi-chevron-down" :class="{'openup' : checkSpirit(spirit.name), 'closeup' : !checkSpirit(spirit.name)}"></i>
    </button>
    
    <div class="nameline"></div>
    <div class="collapse show" :id="'collapseTarget' + spirit.name">
        <div class="row">

          <div class="citrusgroup col-md-6 col-sm-12" v-for="(property, flavor) in spirit.drinkList">
            <h3 class="subcategory" :class="{'citrus' : flavor === 'citrus', 'spirits' : flavor === 'spirits'}">{{ flavor }}</h3>
            <div class="drinklist">
              <template v-for="drink in property">
                <h5 :id="'popover-button-' + drink.name" :class="{'inactive' : !drink.active }" class="drinktitle" tabindex="-1">{{drink.name}}</h5>
                <i :class="{'inactive' : !drink.active }" class="bi bi-star-fill" v-if="drink.favorite === true"></i>
                <p :class="{'inactive' : !drink.active }" style="margin-bottom: 1.75rem;">{{drink.ingredients.join(', ')}}</p>
                <div :id="'menupopover' + spirit.name"></div>
                <b-popover :container="'menupopover' + drink.name" :target="'popover-button-' + drink.name" triggers="focus" :key="drink.name" placement="right">
                  <button class="tooltip-button" v-on:click="launchDrinkModal('history', drink.name)">
                  <i class="bi bi-book"></i><span>History</span>
                  </button>
                  <button class="tooltip-button" v-on:click="launchDrinkModal('recipe', drink.name)">
                  <i class="bi bi-list-check"></i><span>Recipe</span>
                  </button>
                </b-popover>
              </template>
            </div>
          </div>
        </div>
    </div>

    <div v-if="showModal">
      <transition name="modal">
        <div class="modal-mask">
          <div class="modal-wrapper">
            <div class="modal-dialog .modal-dialog-centered" role="document">
              <div class="modal-content">
                <div class="modal-header">
                  <DrinkInfo :drink="selectDrink" :tab="openTab" />
                  <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="showModal = false">
                    <span aria-hidden="true">&times;</span>
                  </button>
                </div>
                <!-- <div class="modal-body">
                </div> -->
                <!-- <div class="modal-footer">
                  <button type="button" class="btn btn-secondary" @click="showModal = false">Close</button>
                </div> -->
              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
    
  </div>

 

</template>
<script>
import DrinkInfo from '@/components/DrinkInfo.vue'

export default {
  name: 'Liquor',
  components: {DrinkInfo},
  props: {
    msg: String,
    spirit: Object
  },
  data:() => ({
    tooltip: 'History',
    spiritOpen: {
      bourbon: true,
      gin: true,
      rum: true
    },
    showModal: false,
    openTab: null,
    sentDrink: null
  }),
  methods: {
    expandSpirit(name) {
      let key = name.toLowerCase();
      this.spiritOpen[key] = !this.spiritOpen[key];
    },
    launchDrinkModal(tab, sentDrink) {
      this.showModal = true;
      this.openTab = tab;
      this.selectDrink = sentDrink;
    },
    checkSpirit(name) {
      let key = name.toLowerCase();
      if (this.spiritOpen[key]) {
        return true;
      } else {
        return false;
      }
    }
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
}

.button-spirit {
  display: inline-block;
  margin-top: 3rem;
  margin-left: 2rem;
  background-color: rgb(55, 55, 55);
  border: none;
  color: rgb(225, 225, 225);
  cursor: pointer;
  width: 250px;
  text-align: left;
}

.button-spirit:focus {
    outline: 0 !important;
}

h1 {
  font-family: 'Antonio', sans-serif;
  /* margin: 40px 0 20px; */
  text-transform: uppercase;
  letter-spacing: 0.08em;
  text-align: left;
  /* margin-left: 2.3rem; */
  display: inline;

}

h3, h4 {
  display: inline-block;
  margin-bottom: 0.25rem;
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

h5 {
  display: inline-block;
  margin-bottom: 0.25rem;
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.drinktitle{ 
  cursor: pointer;
}

h1:hover, .button-spirit:hover {
  color: white;
}

p {
  margin-top: 0;
  font-family: "Merriweather", serif;
  font-size: 0.8em;
  font-weight: 300;
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

.bi-book {
  margin-right: 0.4rem;
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

.popover {
  display: block;
  margin-left: 1rem;
  box-shadow: rgba(4, 4, 4, 0.79) 0px 7px 15px -6px;
  background-color: rgb(31, 31, 31);
  width: 250px;
  height: 55px;
  z-index: 9;

} 

.popover-body > span,
.popover-body > i {
  color: rgb(193, 193, 193);
}

.closeup {
  animation-name: swivel;
  animation-duration: 0.5s;
  animation-fill-mode: forwards;
  animation-timing-function: cubic-bezier(0.23, 1, 0.320, 1);
}

@-moz-keyframes swivel { 
  0% { -moz-transform: rotate(0); }
  100% { -moz-transform: rotate(-90deg); } 
  }
@-webkit-keyframes swivel { 
  0% { -webkit-transform: rotate(0); } 
  100% { -webkit-transform: rotate(-90deg); } 
  }
@keyframes swivel { 
  0% { -webkit-transform: rotate(0); transform:rotate(0); } 
  100% { -webkit-transform: rotate(-90deg); transform:rotate(-90deg); } 
  }


.openup {
  animation-name: unswivel;
  animation-duration: 0.5s;
  /* animation-direction: reverse; */
}

@-moz-keyframes unswivel { 
  100% { -moz-transform: rotate(0); }
  0% { -moz-transform: rotate(-90deg); } 
  }
@-webkit-keyframes unswivel { 
  100% { -webkit-transform: rotate(0); } 
  0% { -webkit-transform: rotate(-90deg); } 
  }
@keyframes unswivel { 
  100% { -webkit-transform: rotate(0); transform:rotate(0); } 
  0% { -webkit-transform: rotate(-90deg); transform:rotate(-90deg); } 
  }


.tooltip-button {
  /* display: inline-block; */
  height: 37px;
  width: 95px;
  background-color: rgb(53, 53, 53);
  color: rgb(193, 193, 193);
  border-style: none;
  border-radius: 6px;
  margin: 0 0.5rem;
}

.tooltip-button:hover {
  background-color: rgb(75, 75, 75);
}

.tooltip-button > i {
  font-size: 0.8em;
  margin-right: 0.5rem;
}

.tooltip-button > span {
  vertical-align: middle;
  text-transform: uppercase;
  font-size: 0.65em;
  font-weight: 300;
  letter-spacing: 0.1em;
}

.modal-mask {
  position: fixed;
  z-index:10;
  top:0;
  right:0;
  bottom:0;
  left:0;
  background:rgba(0, 0, 0, 0.53);
  width:100%;
  height: 10000px;
}

.modal-header {
  border-bottom: 0;
}


.modal-content { 
  background-color: rgb(53, 53, 53);
  font-family: "Lato", sans-serif;
}



.modal-dialog {
    display: flex;
    flex-direction: column;
    justify-content: center;
    overflow: auto;
    position: fixed;
    margin: 0 auto;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
}


@media(max-width: 768px) {
  .modal-dialog {
    min-height: calc(100vh - 20px);
  }
}

.close {
  color: gray;
  border-style: none;
  text-shadow: none;
}

.close:hover{
  color: rgb(179, 179, 179);
}


</style>
