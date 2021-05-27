<template>
  <fragment>
    <Jumbotron :post="posts[0]" v-if="posts.length > 0" />
    <FeaturedPosts :posts="posts.slice(1, 5)" v-if="posts.length > 3" />
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
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>
