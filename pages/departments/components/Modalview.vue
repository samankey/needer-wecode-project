<template>
  <div class="modal">
    <div class="overlay" @click="$emit('close-modal')"></div>
    <div class="modal-card"><slot /></div>
  </div>
</template>
<script>
export default {}
</script>
<style>
/* Modal */
.modal,
.overlay {
  width: 100%;
  height: 100%;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 10;
}
.overlay {
  opacity: 0.5;
  background-color: black;
  z-index: 10;
}
.modal-card {
  position: relative;
  max-width: 1200px;
  margin: auto;
  margin-top: 30px;
  padding: 20px;
  background-color: white;
  min-height: 500px;
  opacity: 1;
  z-index: 10;
}
</style>
