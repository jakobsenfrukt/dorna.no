<template>
  <main class="site-main">
    <section class="project-page">
      <img class="project-image" :src="project.mainImage[0].url" />
      <div class="project-content">
        <div class="project-header">
          <h1 class="project-title">{{ project.title }}</h1>
          <span>{{ project.year }}</span>
        </div>
        <div class="project-text">
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
          </p>
        </div>
      </div>
      <div class="project-gallery">
        <div v-for="(image, index) in project.gallery" :key="index" class="project-image" :style="{ animationDelay: index/3 + 's' }">
          <img :src="image.url" />
        </div>
      </div>
    </section>
    <Gallery />
  </main>
</template>

<script>
import Gallery from '~/components/Gallery.vue'
import gql from 'graphql-tag'
export default {
  components: {
    Gallery
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
  },
  apollo: {
    project: {
      variables() {
        return { slug: this.$route.params.slug }
      },
      query: gql`
      query Project($slug: String!) {
        project: entry(slug: $slug) {
          ... on Projects {
            title
            year
            mainImage {
              url
            }
            gallery {
              url
            }
          }
        }
      }`
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/css/variables.scss';
.site-main {
  padding-bottom: 10rem;
}
.project-page {
  padding: 2rem 2rem 10rem;
}
.project-image {
  margin-bottom: 2rem;
  opacity: 0;
  animation: fade-in 1s ease-in;
  animation-fill-mode: forwards;
}
.project-content {
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 2rem;
}
.project-header, .project-text {
  width: 50%;
}
@media (max-width: $media-s) {
  .project-header, .project-text {
    width: 100%;
  }
  .project-header {
    margin-bottom: 1rem;
  }
}
@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>

