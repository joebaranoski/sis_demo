<template>
  <div class="bet-outcome">
    <div class="bet-name">
      <span>TB Buccaneers</span>
      <span style="margin-left: 80px;">-150</span>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        focusable="false"
        class="cancel-bet-icon"
        viewBox="0 0 24 24"
        color='var(--token-bcfe2c2e-c766-4df8-85c6-becee5abcaa7, rgba(43, 43, 61, 0.5)) /* {\"name\":\"$color-10\"} */'
        style="fill: var(--token-bcfe2c2e-c766-4df8-85c6-becee5abcaa7, rgba(43, 43, 61, 0.5)) ; flex-shrink: 0;"
      >
        <path
          d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"
        ></path>
      </svg>
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
  margin: 0 35px -10px 35px;
}

.bet-name {
  font-weight: 700;
  font-size: 20px;
  font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.bet-type {
  margin: 4px 0;
  font-size: 15px;
  font-weight: 700;
  color: rgba(24, 24, 41, 0.6);
}

.bet-event {
  font-size: 13px;
  font-weight: 500;
}

.cancel-bet-icon {
  width: 26px;
  margin-right: -10px;
}
</style>
