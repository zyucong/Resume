<template>
  <div id="app">
    <Dots :num="this.cards.length" :selected="this.currentCard" :switch="updateCard" />
    <Card v-for="(card, index) in cards" :key="index" :card_id="card.id" :plain="card.plain" :color="card.color" :test="card.test">
      <!-- <Glider v-if="component == 'title'" name="Julian Zhu" /> -->
      <Project v-if="card.component == 'project'" :projects="card.content" :title="card.title" :color="card.border_color" />
    </Card>
  </div>
</template>

<script>
import Dots from '@/components/Dots.vue'
import Card from '@/components/Card.vue'
import Project from '@/components/Project.vue'
import { setTimeout } from 'timers';
import { Promise } from 'q';
// import Glider from '@/components/Glider.vue'

export default {
  name: 'app',
  components: {
    Dots,
    Card,
    Project
    // Glider
  },
  data() {
    return {
      threshold: 15,
      currentCard: 0,
      animation_time: 800,
      cards: [
        {id: "inner1", plain: true, color: '#272B30', component: "title", test: "card1",},
        {id: "inner2", plain: false, image: true, color: null, test: "card2", title: "Web App",
        component: "project",
        border_color: '#29ABE0',
        content: [
          {
            title: "Sokoban Game",
            description: "A sokoban game implemented with UI designed found on Internet",
            link: "http://github.com"
          },
          {
            title : "My Resume (This Site)",
            description: "Apply skills with Vue on this site",
            link: "http://github.com"
          },
          // {
          //   title : "My Resume (This Site)",
          //   description: "Apply skills with Vue on this site",
          //   link: "http://github.com"
          // }
        ]},
        {id: "inner3", plain: false, image: true, color: null, test: "card3", title: "Little Script", 
        component: "project",
        border_color: "#93C54B",
        content: [
          {
            title: "Enrolment Monitor",
            description: "A script to periodically detect if there is vacancy on specific course",
            link: "http://github.com"
          },
          {
            title: "legit",
            description: "A script to mimic the behaviour of git",
            link: "http://github.com"
          }
        ]}
      ]
    }
  },
  mounted() {
    for (const [idx, card] of this.cards.entries()) {
      if (idx != this.currentCard) {
        // document.getElementById(card.id).style.opacity = '0';
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
    getCurrentCard() {
      return document.getElementById(this.cards[this.currentCard].id);
    },
    haltWheel() {
      document.removeEventListener("wheel", this.handleScroll);
      setTimeout(() => {document.addEventListener("wheel", this.handleScroll);}, 1000);
    },
    goingDown() {
      const currentCard = this.getCurrentCard();
      ++this.currentCard;
      const nextCard = this.getCurrentCard();
      // window.Velocity(currentCard, {'margin-top': '-100vh', 'opacity': 0}, time);
      currentCard.classList.remove('fadeIn');
      // currentCard.classList.add('fadeOut');
      currentCard.classList.add('fadeOutUp');
      nextCard.classList.remove('fadeOutDown');
      nextCard.classList.remove('fadeOutUp');
      // nextCard.classList.add("fadeIn");
      nextCard.classList.add('fadeIn');
    },
    goingUp() {
      const currentCard = this.getCurrentCard();
      --this.currentCard;
      const prevCard = this.getCurrentCard();
      currentCard.classList.remove('fadeIn');
      currentCard.classList.add('fadeOutDown');
      prevCard.classList.remove('fadeOutUp');
      prevCard.classList.remove('fadeOutDown');
      prevCard.classList.add('fadeIn');
    },
    handleScroll(e) {
      if (e.deltaY > this.threshold && this.currentCard < this.cards.length - 1) {
        // document.removeEventListener("wheel", this.handleScroll);
        // setTimeout(() => {document.addEventListener("wheel", this.handleScroll);}, 1000);
        this.haltWheel();
        this.goingDown();
      }
      if (e.deltaY < - this.threshold && this.currentCard > 0) {
        // document.removeEventListener("wheel", this.handleScroll);
        // setTimeout(() => {document.addEventListener("wheel", this.handleScroll);}, 1000);
        this.haltWheel();
        this.goingUp();
      }
    },
    updateCard(idx) {
      this.haltWheel();
      const goingdown = idx > this.currentCard ? true : false;
      while(idx != this.currentCard) {
        if (goingdown) {
          const currentCard = this.getCurrentCard();
          this.currentCard = idx;
          // console.log(idx);
          const nextCard = this.getCurrentCard();
          console.log(nextCard);
          currentCard.classList.remove('fadeIn');
          currentCard.classList.add('fadeOutUp');
          nextCard.classList.remove('fadeOutDown');
          nextCard.classList.remove('fadeOutUp');
          nextCard.classList.add('fadeIn');
        } else {
          const currentCard = this.getCurrentCard();
          this.currentCard = idx;
          const prevCard = this.getCurrentCard();
          console.log(prevCard);
          currentCard.classList.remove('fadeIn');
          currentCard.classList.add('fadeOutDown');
          prevCard.classList.remove('fadeOutUp');
          prevCard.classList.remove('fadeOutDown');
          prevCard.classList.add('fadeIn');
        }
      }
    }
  }
}
</script>

<style>
  #app {
    width: 100vw;
    height: 100vh;
    background-color: #272B30;
    overflow: hidden;
  }
</style>
