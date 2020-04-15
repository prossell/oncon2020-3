<template lang="pug">
  .SecSupporters#supporters
    SectionTitle(:title="'Supporter'")
    .container(v-if="publish")
      .supporters_list(v-if="supporters")
        .supporter_box(v-for="(sup, sup_key) in supporters" :key="`sup_key${sup_key}`")
          a(:href="sup.link")
            img.sup_logo(v-if="sup.logo" :src="require(`~/assets/sponsor_imgs/${sup.logo}.png`)")
            .supporter_name(v-if="$i18n.locale === 'ja'") {{sup.jaName}}
            .supporter_name(v-else) {{sup.enName}}
</template>
<script>
import SectionTitle from '~/components/atoms/SectionTitle.vue'

export default {
  components: {
    SectionTitle
  },
  data() {
    return {
      publish: true,
      supporters: [
        {
          link: 'https://dena.com/jp/',
          logo: 'dena',
          jaName: '株式会社ディー・エヌ・エー',
          enName: 'DeNA Co., Ltd.'
        },
        {
          link: 'https://kosen-career.tech/',
          logo: 'kosen_career',
          jaName: '株式会社 高専キャリア教育研究所',
          enName: 'Kosen Career Co., Ltd.'
        }
      ]
    }
  }
}
</script>
<style lang="scss" scoped>
.supporters_list {
  @include flex($wrap: wrap, $justifyContent: center, $alignItems: flex-start);
  width: 100%;
}
.supporter_box {
  padding: 8px;
  margin-bottom: 36px;
  width: 60%;
}

.sup_logo {
  display: block;
  width: 100%;
  height: 100%;
  background: $white;
  transition: 0.3s $ease-out-1;
  transform: translateY(0);
  &::before {
    content: '';
    display: block;
    padding-top: 50%;
    background: $white;
  }
  &:hover {
    transform: translateY(-8px);
    box-shadow: 0 4px 16px rgba($black, 0.1);
  }
}
.supporter_name {
  text-align: center;
  color: $gray-txt;
  padding: 4px 0;
  font-size: 1.8rem;
  // span {
  //   color: $gray;
  //   font-size: 1.5rem;
  //   padding-right: 12px;
  // }
}
</style>
