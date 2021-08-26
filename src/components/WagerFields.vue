<template>
  <div class="wager-fields">
    <input
      class="wager-field"
      type="text"
      id="wager"
      name="wager"
      :value="wager"
      @input="$emit('handleWagerUpdate', $event.target.value)"
      @blur="$emit('handleWagerBlur')"
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
export default {
  name: 'WagerFields',
  props: {
    payout: String,
    wager: String,
  },
};
</script>

<style scoped>
input {
  height: 48px;
  background-color: #f5f5f5;
}

input:focus {
  outline-color: #01ebff;
}
</style>
