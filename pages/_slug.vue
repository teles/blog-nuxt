<template>
  <article class="page__article">
    <section class="page__article__image-box">
      <h1 class="page__article__title">{{ post.title }}</h1>
      <img :src="post.image.src" class="page__article__image-box__image" />
    </section>
    <section class="page__article__content">
      <NuxtContent :document="post" class="content" />
    </section>
  </article>
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

.page__article__image-box {
  display: flex;
  flex-direction: column;
  padding: 0 var(--spacing-2);
  background: linear-gradient(to bottom, var(--color-dark) 80%, transparent 80%);
  margin: 0;
  align-items: center;
}

.page__article__image-box__image {
  width: 100%;
  border: 1px solid #fff;
  max-height: 60vh;
  min-height: 300px;
  object-fit: cover;
  max-width: 1280px;
  margin: 0 auto;
  border-radius: 8px;
}

.page__article__title {
  font-size: 2.2em;
  color: #fff;
  max-width: 1280px;
  width: 100%;
  margin: var(--spacing-1) 0 var(--spacing-2);
}

.page__article__content {
  width: 100%;
  padding: var(--spacing-2);
  max-width: 1280px;
  margin: 0 auto;
  box-sizing: border-box;
}

</style>
