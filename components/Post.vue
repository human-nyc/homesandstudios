<template>
  <div>
    <div v-if="post.mainImage" class="post-image">
      <img :src="post.mainImage + '?w=500'" class="cover" />
    </div>

    <div class="post-header">
      <h2>{{ post.title }}</h2>
      <p v-if="post.publishedAt" class="dateTime">
        {{ time(post.publishedAt) }}
      </p>
    </div>

    <div class="post-body">
      <BlockContent v-if="post.body" :blocks="post.body" />
    </div>
  </div>
</template>

<script>
import BlockContent from 'sanity-blocks-vue-component'

export default {
  components: {
    BlockContent,
  },
  props: {
    post: {
      type: Object,
      default: () => {},
    },
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
.post {
  max-width: 600px;
  padding: var(--gutter);
  position: sticky;
  top: 0;

  @media (min-width: 1024px) {
    padding: calc(var(--gutter) * 4);
  }

  &-image {
    background: #888;
    border: 1px solid;

    @media (min-width: 768px) {
      width: 300px;
      height: 300px;
    }
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  &-header,
  &-body {
    display: block;
    margin: var(--gutter) 0;
  }
  &-body {
    text-transform: initial;
    p {
      margin: var(--gutter) 0;
    }
    a {
      display: inline-block;

      &::after {
        content: '';
        display: block;
        margin-top: -1px;
        border-bottom: 1px solid blue;
      }
      &:hover {
        color: blue;
      }
    }
  }
}
</style>
