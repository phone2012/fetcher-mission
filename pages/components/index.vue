<template>
  <article class="container-page">
    <div class="container">
      <fetcher-header
        title="Timmmmmmmmmerrrrr"
        uri-path="/"
        bg-color="bg-blue"
      ></fetcher-header>
      <main>
        <div class="row">
          <div class="search-result">
            <button
              class="submit-btn"
              @click.prevent="showMe"
            >
              TOUCH ME !
            </button>
          </div>
        </div>
        <foo-appear
          :show="show_toggle"
          :delay="current_delay"
        ></foo-appear>
      </main>
    </div>
  </article>
</template>

<script>
import FetcherHeader from '@/components/FetcherHeader'
import FooAppear from '@/components/FooAppear'

export default {
  components: {
    FetcherHeader,
    FooAppear
  },
  data () {
    return {
      loading: false,
      show_toggle: false,
      current_delay: 0,
      max_delay: 10 // sec
    }
  },
  methods: {
    showMe () {
      this.show_toggle = true
      this.current_delay = this.max_delay
      this.timer = setInterval(() => {
        if (this.current_delay === 1) {
          this.show_toggle = false
          clearInterval(this.timer)
        }
        this.current_delay -= 1
      }, 1000)
    }
  }
}
</script>


<style lang="scss" scoped>
@import '@/assets/scss/_variables.scss';
@import '@/assets/scss/_flex.scss';

header,
main {
  padding: 1rem;
}

button {
  &.submit-btn {
    width: 150px;
    height: 60px;
    color: white;
    font-size: 1.25rem;
    background-color: $color-green;
    border: 5px solid darken($color-green, 10);
  }
}

.container {
  width: 100%;
  height: 100%;
  max-width: 990px;
}

.row {
  lost-flex-container: row;
}

.col {
  lost-flex-container: column;
}

.text {
  &-result {
    font-size: 1.25rem;
    color: $color-dark-grey;
  }
}
</style>

