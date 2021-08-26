<template>
  <div class="bet-outcome">
    <div class="bet-name">
      <span>TB Buccaneers</span>
      <span>-150</span>
    </div>
    <span class="bet-type" style="align-self: flex-start">MONEYLINE</span>
    <span class="bet-event" style="align-self: flex-start">
      DAL Cowboys @ TB Buccaneers
    </span>
  </div>
</template>

<script>
export default {
  name: 'BetOutcome',
};
</script>

<style scoped>
.bet-outcome {
  display: flex;
  flex-direction: column;
  margin: 0 35px;
}

.bet-name {
  font-weight: 700;
  font-size: 20px;
  font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';
  display: flex;
  justify-content: space-between;
}
</style>
