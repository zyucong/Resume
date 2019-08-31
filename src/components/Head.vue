<template>
  <div class="head-container">
    <div class="title">
      <h1 class="name">{{name}}</h1>
    </div>
    <hr>
    <div class="tags">
      <p class="tag">Student <i class="material-icons">person</i> Tutor <i class="material-icons">person</i> Nerd</p>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Head',
    props: ['name']

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