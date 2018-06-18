<template lang="html">
  <div class="container">
    <p>{{ count1 }}</p>
  </div>
</template>

<script>
export default {
  props: {
    count1: {
      type: String,
    }
  }
}
</script>

<style scoped>
  .container {
    position        : fixed;
    lost-center     : 550px;
    lost-align      : middle-center;
    width           : 400px;
    height          : 200px;
    background-color: red;
  }
</style>
