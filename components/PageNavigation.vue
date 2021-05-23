<template>
  <nav :class="isDarker ? 'page__navigation--darker' : 'page_navigation' ">
    <ul class="page__navigation__list">
      <li class="page__navigation__item">
        <a class="page__navigation__anchor">Moda</a>
      </li>
      <li class="page__navigation__item">
        <a class="page__navigation__anchor">Comportamento</a>
      </li>
      <li class="page__navigation__item">
        <a class="page__navigation__anchor">Bem Estar</a>
      </li>
      <li class="page__navigation__item">
        <a class="page__navigation__anchor">Estilo de vida</a>
      </li>
    </ul>
  </nav>
</template>
<script>
export default {
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

.page__navigation,
.page__navigation--darker {
  padding: 0 var(--spacing-1);
}

.page__navigation--darker {
  background-color: var(--color-dark);
  color: #fff;
}

.page__navigation__list {
  margin: 0 auto;
  max-width: 1280px;
  list-style: none;
  padding: var(--spacing-2) 0;
  display: block;
  gap: 20px;
}

@media(min-width: 768px) {
  .page__navigation__list {
    display: flex;
  }
}

.page__navigation__item {
  text-transform: uppercase;
  font-size: .8em;
  font-weight: 800;
  transition: all ease-in .2s;
}

.page__navigation__item:hover {
  opacity: .5;
  cursor: pointer;
}
</style>
