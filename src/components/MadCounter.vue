<template>
  <h1>{{ title }}</h1>
  <aside>
    <Controls @play="start()" @stop="finish()" @pause="wait()" />
  </aside>
  <section>
    <div id="counter">
      Contador: <span id="counterValue">{{ counterValue }}</span>
    </div>
  </section>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import Controls from "./Controls.vue";
export default defineComponent({
  name: "MadCounter",
  props: {
    title: String,
  },
  data() {
    return {
      counterValue: 0,
      counterId: 0,
    };
  },
  components: {
    Controls,
  },
  methods: {
    start() {
      this.counterId = setInterval(() => {
        this.counterValue++;
      }, 1000);
    },
    wait() {
      clearInterval(this.counterId);
    },
    finish() {
      clearInterval(this.counterId);
      this.counterValue = 0;
    },
  },
});
</script>
<style scoped>
h1 {
  text-align: center;
  margin-bottom: 1rem;
}
aside {
  display: flex;
  justify-content: center;
}
section {
  text-align: center;
}
#counter{
  font-size: 1.5em;
}
@media screen and (max-width: 430px){
  aside{
    display: grid;
  }; 
}
h1, #counter{
  padding: 0.7rem;
}
</style>
