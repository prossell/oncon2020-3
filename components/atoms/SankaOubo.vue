<template lang="pug">
  .sankaoubo_box
    nuxt-link(to="/disclaimer").application_btn
      SankaouboSvg.sankaoubo(v-if="this.$i18n.locale === 'ja'")
      .sankaoubo(v-if="this.$i18n.locale === 'en'")
        .enfont Apply for this event

</template>
<script>
import SankaouboSvg from '~/assets/images/sankaoubo.svg?inline'
import BoshushuryoSvg from '~/assets/images/boshushuryo.svg?inline'
import CommingSoonSvg from '~/assets/images/comming_soon.svg?inline'
export default {
  components: {
    SankaouboSvg,
    BoshushuryoSvg,
    CommingSoonSvg
  }
}
</script>
<style lang="scss" scoped>
.application_btn {
  width: 520px;
  height: 72px;
  margin-left: auto;
  text-decoration: none;
  background-color: $black;
  @include flex($justifyContent: center);
  &:hover {
    .sankaoubo {
      transform: scale(0.9);
    }
  }
}

.sankaoubo {
  transition: 0.4s $ease-out-1;
  width: 260px;
}

.enfont {
  color: $theme-green;
  text-align: center;
  font-family: $noto-sans;
  font-weight: bold;
  font-style: italic;
  font-size: 2.4rem;
  background: -webkit-linear-gradient(60deg, $theme-green, $theme-blue);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

@media screen and (max-width: $md) {
  .application_btn {
    width: 30vw;
    height: 5vw;
  }
  .sankaoubo {
    width: 24vw;
  }
  .enfont {
    font-size: 2rem;
  }
}

@media screen and (max-width: $tb) {
  .enfont {
    font-size: 1.8rem;
  }
}

@media screen and (max-width: $sm) {
  .application_btn {
    margin: auto;
    width: 100%;
    height: 52px;
  }
  .sankaoubo {
    width: 75%;
  }
  .enfont {
    font-size: 2rem;
  }
}
</style>
