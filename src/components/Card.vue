<template>
  <div class="cardContainer">
    <div class="coverWrapper">
      <img :src="'/static/'+cover" :alt=cover>
    </div>
    <div class="descWrapper">
      <h3> {{ title }}</h3>
      <p class="caption"> {{ desc }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: ['cover', 'title', 'desc'],
};
</script>

<style lang="scss">
@import '~@/assets/scss/variables/_vars.scss';
@import '~@/assets/scss/helpers/_mixins.scss';

.cardContainer {
  background-color: $white;
  box-shadow: $shadow;
  margin: 3rem 4rem;
  cursor: pointer;
  transition: all 0.2s ease-in-out;

  &:hover {
    box-shadow: $hover-shadow;
    transition: all 0.2s ease-in-out;
  }
}
.coverWrapper {
  width: 100%;

  img {
    width: 100%;
    object-fit: cover;
    object-position: center;
  }
}
.descWrapper {
  padding: 3rem;
}
</style>
