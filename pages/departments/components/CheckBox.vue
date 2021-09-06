<template>
  <div>
    <input id="chk1" type="checkbox" />
    <label for="chk1"><span></span></label>
  </div>
</template>

<script>
export default {
  computed: {},
}
</script>

<style lang="scss" scoped>
input {
  position: absolute;
  left: -1000%;
}

label {
  display: block;
  position: relative;
  width: 40px;
  height: 20px;
  background: salmon;
  border-radius: 80px;
  transition: background 0.4s;
  z-index: 0;
}

span {
  display: none;
}

label:after {
  content: '';
  position: absolute;
  left: 4px;
  top: 50%;
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: white;
  transform: translateY(-50%);
  box-shadow: 1px 3px 4px rgba(0, 0, 0, 0.2);
  transition: all 0.6s;
  z-index: 0;
}

input:checked + label {
  background: sandybrown;
}

input:checked + label:after {
  left: calc(100% - 19px);
}

label span {
  display: none;
}
</style>
