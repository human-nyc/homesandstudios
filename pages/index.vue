<template>
  <div class="wrapper">
    <Header />
    <div class="container">
      <h1 class="title">Homepage</h1>
      <div class="post-wrapper">
        <!-- <Post :post="post" class="post" /> -->
      </div>
      <div class="posts">
        <!-- <PostListItem
          v-for="(postItem, index) in posts"
          :key="postItem._id"
          :class="['post-item', { current: index == postIndex }]"
          :index="index"
          :post="postItem"
          :post-index="postIndex"
        /> -->
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
// import sanityClient from '@sanity/client'
import Header from "~/components/Header.vue";
import Footer from "~/components/Footer.vue";

// const client = sanityClient({
//   projectId: 'v4q6145o',
//   dataset: 'production',
//   useCdn: true
// })

// const query = `
//   {
//     "posts": *[_type == "post"]{
//       "id": _id,
//       "title": title,
//       "body": body,
//       "slug": slug.current,
//       "header": header,
//       "mainImage": mainImage.asset->url,
//       "trackId": trackId,
//       "trackUrl": trackUrl,
//       "publishedAt": publishedAt
//     } | order(publishedAt desc),
//     "about": *[_type == "page" && slug.current == "about"][0]{
//       "id": _id,
//       "title": title,
//       "body": body,
//       "mainImage": mainImage.asset->url,
//       "slug": slug.current,
//       "publishedAt": publishedAt
//     }
//   }
// `
export default {
  components: {
    Header,
    Footer,
    // PostListItem,
    // Post,
  },
  // async asyncData ({ route, params }) {
  //   const data = await client.fetch(query)
  //   const postIndex = params.slug
  //     ? data.posts
  //       .map((post, i) => (post.slug === params.slug ? i : null))
  //       .filter(el => el != null)[0]
  //     : -1

  //   return {
  //     posts: data.posts,
  //     post: postIndex === -1 ? data.about : data.posts[postIndex],
  //     postIndex
  //   }
  // },
  // data () {
  //   return {
  //     posts: [],
  //     post: '',
  //     postIndex: 0
  //   }
  // }
};
</script>

<style lang="scss">
@import "~/styles/style.scss";
</style>

<style lang="scss" scoped>
.title {
  // background: red;
}
</style>
