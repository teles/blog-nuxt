<template>
  <ul class="featured-posts">
    <li class="featured-posts__post" v-for="(post, index) in posts" :key="index">
      <a href="lala" class="featured-posts_post__category">{{post.category}}</a>
      <img :src="post.image.src" class="featured-posts__post__image">
      <h2 class="featured-posts__post__title">
        <NuxtLink :to="{ name: 'slug', params: { slug: post.slug } }" class="featured-posts__post__anchor">
          {{post.title}}
        </NuxtLink>
      </h2>
      <p class="featured-posts__post__description">{{`${post.description.substring(0, 200)}...`}}</p>
    </li>
  </ul>
</template>
<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>
<style>
@import '../static/css/_global-variables.css';

.featured-posts {
  display: block;
  box-sizing: border-box;
  margin: 20px auto 0 auto;
  background-color: var(--color-almost-white);
  padding: 40px var(--spacing-1);
}

@media (min-width: 768px) {
  .featured-posts {
    display: grid;
    grid-template-areas: ". first second ." ". third fourth .";
    grid-gap: var(--spacing-2);
  }
}

@media (min-width: 1024px) {
  .featured-posts {
    display: grid;
    grid-template-areas: ". first second ." ". first third ." ". first fourth .";
    grid-gap: var(--spacing-2);
    grid-template-columns: 1fr minmax(418px, 700px) minmax(350px, 580px) 1fr;
    grid-template-rows: min-content min-content;
  }
}

.featured-posts__post:nth-child(1) {
  grid-area: first;
}

.featured-posts__post:nth-child(2) {
  grid-area: second;
}

.featured-posts__post:nth-child(3) {
  grid-area: third;
}

.featured-posts__post:nth-child(4) {
  grid-area: fourth;
}

.featured-posts_post__category {
  display: block;
  text-decoration: none;
  grid-area: link;
  text-transform: uppercase;
  font-size: .8em;
  font-weight: 600;
  color: var(--color-red-featured);
}

.featured-posts__post {
  display: block;
  list-style: none;
  grid-gap: 10px;
  max-height: 100%;
}

@media(min-width: 768px) {
  .featured-posts__post {
    display: block;
  }
}

@media(min-width: 1024px) {

  .featured-posts__post {
    display: grid;
    grid-gap: 10px;
  }

  .featured-posts__post:first-child {
    grid-template-areas:
      "link link "
      "image image"
      "title title"
      "description description";
    grid-template-columns: minmax(120px, 33%) 1fr;
    grid-template-rows: repeat(4, min-content);
  }

  .featured-posts__post:not(:first-child) {
    grid-template-areas:
      "link link"
      "image title"
      "image description";
    grid-template-columns: minmax(200px, 33%) 1fr;
    grid-template-rows: repeat(3, min-content);
  }
}

.featured-posts__post__image {
  width: 100%;
  margin-bottom: 20px;
  grid-area: image;
  object-fit: cover;
  border-radius: 4px;
}

.featured-posts__post__title {
  margin: 0;
  grid-area: title;
}

.featured-posts__post__title::first-letter {
  text-transform: uppercase;
}

.featured-posts__post__anchor {
  text-decoration: none;
  color: var(--color-dark);
}

.featured-posts__post__description {
  color: var(--color-dark--light);
  font-weight: 100;
  margin-top: 10px;
  grid-area: description;
  line-height: var(--line-height-regular);
}
</style>
