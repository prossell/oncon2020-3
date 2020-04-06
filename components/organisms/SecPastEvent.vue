<template lang="pug">
  .SecPastEvent#pastevent
    SectionTitle(:title="'Past events'")
    .container
      .event(v-for="(event, event_key) in events" :key="`event_key${event_key}`")
        a(:href="event.link")
          .event_data {{event.data}}
          .event_title {{event.title}}
</template>

<script>
import SectionTitle from '~/components/atoms/SectionTitle.vue'
export default {
  components: {
    SectionTitle
  },
  data() {
    return {
      events: [
        {
          link: 'https://oncon2020.prossell.jp/',
          data: '1/14〜3/3',
          title: 'ONLINE INTERN CONTEST 2020'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
// .SecPastEvent {
//   position: relative;
// }

.event {
  font-family: $PT-sans;
  text-align: center;
  position: relative;
  a {
    color: $black-txt;
  }
  &_data {
    display: inline;
  }
  &_title {
    font-size: 2rem;
    display: inline;
    padding-left: 16px;
  }
}
</style>
