<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<style lang="scss">
.container {
  margin: 0px 0px 0px calc(max((100vw - 1200px) / 2, 0px));
}
</style>
