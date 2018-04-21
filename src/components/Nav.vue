<template>
  <div class="navContainer">
    <div class="searchBox">
      <ul>
        <li><img src="/static/icon-search.svg" alt="Search"></li>
        <li><img src="/static/icon-account.svg" alt="Account"></li>
        <li><img src="/static/icon-pack.svg" alt="Pack"></li>
      </ul>
    </div>
    <transition name="fade">
      <div class="background" v-show="isOpened"></div>
    </transition>
    <header class="navSide">
      <div class="navSide__logo">
        <img src="/static/logo.svg" alt="Logo">
      </div>
      <div class="navSide__btn">
        <button class="btn" @click=toggleMenu v-if="!isOpened">Menu</button>
        <button class="btn" @click=toggleMenu v-else>Close</button>
      </div>
      <transition name="toRight">
        <header class="navOpen" v-show="isOpened">
          <div class="navOpen__wrapper">
            <section class="nav--left">
              <nav class="navOpen__links">
                <ul class="navOpen__mainlinks">
                  <li class="navOpen__route"><a href="#" title="link">Artists</a></li>
                  <li class="navOpen__route"><a href="#" title="link">Events</a></li>
                  <li class="navOpen__route"><a href="#" title="link">News Archive</a> </li>
                  <li class="navOpen__route"><a href="#" title="link">Contact</a></li>
                </ul>
                <div class="navOpen__shop">
                  <p class="navOpen__route">Shop</p>
                  <nav>
                    <ul>
                      <li>Vinyl</li>
                      <li>7-Inch</li>
                      <li>7-Inch</li>
                      <li>Mp3</li>
                      <li>Cassette</li>
                      <li>CDs</li>
                      <li>Special Editions</li>
                      <li>Vinyl Subscription</li>
                    </ul>
                    <ul>
                      <li>Shirts</li>
                      <li>Sweatshirts</li>
                      <li>Hats</li>
                      <li>Accessories</li>
                      <li>Artwork</li>
                    </ul>
                  </nav>
                </div>
              </nav>
            </section>
            <section class="nav--right">
              <div class="navOpen__slider">
                <div class="slider--wrapper">
                  <div class="slider__infosTop">
                    <div class="tag">
                      <p>New Releases</p>
                    </div>
                    <a href="#" class="link">see all</a>
                  </div>
                  <div class="slider__coverAlbum" ref="cover">
                    <img src="/static/head-harrison.png" alt="#">
                    <img src="/static/head-2.png" alt="#">
                    <img src="/static/head-harrison.png" alt="#">
                  </div>
                  <div class="slider__mainInfos">
                    <p class="slider__mainInfos__artist">DJ Harrison</p>
                    <h3 class="slider__mainInfos__title">Hazy Moods</h3>
                    <div class="slider__dots" ref="sliderDots">
                      <div class="dot"></div>
                      <div class="dot"></div>
                      <div class="dot"></div>
                    </div>
                  </div>
                </div>
              </div>
            </section>
          </div>
        </header>
      </transition>
    </header>
  </div>
</template>

<script>
export default {
  name: 'NavComponent',
  data() {
    return {
      isOpened: false,
      currentSlide: 0,
    };
  },
  mounted() {
    this.initSlider();
    setInterval(() => {
      this.initSlider();
    }, 1500);
  },
  methods: {
    toggleMenu() {
      this.isOpened = !this.isOpened;
    },
    sliderDots() {
      for (
        let index = 0;
        index < this.$refs.sliderDots.children.length;
        index += 1
      ) {
        this.$refs.sliderDots.children[index].classList.remove('dot--current');
      }
      this.$refs.sliderDots.children[this.currentSlide].classList.add(
        'dot--current',
      );
    },
    initSlider() {
      this.currentSlide < 2
        ? (this.currentSlide += 1)
        : (this.currentSlide = 0);
      switch (this.currentSlide) {
        case 0:
          this.$refs.cover.style.transform = 'translateX(50%)';
          break;
        case 1:
          this.$refs.cover.style.transform = 'translateX(0%)';
          break;
        case 2:
          this.$refs.cover.style.transform = 'translateX(-50%)';
          break;
        default:
          break;
      }
      this.sliderDots();
    },
  },
};
</script>

<style lang="scss">
@import '~@/assets/scss/variables/_vars.scss';
@import '~@/assets/scss/helpers/_mixins.scss';

.searchBox {
  position: fixed;
  top: 0;
  right: 0;
  z-index: 9;
}
.searchBox ul {
  @include flex(row, center, space-between);
}
.searchBox ul li {
  width: 8rem;
  height: 8rem;
  background-color: $main-color;
  transition: all 0.4s ease-out;
  @include flex();
}
.searchBox ul li:hover {
  cursor: pointer;
  background-color: #f57200;
  transition: all 0.2s ease-out;
}
.background {
  background: $black;
  will-change: opacity;
  opacity: 0.75;
  width: 100%;
  height: 100%;
  position: fixed;
  z-index: 10;
  top: 0;
  left: 0;
}
.navSide {
  display: flex;
  flex-direction: column;
  width: 8rem;
  height: 60%;
  position: fixed;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  z-index: 10;
  box-shadow: $shadow;
}
.navSide__logo {
  background-color: $white;
  flex: 2;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.navSide__logo img {
  margin-top: 1.5rem;
}
.navSide__btn {
  transform-origin: top right;
  transform: rotate(-90deg) translate(0%, -100%);

  button {
    height: 2rem;
  }
}
.navOpen {
  position: absolute;
  top: 0;
  left: 100%;
  height: 100%;
  width: calc(100vw - 8rem);
  z-index: -1;
}
.navOpen__wrapper {
  @include flex(row, flex-start, flex-start);
  height: 100%;
}
.nav--left,
.nav--right {
  height: 100%;
  flex: 1;
}
.nav--left {
  background-color: $white;
}
.nav--right {
  background-color: $light-grey;
}
.navOpen__links {
  display: flex;
  height: auto;
  margin: auto;
  padding: 4rem 3rem;
}
.navOpen__route {
  font-weight: $bold;
  font-size: 1.125em;
  margin-bottom: 2rem;
}
.navOpen__mainlinks {
  flex: 1;
}
.navOpen__mainlinks a {
  position: relative;
  z-index: 0;
  @include p-el(after, 100%, 40%, $main-color);

  &::after {
    z-index: -1;
    left: 0;
    bottom: 0;
    will-change: transform;
    transform: scaleX(0);
    transform-origin: left;
    transition: all 0.3s ease-in-out;
  }

  &:hover::after {
    will-change: transform;
    transform: scaleX(1);
    transition: all 0.3s ease-in-out;
  }
}
.navOpen__shop {
  display: flex;
  flex: 2;
  flex-direction: column;
}
.navOpen__shop nav {
  display: flex;
  flex-direction: row;
}
.navOpen__shop ul {
  margin-right: 4rem;
}
.navOpen__shop li {
  line-height: 2em;
  font-size: 0.75em;
  transition: all 0.2s ease-in-out;
  cursor: pointer;

  &:hover {
    color: $main-color;
    transition: all 0.2s ease-in-out;
  }
}
.navOpen__slider {
  overflow: hidden;
  height: auto;
  margin: auto;
}
.slider__infosTop {
  @include flex(row, center, space-between);
  padding: 3rem 4rem;
}
.slider__infosTop .link {
  font-size: 0.625em;
  font-weight: $bold;
  text-decoration: underline;
}
.slider__coverAlbum {
  margin-bottom: 2rem;
  @include flex(row, center, center);
  transition: all 0.3s ease-in-out;

  img {
    width: 50%;
    height: 50%;
  }
}
.slider__mainInfos {
  text-align: center;
}
.slider__mainInfos__artist {
  font-size: 1.5em;
  line-height: 1.4em;
  font-weight: $bold;
}
.slider__mainInfos__title {
  font-size: 0.75em;
  font-style: italic;
  font-weight: $regular;
}
.slider__dots .dot {
  border-color: $black;
}
.slider__dots .dot--current {
  background-color: $black;
}
.slider__dots {
  margin: 2rem 0;
}
</style>
