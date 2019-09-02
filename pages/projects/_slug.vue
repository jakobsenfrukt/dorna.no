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
            {{ project.body }}
          </p>
          <ul class="project-meta">
            <li v-if="project.category"><strong>Category</strong><br />{{ project.category }}</li>
            <li v-if="project.client"><strong>Client</strong><br />{{ project.client }}</li>
            <li v-if="project.location"><strong>Location</strong><br />{{ project.location }}</li>
            <li v-if="project.notes">{{ project.notes }}</li>
          </ul>
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
            body
            category
            location
            client
            notes
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
  justify-content: space-between;
  margin-bottom: 2rem;
}
.project-header, .project-text {
  width: 49%;
}
.project-meta {
  font-size: 0.8rem;
  list-style: none;
  margin: 2rem 0 0;
  padding: 0;

  display: flex;
  flex-wrap: wrap;

  li {
    width: 50%;
    padding: 0 2rem .8rem 0;
  }
  strong {
    font-weight: normal;
  }
}
.project-gallery {
  display: flex;
  justify-content: space-between;

  .project-image {
    width: 49%;
  }
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

