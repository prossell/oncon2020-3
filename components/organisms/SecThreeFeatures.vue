<template lang="pug">
  .SecThreeFeatures#threefeatures
    .container
      SectionTitle(:title="'ThreeFeatures'")
      .feature_content_wrapper
        .feature_content
          .feature_topic(v-for="(feature,feature_id) in features")
            OneFeature(
              :title="'feature.' + feature + '.title'"
              :logo="feature_id"
              :discription="'feature.' + feature + '.discription'"
            )
</template>
<script>
// components
import SectionTitle from '~/components/atoms/SectionTitle.vue'
import OneFeature from '~/components/molecules/OneFeature.vue'
// svg
export default {
  components: {
    SectionTitle,
    OneFeature
  },
  data() {
    return {
      features: ['online', 'link', 'process']
    }
  }
}
</script>
<style lang="scss" scoped>
@import '~/assets/scss/organisms/SecThreeFeatures.scss';
</style>
