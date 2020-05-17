<template>
  <div id="app">
    <section class="app-header">
      <img 
        alt="Vue logo"
        src="./assets/logo.png"
      >
      <h1>Vue Basics</h1>
    </section>
    <div>
      <div
        v-for="beer in beers" 
        :key="beer.id"
        class="beers-list"
      >
        <div class="beer-card">
          <div class="beer-card-img-container">
            <img
              height="120px" 
              :src="beer.image_url"
            >
          </div>
          <div class="beer-card-body">
            <div>
              <strong>{{ beer.name }}</strong> 
            </div>
            <div>
              <span class="beer-card-tagline">{{ beer.tagline }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return {
      beers: [
        {
            "id":1,
            "name":"Buzz",
            "tagline":"A Real Bitter Experience.",
            "first_brewed":"09/2007",
            "description":"A light, crisp and bitter IPA brewed with English and American hops. A small batch brewed only once.",
            "image_url":"https://images.punkapi.com/v2/keg.png",
            "food_pairing":[
              "Spicy chicken tikka masala",
              "Grilled chicken quesadilla",
              "Caramel toffee cake"
            ],
            "brewers_tips":"The earthy and floral aromas from the hops can be overpowering. Drop a little Cascade in at the end of the boil to lift the profile with a bit of citrus.",
            "contributed_by":"Sam Mason <samjbmason>"
        },
        {
            "id":2,
            "name":"Trashy Blonde",
            "tagline":"You Know You Shouldn't",
            "first_brewed":"04/2008",
            "description":"A titillating, neurotic, peroxide punk of a Pale Ale. Combining attitude, style, substance, and a little bit of low self esteem for good measure; what would your mother say? The seductive lure of the sassy passion fruit hop proves too much to resist. All that is even before we get onto the fact that there are no additives, preservatives, pasteurization or strings attached. All wrapped up with the customary BrewDog bite and imaginative twist.",
            "image_url":"https://images.punkapi.com/v2/2.png",
            "food_pairing":[
              "Fresh crab with lemon",
              "Garlic butter dipping sauce",
              "Goats cheese salad",
              "Creamy lemon bar doused in powdered sugar"
            ],
            "brewers_tips":"Be careful not to collect too much wort from the mash. Once the sugars are all washed out there are some very unpleasant grainy tasting compounds that can be extracted into the wort.",
            "contributed_by":"Sam Mason <samjbmason>"
        },
        {
            "id":3,
            "name":"Berliner Weisse With Yuzu - B-Sides",
            "tagline":"Japanese Citrus Berliner Weisse.",
            "first_brewed":"11/2015",
            "description":"Japanese citrus fruit intensifies the sour nature of this German classic.",
            "image_url":"https://images.punkapi.com/v2/keg.png",
            "food_pairing":[
              "Smoked chicken wings",
              "Miso ramen",
              "Yuzu cheesecake"
            ],
            "brewers_tips":"Clean everything twice. All you want is the clean sourness of lactobacillus.",
            "contributed_by":"Sam Mason <samjbmason>"
        },
        {
            "id":4,
            "name":"Pilsen Lager",
            "tagline":"Unleash the Yeast Series.",
            "first_brewed":"09/2013",
            "description":"Our Unleash the Yeast series was an epic experiment into the differences in aroma and flavour provided by switching up your yeast. We brewed up a wort with a light caramel note and some toasty biscuit flavour, and hopped it with Amarillo and Centennial for a citrusy bitterness. Everything else is down to the yeast. Pilsner yeast ferments with no fruity esters or spicy phenols, although it can add a hint of butterscotch.",
            "image_url":"https://images.punkapi.com/v2/4.png",
            "food_pairing":[
              "Spicy crab cakes",
              "Spicy cucumber and carrot Thai salad",
              "Sweet filled dumplings"
            ],
            "brewers_tips":"Play around with the fermentation temperature to get the best flavour profile from the individual yeasts.",
            "contributed_by":"Ali Skinner <AliSkinner>"
        },
        {
            "id":5,
            "name":"Avery Brown Dredge",
            "tagline":"Bloggers' Imperial Pilsner.",
            "first_brewed":"02/2011",
            "description":"An Imperial Pilsner in collaboration with beer writers. Tradition. Homage. Revolution. We wanted to showcase the awesome backbone of the Czech brewing tradition, the noble Saaz hop, and also tip our hats to the modern beers that rock our world, and the people who make them.",
            "image_url":"https://images.punkapi.com/v2/5.png",
            "food_pairing":[
              "Vietnamese squid salad",
              "Chargrilled corn on the cob with paprika butter",
              "Strawberry and rhubarb pie"
            ],
            "brewers_tips":"Make sure you have a big enough yeast starter to ferment through the OG and lager successfully.",
            "contributed_by":"Sam Mason <samjbmason>"
        }
    ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

.app-header{
  display: flex;
  align-items: center;
  margin-bottom: 12px;
  border-bottom: 1px solid #dbdbdb;
}
.app-header img {
    height: 30px;
    margin-right: 16px;
  }
.app-header h1 {
  margin: 0;
}

.beers-list{
  max-width: 800px;
}

.beer-card{
  display: flex;
  border: 1px solid #eee;
  border-radius: 10px;
  padding: 12px;
  margin-bottom: 12px;
}

.beer-card-body{
  padding: 0 8px;
}

.beer-card-img-container{
  min-width: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.beer-card-tagline{
  font-size: 14px;
  background-color: #eee;
  padding: 0 8px;
  margin-left: 8px;
}

.beer-card-actions{
  margin-left: auto;
  display: flex;
  flex-direction: column;
  flex: 0 0 auto;
}

.beer-card-action{
  cursor: pointer;
  margin: 4px 0;
  user-select:none;
  text-align: right;
}

</style>
