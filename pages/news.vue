<template lang="pug">
  .news_vue
    HeaderMenu()
    SubPageTopTitle(:title="'News'")
    .container
      .news_message  {{ $t('news.message') }}
      .wrapper
        .news_list
          .news(v-for="(news, news_key) in latestNews " :key="`news_${news_key}`" v-if="news.pub")
              .news_wrapper
                a.title(v-if="news.link" :href="news.link") {{news.title_ja}}
                .title(v-else) {{news.title_ja}}
                .date {{news.date}}
              .news_detaile {{news.detaile_ja}}
        //- .news_list(v-else)
        //-   .news(v-for="(news, news_key) in latestNews " :key="`news_${news_key}`" v-if="news.pub")
        //-       .news_wrapper
        //-         a.title(v-if="news.link" :href="news.link") {{news.title_en}}
        //-         .title(v-else) {{news.title_en}}
        //-         .date {{news.date}}
        //-       .news_detaile {{news.detaile_en}}
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
          date: '2020/04/24',
          title_ja: 'オンコン公式Webサイトを公開しました。',
          title_en: 'ONCON Official Website Was Launched.'
        },
        {
          pub: true,
          date: '2020/04/25',
          title_ja: 'noteを公開しました！',
          // title_en: 'Report Published in Kosen Magazine',
          detaile_ja: 'オンコンの詳細をわかりやすくまとめております！',
          // detaile_en: 'Report from a previous participant (Japanese Only)',
          link: 'https://note.com/prossell2019/n/n51f4bd489eb4'
        },
        {
          pub: true,
          date: '2020/04/26',
          title_ja: 'サポーター企業の公開',
          detaile_ja: '(株)高専キャリア教育研究所 様'
        },
        {
          pub: true,
          date: '2020/04/26',
          title_ja: '審査員(Judges)ページの公開',
          detaile_ja: '審査員およびメンターの方々の紹介をしております。',
          link: '/judges'
        },
        {
          pub: true,
          date: '2020/04/27',
          title_ja: 'サポーター企業の追加',
          detaile_ja: '(株)アカデミックギャングスター 様'
        },
        {
          pub: true,
          date: '2020/04/27',
          title_ja: '審査員(メンター)の追加',
          detaile_ja: '中川卓也 様'
        },
        {
          pub: true,
          date: '2020/04/28',
          title_ja: '審査員の追加',
          detaile_ja: '西村真陽 様，山根弘成 様'
        },
        {
          pub: true,
          date: '2020/04/30',
          title_ja: '審査員の追加',
          detaile_ja: '齊藤義明 様'
        },
        {
          pub: true,
          date: '2020/05/01',
          title_ja: '🎏🎏🎏 オンコンがスタートしました！🎏🎏🎏',
          detaile_ja:
            '学生の応募を締め切りました。22チーム110名でこれから1週間頑張りましょう！！！'
        },
        {
          pub: true,
          date: '2020/05/01',
          title_ja: 'サポーター企業の追加',
          detaile_ja: '(株)DeNA 様'
        },
        {
          pub: true,
          date: '2020/05/06',
          title_ja: 'Final Pitchの見学者募集を開始しました。',
          detaile_ja: '申し込みページへ移動します。（終了しました。）',
          link: '/awardCeremony'
        },
        {
          pub: true,
          date: '2020/05/07',
          title_ja: '最終発表チームの紹介！（note）',
          detaile_ja: '翌日の最終発表に出場するチームを紹介します！',
          link: 'https://note.com/prossell2019/n/nfc21159aae61'
        },
        {
          pub: true,
          date: '2020/05/08',
          title_ja: 'オンコンが無事終了しました！（結果はnoteへ）',
          detaile_ja: '参加者のみなさん！1週間お疲れ様でした！！！',
          link: 'https://note.com/prossell2019/n/n1c3a086b67dc'
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
      titleTemplate: '%s - ONLINE INTERN CONTEST 2020 #3'
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
