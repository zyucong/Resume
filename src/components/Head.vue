<template>
  <div class="head-container">
    <div class="title">
      <h1 class="name">{{name}}</h1>
    </div>
    <!-- <hr> -->
    <div id="ticker-box">
      <p id="ticker-content">I don't know why I should do a ticker, but I want to do it to show that I can do it. Now it is long enough to be infinitely scrolling. </p>
    </div>
    <div class="tags">
      <p class="tag">Student <i class="material-icons">person</i> Tutor <i class="material-icons">person</i> Nerd</p>
    </div>
  </div>
</template>

<script>
import { setInterval } from 'timers';
export default {
  name: 'Head',
  props: ['name'],
  data() {
    return {
      box: null,
      text: null,
      boxWidth: 0,
      textWidth: 0
    }
  },
  mounted() {
    this.box = document.getElementById("ticker-box");
    this.text = document.getElementById("ticker-content");
    this.boxWidth = this.box.offsetWidth;
    this.textWidth = this.text.offsetWidth;
    if (this.boxWidth > this.textWidth) return false;
    this.text.innerHTML += this.text.innerHTML;
    // console.log(this.box.scrollLeft);
    // setInterval(this.scroll(), 10);
    setInterval(() => {
      if (this.box.scrollLeft >= this.text.offsetWidth / 2) {
        this.box.scrollLeft = 0;
      }
      this.box.scrollLeft++;
    }, 18);
  },
  methods: {
    scroll() {
      // console.log("interval");
      // setInterval(this.scroll(), 20);
    }
  }
}
</script>

<style>
.head-container {
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.head-container .name {
  color: white;
  font-size: 3rem;
}
.head-container #ticker-box {
  width: 40%;
  color: white;
  overflow: hidden;
  white-space: nowrap;
}
.head-container #ticker-content {
  display: inline-block;
}
.head-container hr {
  border: 0;
  height: 3px;
  border-radius: 25px;
  width: 40%;
  background-color: #919aa1;
}
.head-container .tag {
  font-size: 1.5rem;
  color: white;
  
}
.head-container .tag i {
  vertical-align: sub;
}
</style>