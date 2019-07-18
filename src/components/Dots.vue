<template>
  <div class="dots-container">
    <div class="dots">
      <div class="dot" v-for="(dot, idx) in num" :key="idx" >
        <i class="material-icons" v-if="selected == dot - 1">radio_button_checked</i>
        <i class="material-icons" v-else @click="toggle(dot - 1)">radio_button_unchecked</i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Dots',
  props: ['num', 'selected', 'switch'],
  methods: {
    toggle(index) {
      this.switch(index);
    }
  }
}
</script>

<style>
.dots-container {
  display: flex;
  /* width: 10vw; */
  align-items: center;
  height: 100%;
  position: fixed;
  z-index: 10;
}
.dots-container .dots {
  display: flex;
  flex-direction: column;
  margin-left: 5rem;
}
.dots-container .dot {
  margin-bottom: 1rem;
  color: white;
}
.dots-container .material-icons:hover {
  cursor: pointer;
  opacity: 0.5;
}
</style>
