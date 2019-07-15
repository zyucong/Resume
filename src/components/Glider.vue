<template>
    <div>
        <h1>{{name}}</h1>
        <hr>
        <div id="gliders">
            <div class="glider">
                
            </div>
        </div>
    </div>
</template>

<script>
import { setInterval } from 'timers';
export default {
  name: "Glider",
  props: [],
  data() {
    return {
      myInterval: null,
      introductions: [
        {
          text: "Student Developer",
          color: ""
        },
        {
          text: "Looking for opportunities",
          color: ""
        }
      ],
      cnt: 0
    }
  },
  methods: {
    slide() {

    },
    reset() {

    }
  },
  created() {
    this.myInterval = setInterval(this.slides, 5000);
  },
  destroyed() {
    window.clearInterval(this.myInterval);
  }
}
</script>
