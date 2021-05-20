<template>
  <article>
    <h1>{{ post.title }}</h1>
    <nuxt-content :document="post" />
  </article>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const post = await $content('posts', params.slug).fetch()
    return {
      post
    }
  },
  head() {
    return {
      title: this.post.title
    }
  }
}
</script>
