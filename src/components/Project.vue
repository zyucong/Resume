<template>
  <div class="project-container">
    <div class="title">
      <h1>{{title}}</h1>
    </div>
    <div class="container" :style="{'border-color': color}">
      <div v-for="(project, index) in projects" :key="index">
        <!-- <p>{{project.title}}</p>
        <p>{{project.description}}</p> -->
        <div class="proj">
          <div class="proj-title">
            <h2>{{project.title}}</h2>
          </div>
          <div class="detail">
            <div class="icon">
              <a :href="project.link"><i class="material-icons">link</i></a>
            </div>
            <div class="description">
              <p>{{ project.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Project',
  props: ['projects', 'title', 'color']
}
</script>

<style>
.project-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
  justify-content: center;
}

.project-container .title {
  font-size: 4rem;
  margin-top: 10vh;
  margin-bottom: 10vh;
  /* margin: 0; */
  /* height: 30vh; */
}

.project-container .container {
  width: 60vw;
  height: 70vh;
  border-top: 3px solid;
  border-right: 3px solid;
  border-left: 3px solid;
  padding: 4rem;
  /* padding-top: 4rem; */
  display: flex;
  flex-direction: column;
}

.project-container .proj {
  height: 7rem;
  margin: 0 auto;
  margin-bottom: 4rem;
}
.project-container .proj .proj-title {
  height: 40%;
}
.project-container .proj .proj-title h2 {
  margin: 0;
  font-size: 2rem;
}
.project-container .proj .detail {
  height: 60%;
  display: flex;
  flex-direction: row;
}
.project-container .proj .detail .icon {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  border-right: solid 2px;
}
.project-container .proj .detail .icon a {
  opacity: 0.4;
  cursor: pointer;
  color: white;
  margin-right: 1rem;
  line-height: 0;
}
.project-container .proj .detail .icon a i {
  font-size: 2rem;
}
.project-container .proj .detail .icon a:hover {
  opacity: 1;
}
.project-container .proj .detail .description {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 5%;
  margin-top: 0;
  margin-bottom: 0;
  font-size: 1.5rem;
}
</style>
