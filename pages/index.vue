<template>
  <Archive :posts="posts" />
</template>

<script>
import Archive from '~/components/Archive';

export default {
  components: {
    Archive
  },
  async asyncData({$content}) {
    const categories = await $content('categories')
      .only(['slug', 'title'])
      .fetch();

    const posts = await $content('posts')
      .only(['title', 'description', 'category', 'image', 'slug', 'published'])
      .where({published: true})
      .sortBy('createdAt', 'asc')
      .fetch();

    return {
      posts: posts.map(post => {
        post.category = categories.find(category => category.slug === post.category);
        return post;
      })
    }
  }
}
</script>
