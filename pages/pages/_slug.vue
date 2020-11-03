<template>
  <div class="wrapper">
    <Header />
    <div class="container">
      <h1 class="title">Page: {page.title}</h1>
      <div class="page-body">
        <BlockContent v-if="page.body" :blocks="page.body" />
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
    "pages": *[_type == "page"]{
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
    const pageIndex = params.slug
      ? data.pages
          .map((page, i) => (page.slug === params.slug ? i : null))
          .filter((el) => el != null)[0]
      : -1

    return {
      pages: data.pages,
      page: data.pages[pageIndex],
      pageIndex,
    }
  },
  data() {
    return {
      pages: [],
      page: '',
      pageIndex: 0,
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
