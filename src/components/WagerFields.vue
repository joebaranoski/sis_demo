<template>
  <div class="wager-fields">
    <input
      class="wager-field"
      type="text"
      id="wager"
      name="wager"
      v-model="wager"
      @blur="formatInput"
      placeholder="$0.00"
    />
    <input
      class="wager-field"
      type="text"
      disabled
      id="payout"
      name="payout"
      :value="payout"
    />
  </div>
</template>

<script>
import { computed, ref } from 'vue';

/** Shamelessly stolen from internet */
function isNumeric(str) {
  if (typeof str != 'string') return false; // we only process strings!
  return (
    !isNaN(str) && !isNaN(parseFloat(str)) // use type coercion to parse the _entirety_ of the string (`parseFloat` alone does not do this)...
  ); // ...and ensure strings of whitespace fail
}

export default {
  name: 'WagerFields',
  setup() {
    const wager = ref('');
    const payout = computed(() => {
      if (!wager.value) {
        return '$0.00';
      }

      const wagerNum = wager.value.replace('$', '');

      if (!isNumeric(wagerNum)) {
        return '$0.00';
      }

      return `$${(Number(wagerNum) * 1.666).toFixed(2)}`;
    });

    const formatInput = () => {
      const wagerNum = wager.value.replace('$', '');

      if (isNumeric(wagerNum)) {
        wager.value = `$${Number(wagerNum).toFixed(2)}`;
      }
    };

    return { payout, formatInput, wager };
  },
};
</script>

<style scoped></style>
