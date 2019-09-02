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
  data: function() {
    return {
      blocks: [
        {
          heading: 'Currently',
          text: 'Dorna is currently working at <a href="http://www.metropolis.no/">Metropolis</a>, one of Norway\'s leading studios for interior architecture. She is engaged in a diverse range of projects for both private and commercial clients. She also works as a technical specialist in dForm, the digital workshop at <a href="https://khio.no">Oslo National Academy of the Arts</a>, where she assists students in the use of the various workshop facilities including laser printing/cutting, 3D scanning and printing, and VR. In addition, she occasionally works as an assistant for Norwegian artist Inghild Karlsen.'
        },
        {
          heading: 'Previously',
          text: '<ul><li>Here Dorna you can fill out some previous work experience.</li><li>I\'m not sure what you would like to have in here.</li><li>Maybe not everything from your CV.</li><li>Just the relevant stuff right?</li><li>Maybe not even in list form.</li><li>I have your CV but I didn\t want to presume anything.</li><li>You\'re awesome.</li><li>Good luck!</li></ul>'
        },
        {
          heading: 'Education',
          text: '<ul><li>Oslo National Academy of the Arts (KHiO), 2014&mdash;2016<br />Master in design with a specialization in interior architecture and furniture design</li><li>Limkokwing University of Creative Technology (LUCT), 2011&mdash;2012<br />Bachelor in interior architecture</li><li>University of Ershad, 2005&mdash;2009<br />Bachelor in English literature</li></ul>'
        },
        {
          heading: 'Technical skills',
          text: '<ul><li>AutoCAD 2D/3D</li><li>ArchiCAD</li><li>Autodesk 3ds Max</li><li>Laser cutting</li><li>3D printing</li><li>Adobe Photoshop</li><li>Adobe Illustrator</li><li>Adobe InDesign</li></ul>'
        },
        {
          heading: 'Exhibitions',
          text: '<ul><li><a href="http://2016.designavgang.no/IM/dorna-lakayan">Designavgang</a><br />June 2016 &ndash; Oslo, Norway</li><li>Frekvens<br />June 2015 &ndash; Oslo, Norway</li><li>Designer\'s Saturday<br />Sep 2015 &ndash; Oslo, Norway</li></ul>'
        },
        {
          heading: 'Background',
          text: 'Dorna grew up in Tehran, Iran. She has since lived in Kuala Lumpur, Malaysia, and currently resides in Oslo, Norway. She speaks English, Farsi, Turkish, and Norwegian. She loves ice cream, beach runs, Dior lipstick, peculiar houseplants, and collecting unique design items.'
        }
      ]
    }
  },
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
