<template>
  <div class="about">
    <h2 class="about-block">CV</h2>
    <div class="about-block double">
      <p>It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages.</p>
    </div>
    <div v-for="(block, index) in blocks" :key="index" class="about-block">
      <h3>{{ block.heading }}</h3>
      <p v-html="block.text"></p>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      blocks: [
        {
          heading: 'CV Section',
          text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.'
        },
        {
          heading: 'CV Section',
          text: '<ul><li>Lorem Ipsum is simply dummy text of the printing and typesetting industry.</li><li>Lorem Ipsum is simply dummy text.</li><li>Dummy text of the printing and typesetting industry.</li><li>Lorem Ipsum is simply dummy text of the printing and typesetting industry.</li><li>Lorem Ipsum is simply dummy text.</li><li>Dummy text of the printing and typesetting industry.</li></ul>'
        },
        {
          heading: 'CV Section',
          text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages.'
        },
        {
          heading: 'CV Section',
          text: 'When an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.'
        }
      ]
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
  }

  &-block {
    width: calc(33.3333333333% - 2rem);
    margin: 1rem;
    padding-right: 2rem;

    &.double {
      width: calc(66.6666666666% - 2rem);
      margin-bottom: 5rem;
    }
  }

  @media (max-width: $media-m) {
    &-block {
      width: calc(50% - 2rem);
    }
  }
  @media (max-width: $media-s) {
    &-block {
      width: 100%;
    }
  }
}
</style>
