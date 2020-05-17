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
      <div class="totals">
        <div class="totals-reaction">
          <h2>🍺 Love</h2>
          <span>{{ totalLoved }}</span>
        </div>
        <div class="totals-reaction">
          <h2>🤮 Hate</h2>
          <span>{{ totalHated }}</span>
        </div>
      </div>
      <div
        v-for="beer in beers" 
        :key="beer.id"
        class="beers-list"
      >
        <div
          class="beer-card"
          :style="{
            'border-color': getBorderColor(beer.id)
          }"
        >
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
            <div>
              <span v-if=" beer.description.length > MAX_CHARS">
                {{ `${beer.description.substring(0,MAX_CHARS)}...` }}
              </span>
              <span v-else>
                {{ beer.description }}
              </span>
            </div>
          </div>
          <actions-list
            :actions="actions"
            @action-click="runAction(beer.id, $event)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ActionsList from './components/ActionsList'

export default {
  name: 'App',
  components: {
    ActionsList
  },
  data(){
    return {
      MAX_CHARS: 200,
      reactions: {},
      actions:[{
        emoji: '🍺',
        name: 'love',
        label: 'Love it!'
      },
      {
        emoji: '🤮',
        name: 'hate',
        label: 'Hate it!'
      }
      ],
      beers: []
    }
  },
  computed:{
    totalReactions(){
      return Object.values(this.reactions)
    },
    totalLoved(){
      return this.totalReactions.filter(reaction => reaction === 'love').length  
    },
    totalHated(){
      return this.totalReactions.filter(reaction => reaction === 'hate').length 
    }
  },
  created(){
    fetch('https://api.punkapi.com/v2/beers?per_page=5')
    .then(response => response.json())
    .then(json => this.beers = json)
  },
  methods:{
    runAction(beerId, name){
      if(this.reactions[beerId] === name) {
        this.reactions[beerId] = null
        return
      }
      this.reactions = {
        ...this.reactions,
        [beerId]: name
      }
    },
    getBorderColor(beerId){
      const beerReaction = this.reactions[beerId]
      if(!beerReaction) return '#eee'
      const color = beerReaction === 'love' ? 'green' : 'red'
      return color
    }
  }
}
</script>

<style scoped>
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

.totals{
  display: flex;
  justify-content: space-evenly;
  text-align: center;
}

.totals-reaction{
  padding: 12px;
}

</style>
