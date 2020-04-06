<template lang="pug">
  .SecVision#vision
    SectionTitle(:title="'Vision'")
    .container
      .main_wrapper
        .idea
          IdeaSvg.idea_svg
          .idea_txt 休暇中の学生にコロナに負けないビジコンを
        .comment
          .comment_img
            img.comment_img_img(src="~/assets/images/yokoyama_kazuki.png")
            .comment_who(v-if="$mq === 'sm'")
              .comment_who--post 運営代表  長岡高専 専攻科 2年
              .comment_who--name 横山 和輝
          .comment_wrapper
            .comment_who(v-if="$mq !== 'sm'")
              .comment_who--post 運営代表  長岡高専 専攻科 2年
              .comment_who--name 横山 和輝
            .comment_txt
              p 今、世界では新型コロナウイルス感染症 (COVID-19) が流行し、経済に大きな影響が出ています。外出自粛の中、学校もバイトも休みでなにをやればいいか分からないって思っている学生も多いのではないでしょうか。コロナが流行している今の社会だからこそ「アフターコロナ」「ウィズコロナ」について考えませんか？
              p “Online Intern Contest 2020-2" では、完全オンラインで全国の学生と協力してコロナ対策に取り組めます！
              p 就活イベントの多くが中止になって困っている21卒の学生さんや夏季インターンが開催されるか不安な22卒の学生さん大歓迎です！
              p また第二回となる今回は高校生の参加もOKです！
              p 前回のオンコンに参加していただいた学生も、今まで学外活動に取り組んだことのない学生も、社会のピンチを自分のチャンスに変えましょう！
        //- .matching
        //-   .matching_thinkings
        //-     .matching_thinkings_title: span 学生の<br>思い
        //-     .matching_thinkings_txt
        //-       p 企業に認められるような経験や実績を積みたい！
        //-       p 自分に合う企業へ就職したい！
        //-       p 地方でもビジコン等に挑戦できる機会が欲しい！
        //-   .matching_logo
        //-     MatchingSvg.matching_logo_svg
        //-   .matching_thinkings
        //-     .matching_thinkings_title: span 企業の<br>思い
        //-     .matching_thinkings_txt
        //-       p ハッカソンやアイデアソン、ビジネスコンテストなど、
        //-         | 様々なイベントに参加するアクティブな学生がほしい！
        //-       p 学生のプロジェクトの進め方を見てみたい！
</template>
<script>
// components
import SectionTitle from '~/components/atoms/SectionTitle.vue'
// svgs
import IdeaSvg from '~/assets/images/idea.svg?inline'
import MatchingSvg from '~/assets/images/matching.svg?inline'

export default {
  components: {
    SectionTitle,
    IdeaSvg,
    MatchingSvg
  }
}
</script>
<style lang="scss" scoped>
@import '~/assets/scss/organisms/SecVision.scss';
</style>
