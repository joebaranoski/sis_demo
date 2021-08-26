<template>
  <div class="place-bet-container">
    <button
      class="place-bet"
      @click="$emit('placeBet')"
      :disabled="!canPlaceBet"
    >
      <span style="font-weight: 700; font-size: 16px"
        >PLACE {{ wager || '$0.00' }} BET</span
      >
      <span style="font-weight: 700; font-size: 11px; margin-top: 6px;"
        >TO RETURN: {{ payout }}</span
      >
    </button>
    <span class="disclaimer">
      Please Note: With wager singles you can only place one bet at a time
    </span>
  </div>
</template>

<script>
export default {
  name: 'PlaceBetButton',
  props: {
    canPlaceBet: Boolean,
    payout: String,
    wager: String,
  },
};
</script>

<style scoped>
.place-bet-container {
  margin-top: 40px;
}

.place-bet {
  display: flex;
  flex-direction: column;
  width: 325px;
  max-width: 95%;
  margin: 10px auto;
  background-color: #02ccff;
  border: none;
  border-radius: 5px;
  align-items: center;
  padding: 14px;
  cursor: pointer;
}

.disclaimer {
  font-size: 10px;
  font-weight: 500;
  color: rgba(24, 24, 41, 0.6);
}
</style>
