<template>
  <header class="site-header">
    <div class="logo">
      <h1><a href="/">Dorna Lakayan</a></h1>
      <span>Interior architect &amp; designer</span>
    </div>
    <div class="contact">
      <span>Available for projects</span>
      <span><a href="mailto:hi@dorna.no" target="_blank">hi@dorna.no</a></span>
    </div>
  </header>
</template>

<style lang="scss" scoped>
@import '@/assets/css/variables.scss';
.site-header {
  width: 100%;
  padding: 2rem;
  line-height: 1.3;
  display: flex;
  justify-content: space-between;
  align-items: center;
  span {
    display: block;
  }
}
.logo {
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
.contact {
  text-align: right;

  a {
    text-decoration: none;
  }
}
</style>
