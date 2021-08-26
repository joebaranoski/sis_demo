<template>
  <BetslipContainer
    @click="highlightButtons"
    :buttonsHighlighted="buttonsHighlighted"
  />
</template>

<script>
import { ref } from 'vue';
import BetslipContainer from './components/BetslipContainer.vue';

export default {
  name: 'App',
  components: {
    BetslipContainer,
  },
  setup() {
    const buttonsHighlighted = ref(false);

    const highlightButtons = () => {
      buttonsHighlighted.value = true;

      setTimeout(() => {
        buttonsHighlighted.value = false;
      }, 350);
    };

    /** Highlight interactable components on app mount */
    setTimeout(() => {
      highlightButtons();
    }, 500);

    return {
      buttonsHighlighted,
      highlightButtons,
    };
  },
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
}

#app {
  background-color: black;
  min-height: 100%;
  height: 100%;
  width: 100%;
  min-width: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
}

.button {
  font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';
  font-size: 12px;
}
</style>
