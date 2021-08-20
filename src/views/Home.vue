<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/casaHLogo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <div v-for="spirit in spiritlist">
    <Liquor :spirit="spirit" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Liquor from '@/components/Liquor.vue'

export default {
  name: 'Home',
  components: {
    // HelloWorld,
    Liquor
  },

  data: ()=> ({
    spiritlist: [
      {
        name: "Bourbon",
        drinkList: {
          citrus: [
            {name: 'Kentucky Mule', ingredients: 'Bourbon, lime juice, s.syrup, ginger beer', category: "citrus", favorite: true },
            {name: 'Bourbon Smash', ingredients: 'Bourbon, lemon wedges, s.syrup, mint leaves', category: "citrus", favorite: false },
            {name: 'Gold Rush', ingredients: 'Bourbon, honey syrup, lemon juice', category: "citrus", favorite: false },
            {name: 'Bourbon Sour', ingredients: 'Bourbon, lemon juice, (egg white), s.syrup', category: "citrus", favorite: false },
            {name: 'Strawberry Fix', ingredients: 'Bourbon, strawberry, lemon juice, s.syrup', category: "citrus", favorite: false },
            {name: 'Suffering Bastard', ingredients: 'Bourbon, Gin, lime juice, bitters, ginger beer, s.syrup', category: "citrus", favorite: false },
          ],
          spirits: [
            {name: 'Old Fashioned', ingredients: 'Bourbon, bitters, s.syrup', category: "spirits", favorite: false },
            {name: 'Manhattan', ingredients: 'Bourbon, sweet vermouth, bitters', category: "spirits", favorite: false },
            {name: 'Fancy Free', ingredients: 'Bourbon, maraschino, bitters', category: "spirits", favorite: false },
            {name: 'Boulevardier', ingredients: 'Bourbon, Campari, sweet vermouth', category: "spirits", favorite: false },
            {name: 'Mint Julep', ingredients: 'Bourbon, mint, s.syrup', category: "spirits", favorite: false },
            {name: 'Martinez', ingredients: 'Bourbon, sweet vermouth, maraschino, bitters', category: "spirits", favorite: false },
          ]
        }
      },
      {
        name: "Gin",
        drinkList: {
          citrus: [
            {name: 'Tom Collins', ingredients: 'Gin, lemon juice, s.syrup, soda', category: "citrus", favorite: false },
            {name: 'Gin-gin Mule', ingredients: 'Gin, lime juice, mint leaves, ginger beer', category: "citrus", favorite: false },
            {name: 'Gimlet', ingredients: 'Gin, lime juice, s.syrup', category: "citrus", favorite: false },
            {name: 'Foghorn', ingredients: 'Gin, lime juice, s.syrup, gingerbeer', category: "citrus", favorite: false },
            {name: 'Southside (NY)', ingredients: 'Gin, lemon juice, s.syrup, mint', category: "citrus", favorite: false },
          ],
          spirits: [
            {name: 'Negroni', ingredients: 'Gin, Campari, sweet vermouth, bitters', category: "spirit", favorite: true },
            {name: 'Artillery', ingredients: 'Gin, sweet vermouth, bitters', category: "spirit", favorite: false },
            {name: 'Casino', ingredients: 'Gin, lemon juice, maraschino, orange bitters', category: "spirit", favorite: false },
            {name: 'Enzoni', ingredients: 'Gin, lemon juice, campari, s.syrup, grapes', category: "spirit", favorite: false }
          ]
        }
      },
      {
        name: "Rum",
        drinkList: {
          citrus: [
            {name: 'Mojito', ingredients: 'Rum, lime juice, mint, s.syrup', category: "citrus", favorite: true },
            {name: 'Daiquiri', ingredients: 'Rum, lime juice, s.syrup', category: "citrus", favorite: false },
            {name: "Cuba Libre", ingredients: 'Rum, coke, lime juice', category: "citrus", favorite: true },
            {name: "Strawberry Sour", ingredients: 'Rum, strawberries, lime juice, s.syrup', category: "citrus", favorite: true }
          ],
          spirits: [
            {name: "King's Jubilee", ingredients: 'Rum, maraschino, lemon juice', category: "citrus", favorite: true },
            {name: "Salty Bird", ingredients: 'Rum, Campari, pineapple juice, lime juice, s.syrup', category: "citrus", favorite: true }
          ]
        }
      }
    ]
  })
  
}
</script>
