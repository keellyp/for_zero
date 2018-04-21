<template>
  <div class="listContainer">
    <h3>Upcoming Events</h3>
    <div
      class="list__element"
      v-for="(event, index) in events"
      :key=index>
      <div class="el__date">{{event[0].date}}</div>
      <div>
        <p class="el__artist">{{event[1].artist}}</p>
        <p class="footnote">{{event[2].place}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListComponent',
  data() {
    return {
      events: [
        [
          { date: '5/31' },
          { artist: 'Gabriel Garzón-Montano' },
          { place: 'Nagano' },
        ],
        [
          { date: '5/31' },
          { artist: 'Peanut Butter Wolf' },
          { place: 'Soundset Festival' },
        ],
        [
          { date: '5/31' },
          { artist: 'Gabriel Garzón-Montano' },
          { place: 'Washington, DC' },
        ],
        [{ date: '5/31' }, { artist: 'Tuxedo' }, { place: 'Allston, MA' }],
        [
          { date: '5/31' },
          { artist: 'Gabriel Garzón-Montano' },
          { place: 'Philadelphia' },
        ],
        [
          { date: '5/31' },
          { artist: 'Gabriel Garzón-Montano' },
          { place: 'Nagano' },
        ],
      ],
    };
  },
};
</script>

<style lang="scss">
@import '~@/assets/scss/variables/_vars.scss';
@import '~@/assets/scss/helpers/_mixins.scss';

.listContainer {
  box-shadow: $shadow;
  background-color: $black;
  color: $white;
  font-size: 0.75em;
  margin: 3rem 4rem;

  h3 {
    font-weight: $bold;
    padding: 2.4rem 1.8rem;
  }
}
.list__element {
  border-top: 1px solid $dark-grey;
  padding: 1.8rem 1.5rem;
  @include flex(row, flex-start, flex-start);
}
.el__date {
  margin-right: 2rem;
  letter-spacing: 1px;
}
.el__artist {
  font-weight: $bold;
}
</style>
