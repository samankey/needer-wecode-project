<template>
  <div class="emptyList">
    <div class="image"><slot name="image" /></div>
    <div class="desc"><slot name="desc" /></div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.emptyList {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 44px 32px 36px;
  background-color: #fff;
  border-radius: 12px;

  .image {
    margin-bottom: 24px;
  }

  .desc {
    font-size: 14px;
    color: rgb(177, 177, 177);
  }
}
</style>
