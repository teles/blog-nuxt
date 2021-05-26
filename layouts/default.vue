<template>
  <div class="page">
    <page-header :is-darker="false" :is-sticky="false" />
    <main class="page__main">
      <Nuxt />
    </main>
    <page-footer />
  </div>
</template>

<script>
import PageHeader from '../components/PageHeader'
import PageFooter from '../components/PageFooter'

export default {
  components: {
    PageHeader,
    PageFooter
  }
}
</script>

<style>
@import '../static/css/_global-variables.css';
@import '../static/css/_global.css';
@import '../static/css/_page.css';
</style>
