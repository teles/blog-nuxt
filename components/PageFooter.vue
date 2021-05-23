<template>
  <footer class="page__footer">
    <img src="/img/logo-principal-seamodapega.svg" class="page__footer__logo" />
  </footer>
</template>
<style>
@import '../static/css/_global-variables.css';

.page__footer {
  display: grid;
  background-color: var(--color-dark);
  grid-template-areas:
    ". content .";
  grid-template-columns: 1fr 1280px 1fr;
  padding: 0 var(--spacing-1);
}

.page__footer__logo {
  grid-area: content;
  height: auto;
  border: 1px solid #fff;
  width: 180px;
  margin: var(--spacing-2) var(--spacing-2) var(--spacing-2) 0;
}

</style>
