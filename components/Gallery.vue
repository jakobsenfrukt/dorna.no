<template>
  <div class="gallery">
    <a v-for="(entry, index) in entries" :key="index" :href="entry.url" class="gallery-item" :style="{ animationDelay: index/3 + 's' }">
      <img :src="entry.mainImage.url" />
      <div class="text">
        <span>{{ entry.title }}</span>
        <span>{{ entry.year }}</span>
      </div>
    </a>
    <!--<div class="more">
      <a href="#">&rarr; View more projects</a>
    </div>-->
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      entries: [
        {
          mainImage: {
            url: 'https://instagram.fosl3-1.fna.fbcdn.net/vp/0af45072e6a6c9297a34ccfecd154016/5D821BC0/t51.2885-15/e35/32715589_2182456961795147_4601917093837799424_n.jpg?_nc_ht=instagram.fosl3-1.fna.fbcdn.net'
          },
          title: 'A space for opportunity',
          year: '2018',
          url: '#'
        },
        {
          mainImage: {
            url: 'https://instagram.fosl3-1.fna.fbcdn.net/vp/0af45072e6a6c9297a34ccfecd154016/5D821BC0/t51.2885-15/e35/32715589_2182456961795147_4601917093837799424_n.jpg?_nc_ht=instagram.fosl3-1.fna.fbcdn.net'
          },
          title: 'A space for opportunity',
          year: '2018',
          url: '#'
        },
        {
          mainImage: {
            url: 'https://instagram.fosl3-1.fna.fbcdn.net/vp/0af45072e6a6c9297a34ccfecd154016/5D821BC0/t51.2885-15/e35/32715589_2182456961795147_4601917093837799424_n.jpg?_nc_ht=instagram.fosl3-1.fna.fbcdn.net'
          },
          title: 'A space for opportunity',
          year: '2018',
          url: '#'
        },
        {
          mainImage: {
            url: 'https://instagram.fosl3-1.fna.fbcdn.net/vp/0af45072e6a6c9297a34ccfecd154016/5D821BC0/t51.2885-15/e35/32715589_2182456961795147_4601917093837799424_n.jpg?_nc_ht=instagram.fosl3-1.fna.fbcdn.net'
          },
          title: 'A space for opportunity',
          year: '2018',
          url: '#'
        },
        {
          mainImage: {
            url: 'https://instagram.fosl3-1.fna.fbcdn.net/vp/0af45072e6a6c9297a34ccfecd154016/5D821BC0/t51.2885-15/e35/32715589_2182456961795147_4601917093837799424_n.jpg?_nc_ht=instagram.fosl3-1.fna.fbcdn.net'
          },
          title: 'A space for opportunity',
          year: '2018',
          url: '#'
        },
        {
          mainImage: {
            url: 'https://instagram.fosl3-1.fna.fbcdn.net/vp/0af45072e6a6c9297a34ccfecd154016/5D821BC0/t51.2885-15/e35/32715589_2182456961795147_4601917093837799424_n.jpg?_nc_ht=instagram.fosl3-1.fna.fbcdn.net'
          },
          title: 'A space for opportunity',
          year: '2018',
          url: '#'
        }
      ]
    }
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
