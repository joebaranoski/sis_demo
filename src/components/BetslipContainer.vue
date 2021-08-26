<template>
  <div class="betslip-container">
    <Betslip
      v-if="!betPlaced"
      :buttonsHighlighted="buttonsHighlighted"
      @placeBet="placeBet"
    />
    <PlacedBetSummary
      v-else
      :betId="betId"
      :placedTime="placedTime"
      @handleCloseBetSummary="returnToBetslip"
    />
  </div>
</template>

<script>
import { ref } from 'vue';
import Axios from 'axios';
import Betslip from './Betslip.vue';
import PlacedBetSummary from './PlacedBetSummary.vue';

export default {
  name: 'BetslipContainer',
  props: {
    buttonsHighlighted: Boolean,
  },
  components: {
    Betslip,
    PlacedBetSummary,
  },
  setup() {
    const betPlaced = ref(false);
    const placedTime = ref(null);
    const betId = ref(null);

    const placeBet = () => {
      Axios.get(
        'https://401054ce-ca4d-4969-9dc2-9d81eedab1e3.mock.pstmn.io/placebet',
      ).then(({ data }) => {
        betPlaced.value = true;
        placedTime.value = data.placedTime;
        betId.value = data.betId;
      });
    };

    const returnToBetslip = () => {
      betPlaced.value = false;
    };

    return { betId, betPlaced, placeBet, placedTime, returnToBetslip };
  },
};
</script>

<style scoped>
.betslip-container {
  background-color: #2b2b3d;
  max-height: 100%;
  height: 815px;
  width: 380px;
  max-width: 100%;
  margin: auto;
  display: flex;
  flex-direction: vertical;
  position: relative;
}
</style>
