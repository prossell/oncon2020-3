<template lang="pug">
  .news_vue
    HeaderMenu()
    SubPageTopTitle(:title="'News'")
    .container
      .news_message  {{ $t('news.message') }}
      .wrapper
        .news_list(v-if="$i18n.locale === 'ja'")
          .news(v-for="(news, news_key) in latestNews " :key="`news_${news_key}`" v-if="news.pub")
              .news_wrapper
                a.title(v-if="news.link" :href="news.link") {{news.title_ja}}
                .title(v-else) {{news.title_ja}}
                .date {{news.date}}
              .news_detaile {{news.detaile_ja}}
        .news_list(v-else)
          .news(v-for="(news, news_key) in latestNews " :key="`news_${news_key}`" v-if="news.pub")
              .news_wrapper
                a.title(v-if="news.link" :href="news.link") {{news.title_en}}
                .title(v-else) {{news.title_en}}
                .date {{news.date}}
              .news_detaile {{news.detaile_en}}
        .twitter_timeline
          <a class="twitter-timeline" data-width="400" href="https://twitter.com/Prossell_JP?ref_src=twsrc%5Etfw">Tweets by Prossell_JP</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
    Footer
</template>
<script>
// components
import HeaderMenu from '~/components/molecules/HeaderMenu.vue'
import SubPageTopTitle from '~/components/atoms/SubPageTopTitle'
import SectionTitle from '~/components/atoms/SectionTitle.vue'
import Footer from '~/components/organisms/Footer.vue'

export default {
  components: {
    HeaderMenu,
    SubPageTopTitle,
    SectionTitle,
    Footer
  },
  data() {
    return {
      news_list: [
        {
          pub: true,
          date: '2020/04/08',
          title_ja: 'オンコン公式Webサイトを公開しました。',
          title_en: 'ONCON Official Website Was Launched.'
        },
        {
          pub: true,
          date: '2020/04/08',
          title_ja: '高専マガジンに掲載されました！',
          title_en: 'Report Published in Kosen Magazine',
          detaile_ja: '前回の参加レポートをまとめております。',
          detaile_en: 'Report from a previous participant (Japanese Only)',
          link: 'https://kosen-magazine.com/online-intern-contest-2020-report/'
        },
        {
          pub: true,
          date: '2020/04/15',
          title_ja: 'サポーター企業の公開',
          title_en: 'Introduction of Suportors',
          detaile_ja: '(株)DeNA様',
          detaile_en: 'DeNA Co., Ltd.'
        },
        {
          pub: true,
          date: '2020/04/16',
          title_ja: 'スポンサー企業の公開',
          title_en: 'Introduction of Sponsor',
          detaile_ja: 'エキサイト(株)様',
          detaile_en: 'Excite Japan Co., Ltd.'
        },
        {
          pub: true,
          date: '2020/04/16',
          title_ja: 'サポーター企業の追加',
          title_en: 'New Suportors',
          detaile_ja:
            '(株)高専キャリア教育研究所様、(株)アカデミックギャングスター様',
          detaile_en: 'Kosen Career Co., Ltd., Academic Gangstar Co., Ltd.'
        },
        {
          pub: true,
          date: '2020/04/16',
          title_ja: '審査員(Judges)ページの公開',
          title_en: 'Add Judges page',
          detaile_ja: '審査員およびメンターの方々の紹介をしております。',
          detaile_en: 'Introduction of the judges and mentors (Japanese Only)',
          link: '/judges'
        },
        {
          pub: true,
          date: '2020/04/17',
          title_ja: '🌸🌸🌸 オンコンがスタートしました！🌸🌸🌸',
          title_en: '🌸🌸🌸 The contest has started！🌸🌸🌸',
          detaile_ja:
            '学生の応募を締め切りました。応募者数は前回の倍近くとなる107名！これから1週間頑張りましょう！',
          detaile_en:
            "The number of applicants was 107, nearly double the previous contest! Let's work hard for the week ahead!"
        }
      ]
    }
  },
  computed: {
    latestNews() {
      return [...this.news_list].reverse()
    }
  },
  head() {
    return {
      title: 'News',
      titleTemplate: '%s - ONLINE INTERN CONTEST 2020 #2'
    }
  }
}
</script>
<style lang="scss" scoped>
.wrapper {
  min-height: calc(100vh - 500px);
  @include flex(
    $wrap: nowrap,
    $justifyContent: space-between,
    $alignItems: flex-start
  );
}

.news_message {
  margin-bottom: 32px;
  font-size: 2rem;
}

.news_list {
  width: 70%;
  margin-right: 24px;
}

.news {
  position: relative;
  margin-bottom: 12px;
  background-color: $white;
  padding: 12px 24px;
  width: 100%;
  &::before {
    content: '';
    @include absolute($top: 0, $left: 0);
    display: block;
    width: 6px;
    height: 100%;
    background-color: $link;
  }
}

.news_wrapper {
  @include flex(
    $wrap: nowrap,
    $justifyContent: space-between,
    $alignItems: baseline
  );
  .title {
    font-size: 2rem;
  }
  .date {
    font-size: 1.5rem;
    color: $gray-txt;
    flex-shrink: 0;
    margin-left: 4px;
    display: block;
    text-decoration: none;
  }
}

.news_detaile {
  margin-top: 4px;
  font-size: 1.5rem;
  color: $gray-txt;
}

.twitter_timeline {
  flex-shrink: 0;
}

@media screen and (max-width: $md) {
  .news_message {
    font-size: 1.8rem;
  }
  .twitter_timeline {
    width: 320px;
  }
}
@media screen and (max-width: $tb) {
  .news_message {
    font-size: 1.6rem;
  }
  .wrapper {
    display: block;
  }
  .news_list {
    width: 100%;
  }
  .news_wrapper {
    .title {
      font-size: 1.7rem;
    }
    .date {
      font-size: 1.4rem;
    }
  }
  .news_detaile {
    font-size: 1.45rem;
  }
  .twitter_timeline {
    margin-top: 48px;
    width: 100%;
    text-align: center;
  }
}
</style>
