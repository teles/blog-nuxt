<template>
  <fragment>
  <header :class="isDarker ? 'page__header--is-darker' : 'page__header'">
    <a class="page__header__logo" href="/">
      <img src="/img/logo-principal-seamodapega.svg" class="page__header__logo__image" />
    </a>
    <ul class="page__header__actions">
      <li class="page__header__action">🔎</li>
    </ul>
  </header>
  <page-navigation :is-darker="isDarker" />
  </fragment>
</template>

<script>
import PageNavigation from './PageNavigation'
import {Fragment} from 'vue-fragment';

export default {
  components: {
    PageNavigation,
    Fragment
  },
  props: {
    isDarker: {
      type: Boolean,
      required: false,
      default: false
    }
  }
}
</script>
<style>
@import '../static/css/_global-variables.css';

.page__header,
.page__header--is-darker {
  display: flex;
  border-bottom: 1px solid #e2e2e9;
  padding: var(--spacing-2) var(--spacing-1) 0 var(--spacing-1);
}

.page__header--is-darker {
  background-color: var(--color-dark);
}

@media(min-width: 768px) {
  .page__header,
  .page__header--is-darker {
    display: grid;
    margin: 0 auto;
    align-items: center;
    grid-template-areas: ". logo actions. " ". line line. ";
    grid-template-columns: 1fr minmax(280px, 640px) minmax(280px, 640px) 1fr;
    border-bottom: 0;
  }

  .page__header::after,
  .page__header--is-darker::after {
    grid-area: line;
    content: "";
    display: block;
    width: 100%;
    height: 1px;
    background-color: var(--color-gray-regular);
  }
}

.page__header__actions {
  grid-area: actions;
  list-style-type: none;
  margin-left: auto;
}

.page__header__action {
  cursor: pointer;
}
.page__header__logo {
  grid-area: logo;
}

.page__header__logo__image {
  margin: var(--spacing-1) var(--spacing-2) var(--spacing-1) 0;
  width: 220px;
  height: auto;
  border: 1px solid #fff;
}

@media(min-width: 768px) {
  .page__header__logo__image {
    font-size: 2em;
    width: 280px;
  }
}

</style>
