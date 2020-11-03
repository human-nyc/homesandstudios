<template>
  <div class="wrapper">
    <Header />
    <div class="container">
      <div class="posts">
        <PostListItem
          v-for="(postItem, index) in posts"
          :key="postItem._id"
          class="postItem"
          :index="index"
          :post="postItem"
        />
      </div>
      <div class="content">
        <h4>
          {{ home ? home.title : 'no home found :(' }}
        </h4>
        <BlockContent v-if="home.body" :blocks="home.body" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import sanityClient from '@sanity/client'
import BlockContent from 'sanity-blocks-vue-component'

const client = sanityClient({
  projectId: 'zyy4ftd8',
  dataset: 'production',
  // useCdn: true,
})

const query = `
  {
    "posts": *[_type == "post"]{
      "id": _id,
      "title": title,
      "body": body,
      "slug": slug.current,
      "mainImage": mainImage.asset->url,
      "publishedAt": publishedAt
    } | order(publishedAt desc),
    "pages": *[_type == "page"]{
      "id": _id,
      "title": title,
      "body": body,
      "mainImage": mainImage.asset->url,
      "slug": slug.current,
      "publishedAt": publishedAt
    },
    "home": *[_type == "page" && slug.current == "home"][0]{
      "id": _id,
      "title": title,
      "body": body,
      "mainImage": mainImage.asset->url,
      "slug": slug.current,
      "publishedAt": publishedAt
    }
  }
`
export default {
  components: {
    BlockContent,
  },
  async asyncData({ route, params }) {
    const data = await client.fetch(query)
    return {
      pages: data.pages,
      posts: data.posts,
      home: data.home,
      test: 'test',
    }
  },
  data() {
    return {
      pages: [],
      posts: [],
      home: {},
    }
  },
}
</script>

<style lang="scss">
@import '~/styles/style.scss';
</style>

<style lang="scss" scoped>
.content {
  padding: var(--gutter);
}
</style>
