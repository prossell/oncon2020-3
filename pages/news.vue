<template lang="pug">
  .news_vue
    HeaderMenu()
    SubPageTopTitle(:title="'News'")
    .container
      .news_message  {{ $t('news.message') }}
      .wrapper
        .news_list
          .news(v-for="(news, news_key) in latestNews" :key="`news_${news_key}`" v-if="news.pub")
              .news_wrapper
                a.title(v-if="news.link" :href="news.link") {{news.title}}
                .title(v-else ) {{news.title}}
                .date {{news.date}}
              .news_detaile {{news.detaile}}
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
          title: 'オンコン公式Webサイトを公開しました。',
          title_en: 'ONCON official website is disclosed.'
        },
        {
          pub: true,
          date: '2020/04/08',
          title: '高専マガジンに掲載されました！',
          detaile: '前回の参加レポートをまとめております',
          title_en: 'Published in Kosen Magazine',
          detaile_en: 'Previous participation report',
          link: 'https://kosen-magazine.com/online-intern-contest-2020-report/'
        }
      ]
    }
  },
  computed: {
    latestNews() {
      return [...this.news_list].reverse()
    },
    change_lang() {
      let lang = ''
      if (this.$i18n.locale === 'en') {
        lang = 'en'
      }
      return lang
    }
  },
  head() {
    return {
      title: 'News',
      titleTemplate: '%s - ONLINE INTERN CONTEST 2020'
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
