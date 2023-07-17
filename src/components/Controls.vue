<template>
  <button
    @click="
      $emit('play');
      changeStatus('running');
    "
    :disabled="isRunning"
  >
    <span class="icon">
      <i class="fas fa-play"></i>
    </span>
    <span>Play</span>
  </button>

  <button
    @click="
      $emit('pause');
      changeStatus('paused');
    "
    :disabled="isPaused || (!isRunning && !isPaused)"
  >
    <span class="icon">
      <i class="fas fa-pause"></i>
    </span>
    <span>Pause</span>
  </button>
  <button
    @click="
      $emit('stop');
      changeStatus('stopped');
    "
    :disabled="!isRunning && !isPaused"
  >
    <span class="icon">
      <i class="fas fa-stop"></i>
    </span>
    <span>Stop</span>
  </button>
</template>
<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Controls",
  emits: ["play", "pause", "stop"],
  data() {
    return {
      isRunning: false,
      isPaused: false,
    };
  },
  methods: {
    changeStatus(status: String) {
      console.log(status);

      switch (status) {
        case "running":
          this.isRunning = true;
          this.isPaused = false;
          break;
        case "paused":
          this.isRunning = false;
          this.isPaused = true;
          break;
        case "stopped":
          this.isRunning = false;
          this.isPaused = false;
          break;
        default:
          throw new Error("Estado desconhecido: " + status);
      }
    },
  },
});
</script>
<style scoped>
button {
  width: 33%;
  height: 5rem;
  cursor: pointer;
  border-radius: 0.4rem;
  outline: none;
  border: 1px black solid;
}
span {
  padding: 4px;
  font-size: 1rem;
}
:disabled {
  background-color: #ccc;
}
@media screen and (max-width: 430px){
  button{
    width: 15em;
    margin-bottom: 0.2rem;
  }
}
</style>
