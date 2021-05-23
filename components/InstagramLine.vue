<template>
  <section class="instagram-line">
    <div class="instagram-line__photo" v-for="(photo, index) in photos" :key="index">
      <img :src="photo.image.src" :alt="photo.alt" :width="photo.image.width" :height="photo.image.height" />
    </div>
  </section>
</template>
<script>
const InstagramAdapter = (data, dimension = 640) => {
  return data.graphql.user.edge_owner_to_timeline_media.edges.map(edge => {
    console.log(JSON.stringify(edge));
    return {
      alt: edge.node.accessibility_caption,
      text: edge.node.edge_media_to_caption.edges[0].node.text,
      image: edge.node.thumbnail_resources
        .filter(thumb => {
          return thumb.config_width === dimension && thumb.config_height === dimension
        })
        .map(thumb => {
          return {
            src: thumb.src,
            width: thumb.config_width,
            height: thumb.config_height
          }
        })[0]
    };
  })
};

export default {
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      photos: InstagramAdapter(this.data)
    }
  }
}
</script>
