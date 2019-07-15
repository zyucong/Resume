<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Card v-for="(card, index) in cards" :key="index" :plain="card.plain" :color="card.color" :card_id="card.id" :test="card.test">
      <!-- <Glider v-if="component == 'title'" name="Julian Zhu" /> -->
    </Card>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Card from '@/components/Card.vue'
import { setTimeout } from 'timers';
// import Glider from '@/components/Glider.vue'

export default {
  name: 'app',
  components: {
    Card
    // Glider
  },
  data() {
    return {
      threshold: 15,
      currentCard: 0,
      cards: [
        {id: "inner1", plain: true, color: '#272B30', component: "title", test: "card1"},
        {id: "inner2", plain: false, image: true, color: null, test: "card2"},
        {id: "inner3", plain: false, image: true, color: null, test: "card3"}
      ]
    }
  },
  mounted() {
    for (const [idx, card] of this.cards.entries()) {
      if (idx != this.currentCard) {
        document.getElementById(card.id).style.opacity = '0';
      }
    }
  },
  created() {
    document.addEventListener("wheel", this.handleScroll);
  },
  destroyed() {
    document.removeEventListener("wheel", this.handleScroll);
  },
  methods: {
    handleScroll(e) {
      const animation_time = 800
      if (e.deltaY > this.threshold && this.currentCard < this.cards.length) {
        document.removeEventListener("wheel", this.handleScroll);
        setTimeout(() => {document.addEventListener("wheel", this.handleScroll);}, 1000);
        // eslint-disable-next-line
        // console.log("wheeled");
        const currentCard = document.getElementById(this.cards[this.currentCard].id);
        ++this.currentCard;
        const nextCard = document.getElementById(this.cards[this.currentCard].id);
        window.Velocity(currentCard, {'margin-top': '-100vh', 'opacity': 0}, animation_time);
        // window.Velocity(currentCard, {'opacity': 0}, animation_time);
        window.Velocity(nextCard, {'opacity': 1}, animation_time);
      }
      if (e.deltaY < - this.threshold && this.currentCard > 0) {
        document.removeEventListener("wheel", this.handleScroll);
        setTimeout(() => {document.addEventListener("wheel", this.handleScroll);}, 1000);
        const currentCard = document.getElementById(this.cards[this.currentCard].id);
        --this.currentCard;
        const prevCard = document.getElementById(this.cards[this.currentCard].id);
        window.Velocity(currentCard, {'opacity': 0}, animation_time);
        window.Velocity(prevCard, {'opacity': 1, 'margin-top': '0vh'}, animation_time);
      }
    }
  }
}
</script>

<style scoped>
  #app {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
  }
</style>
