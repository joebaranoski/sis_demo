<template>
  <div class="wager-fields">
    <div class="wager-field">
      <input
        type="text"
        id="wager"
        name="wager"
        :value="wager"
        @input="$emit('handleWagerUpdate', $event.target.value)"
        @blur="$emit('handleWagerBlur')"
        placeholder="$0.00"
      />
      <label for="wager">WAGER</label>
    </div>
    <div class="wager-field">
      <input type="text" disabled id="payout" name="payout" :value="payout" />
      <label for="wager">PAYOUT</label>
    </div>
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
.wager-fields {
  display: flex;
  margin: 10px;
  justify-content: space-around;
  padding: 20px 0 20px;
  border-top: 1px solid rgba(24, 24, 41, 0.2);
}

.wager-field {
  position: relative;
  display: flex;
  width: 42%;
}

input {
  text-align: center;
  width: 100%;
  height: 38px;
  background-color: #f5f5f5;
  outline-color: rgb(233, 233, 233);
  font-size: 16px;
  border-radius: 5px;
  padding-bottom: 10px;
  border: 1px solid #dcdcdc;
}

input:focus {
  outline-color: #01ebff;
}

label {
  position: absolute;
  bottom: 8px;
  font-size: 10px;
  left: 55px;
}
</style>
