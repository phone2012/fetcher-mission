<template>
  <div class="full-page" v-if="show">
    <div class="container">
      <h1 class="text-title">I WILL CLOSE MY SELF IN {{delay}}</h1>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: Boolean,
    delay: Number
  }
}
</script>


<style lang="scss" scoped>
.full-page {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(tomato, 0.5);
  z-index: 9999;
}

.container {
  lost-center: 550px;
  lost-align: middle-center;
  height: 300px;
  background-color: white;
}

.text-title {
  font-size: 1.25rem;
  color: darkgray;
}
</style>
