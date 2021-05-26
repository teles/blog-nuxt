<template>
  <archive :posts="posts" />
</template>

<script>
import Archive from '../../components/Archive';

export default {
  components: {
    Archive
  },
  async asyncData ({ $content, params }) {
    const categories = await $content('categories')
      .only(['slug', 'title'])
      .fetch();

    const category = await $content('categories')
      .where({slug: params.slug})
      .only(['slug', 'title'])
      .fetch();

    const posts = await $content('posts')
      .only(['title', 'description', 'category', 'image', 'slug', 'published'])
      .where({published: true, category: params.slug})
      .sortBy('createdAt', 'asc')
      .fetch();

    return {
      posts: posts.map(post => {
        post.category = categories.find(category => category.slug === post.category);
        return post;
      }),
      category
    }
  },
  head() {
    return {
      title: this.category.title
    }
  }
}
</script>
