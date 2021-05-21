<template>
  <div class="page">
    <header class="page__header"></header>
    <article class="page__main">
      <h1 class="title--is-1">{{ post.title }}</h1>
      <nuxt-content :document="post" class="content" />
    </article>
  </div>
</template>

<script>
export default {
  layout: 'post',
  async asyncData ({ $content, params }) {
    const post = await $content('posts', params.slug).fetch();
    return { post }
  },
  head() {
    return {
      title: this.post.title
    }
  }
}
</script>
<style>
@import '../static/css/_content.css';
@import '../static/css/_typography.css';
</style>
