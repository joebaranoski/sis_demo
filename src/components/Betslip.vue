<template>
  <div :class="classNames" @click="handleBetslipClick">
    <button class="betslip-button" @click.stop="handleToggleBetslip"></button>
    <div class="summary" v-if="!betslipOpen">
      <PickCount />
      <span class="balance">BALANCE: $240.00</span>
    </div>
    <div
      v-else
      :class="{ 'wager-box': true, 'wager-box-loaded': showWagerBoxes }"
    >
      <span class="balance" style="align-self: flex-end">BALANCE: $240.00</span>
      <BetOutcome />
      <WagerFields
        @handleWagerUpdate="updateWager"
        @handleWagerBlur="formatInput"
        :payout="payout"
        :wager="wager"
      />
      <PlaceBetButton
        @placeBet="$emit('placeBet')"
        :canPlaceBet="canPlaceBet"
        :payout="payout"
        :wager="wager"
      />
    </div>
  </div>
</template>

<script>
import { computed, ref } from 'vue';
import BetOutcome from './BetOutcome.vue';
import PickCount from './PickCount.vue';
import PlaceBetButton from './PlaceBetButton.vue';
import WagerFields from './WagerFields.vue';

/** Shamelessly stolen from internet */
export function isNumeric(str) {
  if (typeof str != 'string') return false; // we only process strings!
  return (
    !isNaN(str) && !isNaN(parseFloat(str)) // use type coercion to parse the _entirety_ of the string (`parseFloat` alone does not do this)...
  ); // ...and ensure strings of whitespace fail
}

export default {
  name: 'Betslip',
  components: {
    BetOutcome,
    PickCount,
    PlaceBetButton,
    WagerFields,
  },
  props: {
    buttonsHighlighted: Boolean,
  },
  setup(props) {
    const betslipOpen = ref(false);
    const showWagerBoxes = ref(false);
    const wager = ref('');

    const handleToggleBetslip = () => {
      if (!betslipOpen.value) {
        setTimeout(() => {
          showWagerBoxes.value = true;
        }, 50);
      } else {
        showWagerBoxes.value = false;
      }

      betslipOpen.value = !betslipOpen.value;
    };

    const handleBetslipClick = () => {
      if (betslipOpen.value) {
        return;
      }

      handleToggleBetslip();
    };

    const updateWager = (updatedWager) => {
      wager.value = updatedWager;
    };

    const formatInput = () => {
      if (isNumeric(wagerNum.value)) {
        wager.value = `$${Number(wagerNum.value).toFixed(2)}`;
      }
    };

    const wagerNum = computed(() => {
      return wager.value.replace('$', '');
    });

    const payout = computed(() => {
      if (!wager.value) {
        return '$0.00';
      }

      if (!isNumeric(wagerNum.value)) {
        return '$0.00';
      }

      return `$${(Number(wagerNum.value) * 1.666).toFixed(2)}`;
    });

    const canPlaceBet = computed(() => {
      return Boolean(isNumeric(wagerNum.value) && Number(wagerNum.value > 0));
    });

    const classNames = computed(() => ({
      betslip: true,
      open: betslipOpen.value,
      hightlightable: !betslipOpen.value,
      highlighted: !betslipOpen.value && props.buttonsHighlighted,
    }));

    return {
      betslipOpen,
      canPlaceBet,
      classNames,
      handleBetslipClick,
      handleToggleBetslip,
      formatInput,
      payout,
      showWagerBoxes,
      updateWager,
      wager,
    };
  },
};
</script>

<style scoped>
.betslip {
  background-color: white;
  height: 120px;
  width: 100%;
  max-height: 100%;
  margin-top: auto;
  cursor: pointer;
  border-radius: 15px 15px 0 0;
  transition: height 0.25s;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.open {
  height: 510px;
  cursor: default;
}

.betslip-button {
  cursor: pointer;
  width: 70px;
  height: 10px;
  border-radius: 5px;
  border: none;
  background-color: #e9e9eb;
  margin: 24px;
}

.hightlightable::before {
  background-color: rgba(60, 182, 223, 0.3);
  content: '';
  position: absolute;
  width: 100%;
  border-top: 3px solid rgba(43, 130, 160, 0.6);
  margin-top: 5px;
  height: 100%;
  left: 0;
  opacity: 0;
  transition: opacity 0.25s;
}

.highlighted::before {
  opacity: 1;
}

.summary {
  display: flex;
  width: calc(100% - 40px);
  max-width: calc(100% - 20px);
  height: 40px;
  margin: 0 10px 20px;
  background-color: #f5f5f5;
  padding: 5px 10px;
  border-radius: 2px;
  align-items: center;
  font-weight: bold;
}

.balance {
  width: 50%;
  max-height: 20px;
  text-align: end;
}

.wager-box {
  display: flex;
  flex-direction: column;
  opacity: 0;
  transition: opacity 0.25s;
}

.wager-box-loaded {
  opacity: 1;
}
</style>
