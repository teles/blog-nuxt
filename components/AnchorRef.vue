<template>
    <a :href="href">
      <slot />
    </a>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    params: {
      type: Object,
      required: false,
      default: () => ({})
    }
  },
  data() {
    return {
      href: this.$router.resolve({name: this.name, params: this.params}).href
    }
  }
}
</script>

<style>

</style>
