<template>
    <div class="card-container">
      <div v-if="plain" class="poster plain-bg">
        <div class="placeholder">
          <slot></slot>
        </div>
      </div>
    </div>
</template>

<script>

export default {
    name: "Card",
    props: ["card-id", "color", "plain", "component"]
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
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>
