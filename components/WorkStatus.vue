<template>
  <div>
    <p class="status" :style="{ backgroundColor: color }">
      <slot></slot>
    </p>
  </div>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      default: '#8B98A7',
    },
  },
}
</script>

<style lang="scss" scoped>
.status {
  padding: 5px 9px 3px 9px;
  border-radius: 999px;
  color: #fff;
  background-color: rgb(139, 152, 167);
  font-size: 12px;
  font-weight: 400;
}
</style>
