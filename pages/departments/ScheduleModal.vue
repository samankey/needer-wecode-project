<template>
  <div>
    <div class="modal">
      <div class="overlay" @click="$emit('close-modal')"></div>
      <div class="modal-card">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },

  created() {},

  methods: {},
}
</script>

<style lang="scss" scoped>
.modal,
.overlay {
  width: 100%;
  height: 100%;
  position: fixed;
  left: 0;
  top: 0;
}

.overlay {
  opacity: 0.05;
  background-color: #111;
}

.modal-card {
  position: relative;
  max-width: 40%;
  min-height: 500px;
  margin: auto;
  margin-top: 100px;
  padding: 40px;
  border-radius: 20px;
  background-color: #f3f5f6;
  z-index: 10;
  opacity: 1;
}
</style>
