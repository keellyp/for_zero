<template>
  <div class="home">
    <Nav></Nav>
    <Header></Header>
    <div class="cards">
      <div class="tag">
        <p>News</p>
      </div>
    <section class="cardsWrapper" ref="cards">
      <div class="cards__col--left">
        <Card
          cover="card-gabriel.jpg"
          title="Gabriel Garzón-Montano – “Fruitflies” – Live in studio">
        </Card>
        <Card
          cover="card-dj.jpg"
          title="DJ Harrison – “PianoJazz / PartyLife”"
          desc="HazyMoods coming June 16">
        </Card>
        <Card
          cover="card-gabriel.jpg"
          title="Gabriel Garzón-Montano – “Fruitflies” – Live in studio">
        </Card>
      </div>
      <div class="cards__col--center">
        <Card
          cover="card-piano.jpg"
          title="In the studio with DJ Harrison – “KalimbaTale”">
        </Card>
        <List class="cardsGrid--list" ref="list"></List>
        <Card
          cover="card-steoples.jpg"
          title="The Steoples – “From the Otherside” ">
        </Card>
      </div>
      <div class="cards__col--right">
        <Head class="cardsGrid--head" ref="head"></Head>
        <div class="cardscolRight__row">
          <Card
            cover="card-dj.jpg"
            title="DJ Harrison – “PianoJazz / PartyLife”"
            desc="HazyMoods coming June 16">
          </Card>
          <Card
          cover="card-steoples.jpg"
          title="The Steoples – “From the Otherside” ">
          </Card>
        </div>
      </div>
    </section>
    </div>

  </div>
</template>

<script>
import ScrollReveal from 'scrollreveal';

import Header from '../components/Header';
import Card from '../components/Card';
import Head from '../components/Head';
import List from '../components/List';
import Nav from '../components/Nav';

export default {
  name: 'Home',
  components: { Header, Card, Head, List, Nav },
  data() {
    return {
      sr: null,
    };
  },
  mounted() {
    this.sr = new ScrollReveal({ reset: true, duration: 400 });
    this.reveal();
  },
  methods: {
    reveal() {
      const cards = this.$refs.cards.querySelectorAll('.cardContainer');
      this.sr.reveal(cards);
      this.sr.reveal(this.$refs.list.$el);
      this.sr.reveal(this.$refs.head.$el);
    },
  },
};
</script>

<style lang="scss">
@import '~@/assets/scss/variables/_vars.scss';
.home {
  background-color: $light-grey;
}
.cards {
  margin-left: auto;
  width: calc(100% - 10rem);
  padding: 10rem 0 14rem 0;
  .tag {
    margin-left: 4rem;
  }
}
.cardsWrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.cards__col--left,
.cards__col--center,
.cards__col--right {
  display: inline-flex;
  flex-direction: column;
}
.cards__col--left {
  flex: 1;
}
.cards__col--center {
  flex: 1;
  margin-top: -10rem;
}
.cards__col--right {
  flex: 2;
}
.cardscolRight__row {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-between;

  .cardContainer {
    flex: 1;
  }
}
</style>
