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

<style scoped>
.plain-bg {
    background-color: #272B30;
}
.poster {
    width: 100vw;
    height: 100vh;
}

.placeholder {
    width: 100%;
    height: 100%;
}

</style>
