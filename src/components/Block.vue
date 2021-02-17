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
      drawerScroll: {
        offsetWidth: 0,
        clientWidth: 0
      }
    }
  },
  created () {
    window.addEventListener('resize', this.submitWrapperHandler)
    this.submitWrapperHandler()
  },
  destroyed () {
    window.removeEventListener('resize', this.submitWrapperHandler)
  },
  computed: {
    sumbitWrapperPosition () {
      return { right: this.drawerScroll.offsetWidth - this.drawerScroll.clientWidth + 'px' }
    }
  },
  methods: {
    submitWrapperHandler () {
      const drawer = document.querySelector('.block')
      this.drawerScroll.offsetWidth = drawer.offsetWidth
      this.drawerScroll.clientWidth = drawer.clientWidth
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
        height: 80px;
        background: #ccc;
    }
}
</style>
