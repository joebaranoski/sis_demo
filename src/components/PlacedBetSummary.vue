<template>
  <div class="placed-bet-summary">
    <span>{{ placedTime }}</span>
    <span>{{ betId }}</span>
  </div>
</template>

<script>
export default {
  name: 'PlacedBetSummary',
  props: {
    betId: Number,
    placedTime: String,
  },
};
</script>

<style scoped>
.placed-bet-summary {
  background-color: white;
  height: 480px;
  width: 100%;
  max-height: 100%;
  margin: auto;
  border-radius: 5px;
  transition: height 0.25s;
  position: relative;
}
</style>
