<template>
  <div class="headContainer">
    <div class="infosTop">
      <div class="tag">
        <p>New Releases</p>
      </div>
      <a href="#" class="small-link">view all</a>
    </div>
    <div class="coverAlbum">
      <div ref="cover" class="coverContainer">
        <img src="/static/head-harrison.png" alt="#">
        <img src="/static/head-2.png" alt="#">
        <img src="/static/head-harrison.png" alt="#">
      </div>
      <div @click=prevCover class="cover__arrowleft"></div>
      <div @click=nextCover class="cover__arrowright"></div>
    </div>
    <div class="mainInfos">
      <p class="mainInfos__artist">DJ Harrison</p>
      <h3 class="mainInfos__title">Hazy Moods</h3>
      <div class="sliderDots" ref="sliderDots">
        <div class="dot dot--current"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HeadComponent',
  data() {
    return {
      sliderCounter: 0,
    };
  },
  methods: {
    prevCover() {
      this.sliderCounter > 0
        ? (this.sliderCounter -= 1)
        : (this.sliderCounter = 2);
      this.$refs.cover.style.transform = `translateX(-${this.sliderCounter *
        100}%)`;
      this.sliderDots();
    },
    nextCover() {
      this.sliderCounter < 2
        ? (this.sliderCounter += 1)
        : (this.sliderCounter = 0);
      this.$refs.cover.style.transform = `translateX(-${this.sliderCounter *
        100}%)`;
      this.sliderDots();
    },
    sliderDots() {
      for (
        let index = 0;
        index < this.$refs.sliderDots.children.length;
        index += 1
      ) {
        this.$refs.sliderDots.children[index].classList.remove('dot--current');
      }
      this.$refs.sliderDots.children[this.sliderCounter].classList.add(
        'dot--current',
      );
    },
  },
};
</script>

<style lang="scss">
@import '~@/assets/scss/variables/_vars.scss';
@import '~@/assets/scss/helpers/_mixins.scss';
.headContainer {
  background-color: $beige;
  box-shadow: $shadow;
  padding: 4rem;
  margin: 3rem 4rem;
}
.infosTop {
  @include flex(row, center, space-between);
  margin-bottom: 3rem;
}
.coverAlbum {
  position: relative;
  overflow: hidden;

  .cover__arrowleft,
  .cover__arrowright {
    position: absolute;
    top: 50%;
    will-change: transform;
    transform: translateY(-50%);
    cursor: pointer;
    width: 15px;
    height: 15px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
    z-index: 1;
  }
  .cover__arrowleft {
    background-image: url(/static/arrow-left.svg);
    left: 0;
  }
  .cover__arrowright {
    background-image: url(/static/arrow-right.svg);
    right: 0;
  }
  img {
    width: 100%;
    height: 100%;
  }
}
.coverContainer {
  display: flex;
  flex-wrap: nowrap;
  transition: all 0.3s ease-in-out;
}
.mainInfos {
  color: $white;
  text-align: center;
}
.mainInfos__artist {
  font-style: italic;
  font-size: 0.6875em;
}
.mainInfos__title {
  font-size: 1em;
}
.sliderDots {
  display: inline-block;
  margin-top: 3rem;
}
.dot {
  width: 5px;
  height: 5px;
  border-radius: 5px;
  border: 1px solid $white;
  display: inline-block;
}
.dot--current {
  background-color: $white;
}
</style>
