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
import HelloWorld from '@/components/HelloWorld.vue'
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
          ],
          spirits: [
            {name: 'Old Fashioned', ingredients: 'Bourbon, bitters, s.syrup', category: "spirits", favorite: false },
          ]
        }
      },
      {
        name: "Gin",
        drinkList: {
          citrus: [
            {name: 'Tom Collins', ingredients: 'Gin, lemon juice, s.syrup, soda', category: "citrus", favorite: false },
            {name: 'Negroni', ingredients: 'Gin, Campari, sweet vermouth, bitters', category: "spirit", favorite: true }
          ]
        }
      },
      {
        name: "Rum",
        drinkList: {
          citrus: [
            {name: 'Mojito', ingredients: 'Rum, lime juice, mint, s.syrup', category: "citrus", favorite: false },
            {name: 'Daiquiri', ingredients: 'Rum, lime juice, s.syrup', category: "citrus", favorite: true }
          ]
        }
      }
    ]
  })
  
}
</script>
