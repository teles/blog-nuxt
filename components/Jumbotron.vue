<template>
  <section class="jumbotron">
    <NuxtLink :to="{ name: 'slug', params: { slug: post.slug } }">
      <img :src="post.image.src" class="jumbotron__image">
    </NuxtLink>
    <div class="jumbotron__content">
      <span href="jumbotron__category" class="jumbotron__category">{{post.category}}</span>
      <h2 class="jumbotron__title">
        <NuxtLink :to="{ name: 'slug', params: { slug: post.slug } }" class="jumbotron__title__anchor">
          {{post.title}}
        </NuxtLink>
      </h2>
      <p class="jumbotron__description">{{post.description}}</p>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  }
}
</script>
<style>
@import '../static/css/_global-variables.css';

.jumbotron {
  display: block;
}

@media(min-width: 768px) {
  .jumbotron {
    display: grid;
    grid-template-columns: minmax(450px, 800px) minmax(298px, 600px);
    grid-gap: 20px;
    text-decoration: none;
  }
}

.jumbotron__image {
  max-height: 60vh;
  width: 100%;
  object-fit: cover;
}

.jumbotron__content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: var(--spacing-1) var(--spacing-2) var(--spacing-1) var(--spacing-1);
}

.jumbotron__category {
  text-decoration: none;
  font-weight: 600;
  text-transform: uppercase;
  font-size: 14px;
  letter-spacing: 2px;
  color: var(--color-red-featured);
}

.jumbotron__title {
  line-height: 1.42;
  font-size: 2em;
  padding-right: 10px;
  text-decoration: none;
  margin: 0;
}

.jumbotron__title::first-letter {
  text-transform: uppercase;
}
.jumbotron__title__anchor {
  color: inherit;
}

.jumbotron__description {
  color: var(--color-dark--light);
  font-weight: 200;
  line-height: var(--line-height-regular);
}
</style>
