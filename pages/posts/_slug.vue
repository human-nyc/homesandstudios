<template>
  <div class="wrapper">
    <Header />
    <div class="container">
      <h1 class="title">{{ post.title }}</h1>
      <div class="post-body">
        <BlockContent v-if="post.body" :blocks="post.body" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import BlockContent from 'sanity-blocks-vue-component'
import sanityClient from '@sanity/client'

const client = sanityClient({
  projectId: 'zyy4ftd8',
  dataset: 'production',
  useCdn: true,
})

const query = `
  {
    "posts": *[_type == "post"]{
      "id": _id,
      "title": title,
      "location": location,
      "body": body,
      "slug": slug.current,
      "mainImage": mainImage.asset->url,
      "publishedAt": publishedAt
    } | order(publishedAt desc)
  }
`
export default {
  components: {
    BlockContent,
  },
  async asyncData({ route, params }) {
    const data = await client.fetch(query)
    const postIndex = params.slug
      ? data.posts
          .map((post, i) => (post.slug === params.slug ? i : null))
          .filter((el) => el != null)[0]
      : -1

    return {
      posts: data.posts,
      post: data.posts[postIndex],
      postIndex,
    }
  },
  data() {
    return {
      posts: [],
      post: '',
      postIndex: 0,
    }
  },
}
</script>

<style lang="scss">
@import '~/styles/style.scss';
</style>

<style lang="scss" scoped>
.title {
  background: red;
}
</style>
