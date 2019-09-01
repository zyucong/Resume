<template>
  <div class="footer">
    <div class="content">
      <h1>Connect with me!</h1>
    </div>
    <div class="socials">
      <a href="https://github.com/zyucong"><github-circle class="link" /></a>
      <a href="https://www.linkedin.com/in/julian-zhu-666a74168/"><linkedin-box class="link" /></a>
      <a href="mailto:yingcongzhu@gmail.com"><email class="link" /></a>
    </div>
  </div>
</template>

<script>
import GithubCircle from 'vue-material-design-icons/GithubCircle.vue';
import LinkedinBox from 'vue-material-design-icons/LinkedinBox.vue';
import Email from 'vue-material-design-icons/Email.vue';

export default {
  name: "Foot",
  components: {
    GithubCircle,
    LinkedinBox,
    Email
  }
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
  width: 30%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.footer .socials .link {
  color: white;
  font-size: 2rem;
  /* display: flex;
  align-items: center;
  justify-content: center; */
}
</style>