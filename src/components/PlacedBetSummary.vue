<template>
  <div class="placed-bet-summary">
    <h1 class="summary-title">1 Picks</h1>
    <DetailRow
      heading="Event Details:"
      content="TB Buccaneers"
      subcontent="DAL Cowboys @ TB Buccaneers (M/L)"
    />
    <DetailRow heading="Bet:" content="$10.00" />
    <DetailRow heading="To Win:" content="$6.67" />
    <DetailRow heading="Payout" content="$16.67" />
    <DetailRow heading="Bet Date" :content="formattedDate" />
    <DetailRow heading="Bet ID" :content="`ID ${betId}`" />
    <button class="close-button" @click="$emit('handleCloseBetSummary')">
      Close
    </button>
  </div>
</template>

<script>
import { computed } from 'vue';
import { DateTime } from 'luxon';
import DetailRow from './DetailRow';

export default {
  name: 'PlacedBetSummary',
  components: {
    DetailRow,
  },
  props: {
    betId: Number,
    placedTime: String,
  },
  setup(props) {
    const formattedDate = computed(() => {
      const time = DateTime.fromISO(props.placedTime);

      return (
        time.toLocaleString(DateTime.TIME_24_WITH_SECONDS) +
        ' ' +
        time.toLocaleString(DateTime.DATE_SHORT)
      );
    });

    return { formattedDate };
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

.summary-title {
  color: white;
  background-color: #2b2b3d;
  margin: 10px;
  padding: 20px 10px;
  text-align: left;
  font-family: Inter-Extrabold, Inter, sans-serif;
  font-size: 24px;
  font-weight: 800;
  border-radius: 8px;
}

.close-button {
  background-color: white;
  border: none;
  font-size: 16px;
  margin-top: 8px;
  cursor: pointer;
}
</style>
