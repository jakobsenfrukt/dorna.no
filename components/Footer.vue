<template>
  <footer class="site-footer">
    <div class="email">
      <span>Email</span>
      <span><a href="mailto:drnlkn@gmail.com" target="_blank">drnlkn@gmail.com</a></span>
    </div>
    <div class="social">
      <span>Instagram</span>
      <span><a href="https://instagram.com/doornow" target="_blank">@doornow</a></span>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
@import '@/assets/css/variables.scss';
.site-footer {
  width: 100%;
  padding: 2rem;
  line-height: 1.3;
  display: flex;
  justify-content: space-between;
  align-items: center;
  span {
    display: block;
  }
  a {
    text-decoration: none;
  }
}
.email {
  text-align: left;

  h1 {
    font-size: 1rem;
    margin: 0 auto;
    font-weight: inherit;

    a {
      text-decoration: none;
    }
  }
}
.social {
  text-align: right;

  a {
    text-decoration: none;
  }
}
</style>
