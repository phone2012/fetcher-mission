<template lang="html">
  <div class="container">
    <p>{{ count }}</p>
  </div>
</template>

<script>
export default {
  props: {
    count: {
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
    background-color: green;
  }
</style>
