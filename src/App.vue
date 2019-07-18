<template>
  <div id="app">
    <Dots :num="this.cards.length" :selected="this.currentCard" :switch="updateCard" />
    <Card v-for="(card, index) in cards" :key="index" :card="card" :projects="card.content" >
      <!-- <Project v-if="card.component == 'project'" :projects="card.content" :title="card.title" :color="card.border_color" /> -->
    </Card>
  </div>
</template>

<script>
import Dots from '@/components/Dots.vue'
import Card from '@/components/Card.vue'
// import Project from '@/components/Project.vue'
import { setTimeout } from 'timers';
// import Glider from '@/components/Glider.vue'

export default {
  name: 'app',
  components: {
    Dots,
    Card
    // Glider
  },
  data() {
    return {
      threshold: 15,
      currentCard: 0,
      animation_time: 800,
      cards: [
        {id: "inner1", plain: true, color: '#272B30', component: "title", title: "card1",},
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
          }
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
        ]},
        // {id: "inner4", plain: true, color: '#272B30', component: "project", title: "card4",},
      ]
    }
  },
  mounted() {
    for (const [idx, card] of this.cards.entries()) {
      if (idx != this.currentCard) {
        // document.getElementById(card.id).style.opacity = '0';
        document.getElementById(card.id).classList.add('stickDown');
      } else {
        document.getElementById(card.id).classList.add('onStage');
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
      currentCard.style.opacity = null;
      // window.Velocity(currentCard, {'margin-top': '-100vh', 'opacity': 0}, time);
      currentCard.classList.remove('onStage');
      // currentCard.classList.add('fadeOut');
      currentCard.classList.add('fadeOutUp');
      nextCard.classList.remove('stickDown');
      // nextCard.classList.remove('fadeOutUp');
      // nextCard.classList.add("fadeIn");
      nextCard.classList.add('fadeIn');
      setTimeout(() => {
        currentCard.classList.remove('fadeOutUp');
        currentCard.classList.add('stickUp');
        nextCard.classList.remove('fadeIn')
        nextCard.classList.add('onStage')
      }, 1000);
    },
    goingUp() {
      const currentCard = this.getCurrentCard();
      --this.currentCard;
      const prevCard = this.getCurrentCard();
      currentCard.style.opacity = null;
      currentCard.classList.remove('onStage');
      currentCard.classList.add('fadeOutDown');
      prevCard.classList.remove('stickUp');
      // prevCard.classList.remove('fadeOutDown');
      prevCard.classList.add('fadeIn');
      setTimeout(() => {
        currentCard.classList.remove('fadeOutDown');
        currentCard.classList.add('stickDown');
        prevCard.classList.remove('fadeIn');
        prevCard.classList.add('onStage');
      }, 1000);
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
      if (goingdown) {
        const currentCard = this.getCurrentCard();
        currentCard.classList.remove('onStage');
        currentCard.classList.add('fadeOutUp');
        setTimeout(() => {
          currentCard.classList.remove('fadeOutUp');
          currentCard.classList.add('stickUp');
        }, 1000);
        while (this.currentCard != idx - 1) {
          ++this.currentCard;
          const nextCard = this.getCurrentCard();
          nextCard.classList.remove('stickDown');
          nextCard.classList.add('stickUp');
        }
        ++this.currentCard;
        const nextCard = this.getCurrentCard();
        nextCard.classList.remove('stickDown');
        nextCard.classList.add('fadeIn');
        setTimeout(() => {
          nextCard.classList.remove('fadeIn');
          nextCard.classList.add('onStage');
        }, 1000);
      } else {
        const currentCard = this.getCurrentCard();
        currentCard.classList.remove('onStage');
        currentCard.classList.add('fadeOutDown');
        setTimeout(() => {
          currentCard.classList.remove('fadeOutDown');
          currentCard.classList.add('stickDown');
        }, 1000);
        while (this.currentCard != idx + 1) {
          --this.currentCard;
          const prevCard = this.getCurrentCard();
          prevCard.classList.remove('stickUp');
          prevCard.classList.add('stickDown');
        }
        --this.currentCard;
        const prevCard = this.getCurrentCard();
        prevCard.classList.remove('stickUp');
        prevCard.classList.add('fadeIn');
        setTimeout(() => {
          prevCard.classList.remove('fadeIn');
          prevCard.classList.add('onStage');
        }, 1000);
      }
    }
  }
}
</script>

<style>
  #app {
    width: 100%;
    height: 100%;
    margin: 0;
    position: fixed;
    left: 0;
    top: 0;
    background-color: #272B30;
    overflow: hidden;
  }
</style>
