<template>
  <div v-if="index == postIndex">
    <h2>{{ post.title }}</h2>
    <p v-if="post.publishedAt" class="dateTime">
      {{ time(post.publishedAt) }}
    </p>
  </div>
  <div v-else>
    <nuxt-link :id="post.slug" :to="'/posts/' + post.slug">
      <h2>{{ post.title }}</h2>
      <p v-if="post.publishedAt" class="dateTime">
        {{ time(post.publishedAt) }}
      </p>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      default: () => {},
    },
    index: {
      type: Number,
      default: 0,
    },
    postIndex: {
      type: Number,
      default: 0,
    },
    isActive: Boolean,
  },
  methods: {
    time(publishedAt) {
      this.publishedAt = publishedAt
      return (
        publishedAt.split('T')[0] +
        ' ' +
        publishedAt.split('T')[1].replace('Z', '')
      )
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
