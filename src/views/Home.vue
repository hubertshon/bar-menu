<template>
  <div class="home">
    <img alt="logo" class="casalogo" src="../assets/casalogo.svg">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Ingredients @toggle="toggleIngredient($event)" />
  <div v-for="spirit in spiritList">
    <Liquor :spirit="spirit" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Liquor from '@/components/Liquor.vue'
import Ingredients from '@/components/Ingredients.vue'

export default {
  name: 'Home',
  components: {
    // HelloWorld,
    Liquor,
    Ingredients
  },

  data: ()=> ({
    spiritList: [
      {
        name: "Bourbon",
        drinkList: {
          citrus: [
            {name: 'Kentucky Mule', ingredients: ['Bourbon', 'lime juice', 's.syrup', 'ginger beer'], category: "citrus", favorite: true, active: true },
            {name: 'Bourbon Smash', ingredients: ['Bourbon', 'lemon wedges', 's.syrup', 'mint leaves'], category: "citrus", favorite: false, active: true },
            {name: 'Gold Rush', ingredients: ['Bourbon', 'honey syrup', 'lemon juice'], category: "citrus", favorite: false, active: true },
            {name: 'Whiskey Sour', ingredients: ['Bourbon', 'lemon juice', '(egg white)', 's.syrup'], category: "citrus", favorite: false, active: true },
            {name: 'Strawberry Fix', ingredients: ['Bourbon', 'strawberry', 'lemon juice', 's.syrup'], category: "citrus", favorite: false, active: true },
            {name: 'Suffering Bastard', ingredients: ['Bourbon', 'Gin', 'lime juice', 'bitters', 'ginger beer', 's.syrup'], category: "citrus", favorite: false, active: true },
          ],
          spirits: [
            {name: 'Old Fashioned', ingredients: ['Bourbon', 'bitters', 's.syrup'], category: "spirits", favorite: false, active: true },
            {name: 'Manhattan', ingredients: ['Bourbon', 'sweet vermouth', 'bitters'], category: "spirits", favorite: true, active: true },
            {name: 'Fancy Free', ingredients: ['Bourbon', 'maraschino', 'bitters'], category: "spirits", favorite: false, active: true },
            {name: 'Boulevardier', ingredients: ['Bourbon', 'Campari', 'sweet vermouth'], category: "spirits", favorite: false, active: true },
            {name: 'Mint Julep', ingredients: ['Bourbon', 'mint', 's.syrup'], category: "spirits", favorite: false, active: true },
            {name: 'Martinez', ingredients: ['Bourbon', 'sweet vermouth', 'maraschino', 'bitters'], category: "spirits", favorite: false, active: true },
          ]
        }
      },
      {
        name: "Gin",
        drinkList: {
          citrus: [
            {name: 'Tom Collins', ingredients: ['Gin', 'lemon juice', 's.syrup', 'soda'], category: "citrus", favorite: false, active: true },
            {name: 'Gin-gin Mule', ingredients: ['Gin', 'lime juice', 'mint leaves', 'ginger beer'], category: "citrus", favorite: false, active: true },
            {name: 'Gimlet', ingredients: ['Gin', 'lime juice', 's.syrup'], category: "citrus", favorite: false, active: true },
            {name: 'Foghorn', ingredients: ['Gin', 'lime juice', 's.syrup', 'ginger beer'], category: "citrus", favorite: false, active: true },
            {name: 'Southside (NY)', ingredients: ['Gin', 'lemon juice', 's.syrup', 'mint'], category: "citrus", favorite: true, active: true },
            {name: "Bee's Knees", ingredients: ['Gin', 'lemon juice', 'honey syrup'], category: "citrus", favorite: false, active: true },
          ],
          spirits: [
            {name: 'Negroni', ingredients: ['Gin', 'Campari', 'sweet vermouth', 'bitters'], category: "spirit", favorite: true, active: true },
            {name: 'Artillery', ingredients: ['Gin', 'sweet vermouth', 'bitters'], category: "spirit", favorite: false, active: true },
            {name: 'Casino', ingredients: ['Gin', 'lemon juice', 'maraschino', 'orange bitters'], category: "spirit", favorite: false, active: true },
            {name: 'Enzoni', ingredients: ['Gin', 'lemon juice', 'Campari', 's.syrup', 'grapes'], category: "spirit", favorite: false, active: true }
          ]
        }
      },
      {
        name: "Rum",
        drinkList: {
          citrus: [
            {name: 'Mojito', ingredients: ['Rum', 'lime juice', 'mint', 's.syrup'], category: "citrus", favorite: true, active: true },
            {name: 'Daiquiri', ingredients: ['Rum', 'lime juice', 's.syrup'], category: "citrus", favorite: false, active: true },
            {name: "Cuba Libre", ingredients: ['Rum', 'coke', 'lime juice'], category: "citrus", favorite: false, active: true },
            {name: "Strawberry Sour", ingredients: ['Rum', 'strawberries', 'lime juice', 's.syrup'], category: "citrus", favorite: false, active: true }
          ],
          spirits: [
            {name: "King's Jubilee", ingredients: ['Rum', 'maraschino', 'lemon juice'], category: "citrus", favorite: false, active: true },
            {name: "Salty Bird", ingredients: ['Rum', 'Campari', 'pineapple juice', 'lime juice', 's.syrup'], category: "citrus", favorite: false, active: true }
          ]
        }
      }
    ],
  }),
  
  methods: {
    toggleIngredient(event) {
      let toggledDrinks = [];
      let cutIngredients = [];
      event.ingredientList.forEach((ingredient) => {
        if (ingredient.active === false) {
          cutIngredients.push(ingredient.name);
        }
      });
      console.log('cut ingredients', cutIngredients);
      this.spiritList.forEach((spirit) => {
        spirit.drinkList.citrus.forEach((drink) => {
          for (let ingredient of drink.ingredients) {
            if (cutIngredients.includes(ingredient)) {
              drink.active = false;
              break;
            } else {
              drink.active = true;
            }
          }
        });

        spirit.drinkList.spirits.forEach((drink) => {
          for (let ingredient of drink.ingredients) { 
            if (cutIngredients.includes(ingredient)) {
              drink.active = false;
              break;
            } else {
              drink.active = true;
            }
          }
        });
      });
    }
  }
}
</script>
<style scoped>
.home{
  margin-top: 1rem;
}

.casalogo {
  width: 105px;
}
</style>
