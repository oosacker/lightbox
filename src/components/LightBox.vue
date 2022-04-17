<template>
  <div>
    <button @click="showSingle">Show single picture.</button>
    <button @click="showMultiple">Show a group of pictures.</button>

    <!-- all props & events -->
    <vue-easy-lightbox
      escDisabled
      moveDisabled
      :visible="visible"
      :imgs="imgs"
      :index="index"
      @hide="handleHide"
    >
      <!-- v-slot in vue@2.6.0+ -->
      <template v-slot:prev-btn="{ prev }">
        <button @click="prev">show the prev</button>
      </template>

      <template v-slot:next-btn="{ next }">
        <button @click="next">show the next</button>
      </template>

      <template v-slot:close-btn="{ close }">
        <button @click="close">close lightbox</button>
      </template>

      <template v-slot:toolbar="{ toolbarMethods }">
        <button @click="toolbarMethods.zoomIn">zoom in</button>
        <button @click="toolbarMethods.zoomOut">zoom out</button>
        <button @click="toolbarMethods.rotateLeft">Anticlockwise rotation</button>
        <button @click="toolbarMethods.rotateRight">clockwise rotation</button>
      </template>
    </vue-easy-lightbox>
  </div>
</template>

<script>
import VueEasyLightbox from 'vue-easy-lightbox'
export default {
  name: 'LightBox',
  components: {
    VueEasyLightbox
  },
  data() {
    return {
      imgs: '',  // Img Url , string or Array of string
      visible: false,
      index: 0   // default: 0
    }
  },
  methods: {
    showSingle() {
      this.imgs = 'http://via.placeholder.com/350x150'
      // or
      this.imgs = { title: 'this is a placeholder', src: 'http://via.placeholder.com/350x150' }
      this.show()
    },
    showMultiple() {
      this.imgs = ['http://via.placeholder.com/350x150', 'http://via.placeholder.com/350x150']
      // or
      this.imgs = [
        { title: 'test img', src: 'http://via.placeholder.com/350x150' },
        'http://via.placeholder.com/350x150'
      ]
      // allow mixing

      this.index = 1  // index of imgList
      this.show()
    },
    show() {
      this.visible = true
    },
    handleHide() {
      this.visible = false
    }
  }
}
</script>

<style scoped>
</style>
