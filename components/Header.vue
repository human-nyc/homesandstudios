<template>
  <div class="header">
    <nuxt-link to="/" class="logo">Homes + Studios</nuxt-link>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.header {
  align-items: center;
  background-color: #fcf951;
  border-bottom: 1px solid;
  color: black;
  display: flex;
  padding: var(--gutter);
  text-transform: uppercase;
  justify-content: center;

  @media (min-width: 1024px) {
    font-size: 26px;
  }
}
</style>
