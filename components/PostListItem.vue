<template>
  <nuxt-link :id="post.slug" :to="'/posts/' + post.slug">
    <h2>{{ post.title }}</h2>
    <h4>{{ post.location }}</h4>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style lang="scss" scoped>
.postItem {
  border-bottom: 1px solid;
  display: block;
  overflow: hidden;
  padding: var(--gutter);

  &:last-child {
    border-bottom: none;
  }
  &.current {
    background-color: red;
    color: white;
  }
  h2 {
    margin: 0;
  }
}
</style>
