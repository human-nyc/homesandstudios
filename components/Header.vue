<template>
  <div class="header">
    <nuxt-link to="/" class="logo">Homes and studios</nuxt-link>
    <nuxt-link to="page" class="link">Page</nuxt-link>
    <nuxt-link to="page" class="link">Page</nuxt-link>
    <nuxt-link to="page" class="link">Page</nuxt-link>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.header {
  padding: var(--gutter);
  border-bottom: 1px solid;
  text-transform: uppercase;
  display: flex;
  justify-content: space-between;

  // @media (min-width: 1024px) {

  // }

  .logo {
    margin-right: 1em;
  }
  .link {
    margin-right: 1em;
  }
}
</style>
