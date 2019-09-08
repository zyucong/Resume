<template>
  <div class="head-container">
    <div class="title">
      <h1 class="name">{{name}}</h1>
    </div>
    <!-- <hr> -->
    <div id="ticker-box">
      <p id="ticker-content">Thank you for visiting my site. Hope you like it!</p>
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
  mounted() {
    let box = document.getElementById("ticker-box");
    let text = document.getElementById("ticker-content");
    let boxWidth = box.offsetWidth;
    let textWidth = text.offsetWidth;
    // now even it is shorter, should be able to scroll
    // if (this.boxWidth > this.textWidth) return false;
    // save a copy
    let content = text.innerHTML;
    text.innerHTML = '&nbsp';
    // console.log(text.offsetWidth);
    // how long is a space
    let spaces = boxWidth / text.offsetWidth;
    text.innerHTML = '';
    // fill the spaces before and after the sentences
    text.innerHTML += '&nbsp'.repeat(spaces);
    text.innerHTML += content;
    text.innerHTML += '&nbsp'.repeat(spaces + 100);
    let threshold = boxWidth + textWidth;
    setInterval(() => {
      if (box.scrollLeft >= threshold) {
        box.scrollLeft = 0;
      }
      box.scrollLeft++;
    }, 15);
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
@media screen and (max-width: 720px) {
  .head-container #ticker-box {
    width: 60%;
  }
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