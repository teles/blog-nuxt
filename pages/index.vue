<template>
  <div>
    <h1>Blog Posts</h1>
    <ul>
      <li v-for="post of posts" :key="post.slug">
        <NuxtLink :to="{ name: 'slug', params: { slug: post.slug } }">
          <img :src="post.img" />
          <div>
            <h2>{{ post.title }}</h2>
            <p>{{ post.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content('posts')
      .only(['title', 'description', 'img', 'slug'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      posts
    }
  }
}
</script>
