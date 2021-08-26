<template>
  <div class="pick-count">
    <svg
      class="pick-icon"
      xmlns="http://www.w3.org/2000/svg"
      focusable="false"
      viewBox="0 0 24 24"
      color='var(--token-a1d62134-0548-46f8-b38d-47558d3ef3e7, rgb(17, 153, 238)) /* {\"name\":\"$chart-1\"} */'
      style="fill: var(--token-a1d62134-0548-46f8-b38d-47558d3ef3e7, rgb(17, 153, 238)) ; flex-shrink: 0;"
    >
      <path d="M1 21h22L12 2 1 21zm12-3h-2v-2h2v2zm0-4h-2v-4h2v4z"></path>
    </svg>
    <span>1 PICK</span>
  </div>
</template>

<script>
export default {
  name: 'PickCount',
};
</script>

<style scoped>
.pick-count {
  background: white;
  width: 165px;
  height: 100%;
  border: 1px #e9e9eb solid;
  box-shadow: 0px 0px 2px #e9e9eb;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';
}

.pick-icon {
  width: 25px;
  margin-right: 5px;
}
</style>
