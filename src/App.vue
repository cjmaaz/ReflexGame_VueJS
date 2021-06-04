<template>
  <h1>Reaction Game</h1>
  <button @click="renderBlock" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="setScore" />
  <Results v-if="scoreAvail" :score="score" />
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      scoreAvail: false,
    };
  },
  methods: {
    renderBlock() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.scoreAvail = false;
    },
    setScore(rectionTime) {
      this.score = rectionTime;
      this.isPlaying = false;
      this.scoreAvail = true;
    },
  },
  components: {
    Block,
    Results,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  text-align: center;
  color: #333;
  margin-top: 2rem;
}
h1 {
  margin: 2rem auto;
}
button {
  background: #0faf87;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 0.5rem 1rem;
}
button:hover,
button:active {
  background: #027e5f;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 0.5rem 1.2rem;
}
button:disabled {
  background: rgba(0, 0, 0, 0.6);
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 0.5rem 1rem;
}
</style>