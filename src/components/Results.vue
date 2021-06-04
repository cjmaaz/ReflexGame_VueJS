<template>
  <h3>Reaction Time: {{ score }}ms</h3>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: {
    score: Number,
  },
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Super Human";
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail Pace";
    }
  },
};
</script>

<style scoped>
h3 {
  margin: 3rem auto;
}
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>