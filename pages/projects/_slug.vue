<template>
  <main class="project-page">
    <img class="project-image" :src="project.mainImage[0].url" />
    <h1>{{ project.title }}</h1>
    <p class="project-text">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
    </p>
  </main>
</template>

<script>
import gql from 'graphql-tag'
export default {
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
            mainImage {
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
.project-page {
  padding: 0 2rem 10rem;
}
.project-image {
  margin-bottom: 2rem;
}
.project-text {
  width: 50%;
}
@media (max-width: $media-s) {
  .project-text {
    width: 100%;
  }
}
</style>

