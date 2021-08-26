<template>
  <div class="detail-row">
    <span class="heading">{{ heading }}</span>
    <div class="content-group">
      <span class="content">{{ content }}</span>
      <span class="subcontent" v-if="subcontent">{{ subcontent }} </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailRox',
  props: {
    heading: String,
    content: String,
    subcontent: String,
  },
};
</script>

<style scoped>
.detail-row {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin: 15px;
  padding: 5px 0;
  border-bottom: 1px solid rgb(233, 233, 233);
}

.heading {
  color: rgba(24, 24, 41, 0.6);
  font-size: 14px;
}

.content {
  font-weight: 700;
}

.subcontent {
  font-size: 11px;
  font-weight: 700;
  color: rgba(24, 24, 41, 0.6);
}

.content-group {
  min-width: 60%;
  display: flex;
  align-items: flex-start;
  flex-direction: column;
}
</style>
