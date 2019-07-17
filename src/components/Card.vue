<template>
    <div class="card-container">
      <!-- <div v-if="plain" class="poster plain-bg"> -->
      <div :id="card_id" class="poster plain-bg">
        <div class="placeholder">
          <!-- <p>{{test}} {{card_id}}</p> -->
          <slot></slot>
        </div>
      </div>
    </div>
</template>

<script>

export default {
    name: "Card",
    props: ["card_id", "color", "plain", "test", "projects"]
}
</script>

<style>
.card-container .plain-bg {
    background-color: #272B30;
}
.card-container .poster {
    width: 100vw;
    height: 100vh;
}
.card-container .placeholder {
    width: 100%;
    height: 100%;
}
.fadeOutDown {
  /* opacity: 0; */
  margin-top: 100vh;
  /* transition-timing-function: ease-in-out; */
  transition: 1s;
}
.fadeOutUp {
  /* opacity: 0; */
  margin-top: -100vh;
  /* transition-timing-function: ease-in-out; */
  transition: 1s;
}
.fadeIn {
  /* opacity: 1; */
  margin-top: 0vh;
  /* transition-timing-function: ease-in-out; */
  transition: 1s;
}
</style>
