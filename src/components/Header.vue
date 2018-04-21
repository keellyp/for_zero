<template>
  <div class="headerContainer">
    <header class="headerWrapper">
      <div class="headline">
        <div class="hidden-wrapper">
          <p>New Release</p>
        </div>
        <div class="hidden-wrapper">
          <h1>Washed Out</h1>
        </div>
        <div class="hidden-wrapper">
          <h2>Get Lost</h2>
        </div>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: 'HeaderComponent',
};
</script>

<style lang="scss">
@import '~@/assets/scss/variables/_vars.scss';
@import '~@/assets/scss/helpers/_mixins.scss';

.headerWrapper {
  height: 100vh;
  background-image: url('/static/bg-washedout.jpg');
  background-size: cover;
  background-position: center;
  @include flex(column, center, center);
}

.headline {
  text-align: center;
  color: $white;
  p {
    animation: textEnter 0.3s ease-in 1;
  }
  h1 {
    margin: 1rem 0;
    animation: textEnter 0.5s ease-in 1;
  }
  h2 {
    animation: textEnter 0.7s ease-in 1;
  }
  @keyframes textEnter {
    0% {
      transform: translateY(100%);
    }
    100% {
      transform: translateY(0%);
    }
  }
}
</style>
