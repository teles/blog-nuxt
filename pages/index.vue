<template>
  <div class="page">
    <header class="page__header"></header>
    <main class="page__main">
      <post-box :post="post" v-for="post of posts" :key="post.slug"></post-box>
    </main>
  </div>
</template>

<script>
import PostBox from '../components/PostBox';

export default {
  components: {
    PostBox,
  },
  async asyncData({ $content }) {
    const posts = await $content('posts')
      .only(['title', 'description', 'image', 'slug', 'published'])
      .where({published: true})
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      posts
    }
  }
}
</script>
