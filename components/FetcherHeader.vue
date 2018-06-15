<template>
  <header class="row" :class="bgColor">
      <div class="col"><h1 class="text-title">{{title}}</h1></div>
      <nuxt-link :to="uriPath" class="back-btn">
        <span>Back</span>
      </nuxt-link>
    </header>
</template>

<script>
export default {
  props: {
    title: String,
    uriPath: String,
    bgColor: String,
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';

header.row {
  height: 90px;
  padding: 0;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: center;
}

.row {
  lost-flex-container: row;
}

.col {
  lost-flex-container: column;
}

.text {
  &-title {
    font-size: 2.5rem;
    color: white;
    padding: 1rem;
  }
}

.bg {
  &-blue {
    background-color: $color-blue;
  }

  &-red {
    background-color: lighten($color-red, 10);
  }
}

.back-btn {
  width: 100px;
  height: 100%;
  font-size: 1rem;
  color: white;
  background-color: tomato;
  border: none;
  text-decoration: none;
  lost-align: middle-center;
  &:hover {
    background-color: darken(tomato, 10);
  }
}
</style>

