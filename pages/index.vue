<template>
  <main class="site-main">
    <div>
      <Gallery />
      <CV />
    </div>
  </main>
</template>

<script>
import Gallery from '~/components/Gallery.vue'
import CV from '~/components/CV.vue'

export default {
  components: {
    Gallery,
    CV
  },
  head () {
    return {
      title: 'Dorna',
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { 
          hid: 'description', 
          name: 'description', 
          content: 'Dorna Lakayan is an interior architect and designer based in Oslo, Norway.' 
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.site-main {
  padding-bottom: 10rem;
}
</style>

