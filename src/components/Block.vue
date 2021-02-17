<template>
  <div
    class="block">
    <div
        v-bind:style="sumbitWrapperPosition"
        class="block__inner"
    >
        {{ blockOffsetWidth }}
        {{ blockClientWidth }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Block',
  data () {
    return {
      blockOffsetWidth: 0,
      blockClientWidth: 0
    }
  },
  created () {
    window.addEventListener('resize', this.handleResize)
    this.handleResize()
  },
  destroyed () {
    window.removeEventListener('resize', this.handleResize)
  },
  computed: {
    sumbitWrapperPosition () {
      return { right: this.blockOffsetWidth - this.blockClientWidth + 'px' }
    }
  },
  methods: {
    handleResize (event) {
    //   console.log(event)
      const drawer = document.querySelector('.block')
      this.blockOffsetWidth = drawer.offsetWidth
      this.blockClientWidth = drawer.clientWidth
    }
  }
}
</script>

<style scoped lang="scss">
.block {
    position: relative;
    width: 350px;
    height: 350px;
    background: #000;
    overflow-y: scroll;

    &__inner {
        position: absolute;
        bottom: 0;
        width: 300px;
        height: 700px;
        background: #ccc;
    }
}
</style>
