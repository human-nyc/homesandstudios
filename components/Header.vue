<template>
  <div class="header">
    <nuxt-link to="/" class="logo">
      Social Studies
    </nuxt-link>

    <nuxt-link to="conversations" class="link">
      Conversations
    </nuxt-link>

    <nuxt-link to="library" class="link">
      Library
    </nuxt-link>

    <nuxt-link to="gallery" class="link">
      Gallery
    </nuxt-link>

    <nuxt-link to="resources" class="link">
      Resources
    </nuxt-link>

    <nuxt-link to="shop" class="link">
      Shop
    </nuxt-link>
  </div>
</template>

<script>

export default {
}
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
