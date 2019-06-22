<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Card v-for="(card, index) in cards" :key="index" :plain="card.plain" :color="card.color" :card-id="card.id">
      <Glider v-if="component == 'title'" name="Julian Zhu" />
    </Card>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Card from '@/components/Card.vue'
import Glider from '@/components/Glider.vue'

export default {
  name: 'app',
  components: {
    Card
  },
  data() {
    return {
      cards: [
        {id: 1, plain: true, color: '#272B30', component: "title"},
        {id: 2, plain: false, color: null}
      ]
    }
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
