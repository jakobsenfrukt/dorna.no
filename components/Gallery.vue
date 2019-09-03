<template>
  <div class="gallery">
    <a v-for="(project, index) in projects" :key="index" :href="`/projects/${project.slug}`" class="gallery-item" :style="{ animationDelay: index/3 + 's' }">
      <img :src="project.mainImage[0].thumbnail" />
      <div class="text">
        <span>{{ project.title }}</span>
        <span v-if="project.year">{{ project.year }}</span>
      </div>
    </a>
    <!--<div class="more">
      <a href="#">&rarr; View more projects</a>
    </div>-->
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  apollo: {
    projects: gql`
    query {
      projects: entries(section:projects) {
    		... on Projects {
          title
          mainImage {
            thumbnail: url(transform: thumb)
          }
          slug
        }
      }
    }`
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/css/variables.scss';
.gallery {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  padding: 0 1rem;

  &-item {
    width: calc(33.3333333333% - 2rem);
    margin: 1rem;
    color: inherit;
    text-decoration: none;

    opacity: 0;
    animation: fade-in 1s ease-in;
    animation-fill-mode: forwards;

    span {
      display: block;
    }

    img {
      transition: all .2s linear;
      filter: grayscale(60%);
    }

    &:hover {
      img {
        filter: grayscale(0%);
      }
    }
  }

  @media (max-width: $media-m) {
    &-item {
      width: calc(50% - 2rem);
    }
  }
  @media (max-width: $media-s) {
    &-item {
      width: 100%;
    }
  }
}

.more {
  display: block;
  width: 100%;
  text-align: right;
  margin: 0 1rem 2.5rem;
  padding: 2.5rem 0 0.5rem;
  border-bottom: 1px solid $color-main;

  a {
    text-decoration: none;
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
