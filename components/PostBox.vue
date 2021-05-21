<template>
  <div class="post-box">
    <h2 class="post-box__title">
      <NuxtLink :to="{ name: 'slug', params: { slug: post.slug } }" class="post-box__title__link">
        {{post.title}}
      </NuxtLink>
    </h2>
    <img class="post-box__image" v-if="post.image && post.image.src" src="post.image.src" />
    <div class="post-box__image"  v-else></div>
    <div class="post-box__description">
      {{post.description}}
    </div>
    <span onclick="location.href='/papel-de-parede/'" class="post-box__call-to-action">Continue</span>
  </div>
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
.post-box {
  display: grid;
  grid-gap: 10px;
  grid-template-areas:
    "post-box-categories"
    "post-box-image"
    "post-box-title"
    "post-box-description"
    "post-box-call-to-action";
  padding: 16px;
  text-decoration: none;
  color: #333;
  font-family: sans-serif;
  margin: 8px;
  grid-template-rows: auto auto 1fr auto;
}
@media(min-width: 768px) {
  .post-box {
    grid-template-areas:
      "post-box-image post-box-categories post-box-categories"
      "post-box-image post-box-title post-box-title"
      "post-box-image post-box-description post-box-description"
      "post-box-image post-box-call-to-action post-box-call-to-action";
    grid-template-columns: 1fr 1fr;
  }
}
.post-box__image,
.post-box__image--not-found {
  width: 100%;
  grid-area: post-box-image;
  max-height: 300px;
  object-fit: cover;
  align-self: center;
  background-color: #fafafa;
  min-height: 100%;
  border: none;
}
.post-box__image--not-found {
  background-color: #666;
}
.post-box__title {
  grid-area: post-box-title;
  margin: 16px 8px;
  font-size: 1.65em;
  color: #333;
}
.post-box__separator {
  color: #303030;
  margin-right: 4px;
}
.post-box__title__link {
  text-decoration: none;
  color: inherit;
}
.post-box__title:after {
  content: "";
  width: 100px;
  height: 2px;
  background: #f06;
  display: block;
  margin-top: 16px;
}
.post-box__description {
  grid-area: post-box-description;
  display: -webkit-box;
  -webkit-line-clamp: 6;
  -webkit-box-orient: vertical;
  max-height: calc(8em * 1.05);
  overflow: hidden;
  margin-left: 8px;
  font-size: 1.05em;
  line-height: 1.4;
}
.post-box__categories {
  grid-area: post-box-categories;
}
.post-box__call-to-action {
  grid-area: post-box-call-to-action;
  margin-left: 8px;
  text-transform: uppercase;
  color: #f06;
  font-weight: 100;
  font-size: .8em;
  cursor: pointer;
}
.post-box__call-to-action:after {
  content: "";
  margin-top: 2px;
}
.post-box__categories__link {
  text-transform: uppercase;
  text-decoration: none;
  margin-left: 8px;
  margin-top: 8px;
  font-size: .9em;
  color: #f06;
  font-weight: 100;
}
</style>
