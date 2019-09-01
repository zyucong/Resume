<template>
    <div class="card-container">
      <!-- <div v-if="plain" class="poster plain-bg"> -->
      <div :id="card.id" class="poster plain-bg">
          <Head v-if="card.component == 'title'" :name="card.name"/>
          <Project v-if="card.component == 'project'" :projects="projects" :title="card.title" :color="card.border_color" :bg="card.background"/>
          <Foot v-if="card.component == 'footer'"/>
          <!-- <p>{{projects}}</p> -->
          <!-- <p>{{test}} {{card_id}}</p> -->
          <!-- <slot></slot> -->
      </div>
    </div>
</template>

<script>
import Head from '@/components/Head.vue'
import Project from '@/components/Project.vue'
import Foot from '@/components/Foot.vue'
export default {
    name: "Card",
    props: ['card', 'projects'],
    components: {
      Head,
      Project,
      Foot
    }
}
</script>

<style>
.card-container .plain-bg {
    background-color: #272B30;
    z-index: -10;
}
.card-container .poster {
    /* width: 100vw;
    height: 100vh; */
    width: 100%;
    height: 100%;
    position: fixed;
    /* top: 0; */
    left: 0;
}
.onStage {
  top: 0;
  opacity: 1;
}
.stickUp {
  top: -100%;
  opacity: 0;
}
.stickDown {
  top: 100%;
  opacity: 0;
}
.fadeOutDown {
  opacity: 0;
  top: 100%;
  /* transition-timing-function: ease-in-out; */
  transition: 1s;
}
.fadeOutUp {
  opacity: 0;
  top: -100%;
  /* transition-timing-function: ease-in-out; */
  transition: 1s;
}
.fadeIn {
  opacity: 1;
  top: 0;
  /* transition-timing-function: ease-in-out; */
  transition: 1s;
}
</style>
