<template>
  <div class="about">
    <h2 class="about-block">CV</h2>
    <div class="about-block double">
      <p>
        {{ about.body }}
      </p>
    </div>
    <div v-for="(block, index) in about.textBlocks" :key="index" class="about-block">
      <h3>{{ block.heading }}</h3>
      <div v-html="block.body.content"></div>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  apollo: {
    about: {
      variables() {
        return { slug: this.$route.params.slug }
      },
      query: gql`
      query {
      about: entry(title: "About") {
        ... on About {
          body
          textBlocks {
            ... on TextBlocksTextBlock {
              heading
              body {
                content
              }
            }
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
.about {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  padding: 5rem 1rem 0;

  h2, h3 {
    font-weight: inherit;
    margin-bottom: 1rem;
  }

  &-block {
    width: calc(33.3333333333% - 2rem);
    margin: 1rem 1rem 2rem;
    padding-right: 2rem;

    &.double {
      width: calc(66.6666666666% - 2rem);
      margin-bottom: 5rem;
    }
  }

  @media (max-width: $media-m) {
    &-block {
      width: calc(50% - 2rem);

      &.double {
        width: 100%;
      }
    }
  }
  @media (max-width: $media-s) {
    &-block {
      width: 100%;
      &.double {
        width: 100%;
        margin-bottom: 2rem;
      }
    }
  }
}
</style>
