<template>
  <div class="footer">
    <div class="content">
      <h1>Connect with me!</h1>
    </div>
    <div class="socials">
      <a class="link" href="">Github</a>
      <a class="link" href="">LinkedIn</a>
      <a class="link" href="">Email</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Foot"
}
</script>

<style>
.footer {
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.footer .content {
  margin-bottom: 2rem;
}
.footer .content h1 {
  color: white;
  font-size: 3rem;
}
.footer .socials {
  width: 40%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
/* .footer .socials .link {
  display: flex;
  align-items: center;
  justify-content: center;
} */
</style>