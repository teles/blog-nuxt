<template>
  <fragment>
    <jumbotron :post="posts[0]"/>
    <featured-posts :posts="posts.slice(1, 5)"/>
  </fragment>
</template>

<script>
import Jumbotron from '../components/Jumbotron';
import FeaturedPosts from '../components/FeaturedPosts';
import {Fragment} from 'vue-fragment';

export default {
  components: {
    Jumbotron,
    FeaturedPosts,
    Fragment
  },
  async asyncData({$content}) {
    const posts = await $content('posts')
      .only(['title', 'description', 'image', 'slug', 'published'])
      .where({published: true})
      .sortBy('createdAt', 'asc')
      .fetch();

    return {
      posts
    }
  }
}
</script>
