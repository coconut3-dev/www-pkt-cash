<template>
  <div class="v-resources">
    <section class="v-header-section">
      <HeaderInternal
        :title="this.$t('resources.heading_title')" 
        :subtitle="this.$t('resources.heading_subtitle')" 
        :button_1="this.$t('resources.heading_button_1')" 
        :button_2="this.$t('resources.heading_button_2')"
        button_1_link="#docs"
        button_2_link="#videos" 
        :button_3="this.$t('resources.heading_button_3')" 
        :button_4="this.$t('resources.heading_button_4')"
        button_3_link="https://pkt.cash/PKT_Network_v1.0_2021.02.01.pdf"
        button_4_link="https://docsend.com/view/ayf5d3tz5rymn8fv"
        :button_5="this.$t('resources.heading_button_5')" 
        :button_6="this.$t('resources.heading_button_6')"
        :button_5_link="localePath('getpkt')"
        :button_6_link="localePath('wpkt')"
        is_resources
        />
    </section>
    <section class="v-resources-section v-resources-section__whitepapers">
      <div class="container">
        <div class="v-resources-section__left">
          <h2 class="v-resources-section__title_small">{{ $t("resources.whitepapers_heading") }}</h2>
          <p class="v-resources-section__text">{{ $t("resources.whitepapers_text_1") }}</p>
          <a href="https://pkt.cash/PKT_Network_v1.0_2021.02.01.pdf" target="_blank" class="v-resources-section__button"><span>{{ $t("resources.whitepapers_button_1") }}</span></a>
          <p class="v-resources-section__text">{{ $t("resources.whitepapers_text_2") }}</p>
          <a href="https://pkt.cash/PacketCrypt-2020-09-04.pdf" target="_blank" class="v-resources-section__button"><span>{{ $t("resources.whitepapers_button_2") }}</span></a>
        </div>
      </div>
    </section>
    <section class="v-resources-section v-resources-section__documentation" id="docs">
      <div class="container">
        <div class="v-resources-section__left">
          <h2 class="v-resources-section__title_small">{{ $t("resources.documentation_title") }}</h2>
          <div class="v-resources-section__links">
            <a href="https://docs.pkt.cash/en/latest/PKT_FAQ/" target="_blank" class="v-resources-section__button"><span>{{ $t("resources.documentation_cta_1") }}</span></a>
            <nuxt-link :to="localePath('mine')" class="v-resources-section__button"><span>{{ $t("resources.documentation_cta_2") }}</span></nuxt-link>
          </div>
          <div class="v-resources-section__links">
            <nuxt-link :to="localePath('wallet')" class="v-resources-section__button"><span>{{ $t("resources.documentation_cta_3") }}</span></nuxt-link>
            <a href="https://docs.pkt.cash/en/latest/mining/pool_setup_guide/" target="_blank" class="v-resources-section__button"><span>{{ $t("resources.documentation_cta_4") }}</span></a>
          </div>
          <div class="v-resources-section__links">
            <nuxt-link :to="localePath('getpkt')" class="v-resources-section__button"><span>{{ $t('resources.heading_button_5') }}</span></nuxt-link>
            <nuxt-link :to="localePath('wpkt')" class="v-resources-section__button"><span>{{ $t('resources.heading_button_6') }}</span></nuxt-link>
          </div>
        </div>
        <div class="v-resources-section__right">
          <img src="/img/resources-documentation.svg" alt="Documentation" />
        </div>
      </div>
    </section>
    <section class="v-resources-section v-resources-section__videos v-resources-section__videos_wrap" id="videos">
      <div class="container">
        <h2 class="v-resources-section__title">{{ $t('resources.video_title') }}</h2>
        <h4 class="v-resources-section__subtitle">{{ $t('resources.video_subtitle_1') }}</h4>
        <template>
          <div class="v-resources-section__videos">
            <VueSlickCarousel v-bind="settings">
              <div class="v-resources-section__videos_item" v-for="(item) of podcast_list">
                <a :href="'https://www.youtube.com/watch?v=' + item.url" target="_blank">
                  <!-- <img :src="'https://img.youtube.com/vi/' + item.url + '/maxresdefault.jpg'" :alt="item.title" class="v-resources-section__videos_item_preview" /> -->
                  <img :src="item.image_default" :alt="item.title" class="v-resources-section__videos_item_preview" />
                  <h5 class="v-resources-section__videos_item__title" v-html="item.title"></h5>
                </a>
              </div>
            </VueSlickCarousel>
          </div>
          <!-- <div v-for="(item) of podcast_list"><Video :v-show="item.video" :url="item.url" @close-modal="item.video = false" /></div> -->
        </template>
        <h4 class="v-resources-section__subtitle">{{ $t('resources.video_subtitle_2') }}</h4>
        <template>
          <div class="v-resources-section__videos">
            <VueSlickCarousel v-bind="settings">
              <div class="v-resources-section__videos_item" v-for="(item) of howto_list">
                <a :href="'https://www.youtube.com/watch?v=' + item.url" target="_blank">
                  <!-- <img :src="'https://img.youtube.com/vi/' + item.url + '/maxresdefault.jpg'" :alt="item.title" class="v-resources-section__videos_item_preview" /> -->
                  <img :src="item.image_default" :alt="item.title" class="v-resources-section__videos_item_preview" />
                  <h5 class="v-resources-section__videos_item__title" v-html="item.title"></h5>
                </a>
              </div>
            </VueSlickCarousel>
          </div>
          <!-- <div v-for="(item) of howto_list"><Video :v-show="item.video" :url="item.url" @close-modal="item.video = false" /></div> -->
        </template>
        <h4 class="v-resources-section__subtitle">{{ $t('resources.video_subtitle_3') }}</h4>
        <template>
          <div class="v-resources-section__videos">
            <VueSlickCarousel v-bind="settings">
              <div class="v-resources-section__videos_item" v-for="(item) of popular_list">
                <a :href="'https://www.youtube.com/watch?v=' + item.url" target="_blank">
                  <!-- <img :src="'https://img.youtube.com/vi/' + item.url + '/maxresdefault.jpg'" :alt="item.title" class="v-resources-section__videos_item_preview" /> -->
                  <img :src="item.image_default" :alt="item.title" class="v-resources-section__videos_item_preview" />
                  <h5 class="v-resources-section__videos_item__title" v-html="item.title"></h5>
                </a>
              </div>
            </VueSlickCarousel>
          </div>
          <!-- <div v-for="(item) of popular_list"><Video :v-show="item.video" :url="item.url" @close-modal="item.video = false" /></div> -->
        </template>
      </div>
    </section>
  </div>
</template>

<script>
import HeaderInternal from "~/components/Base/HeaderInternal";
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';
import Video from '~/components/Resources/Video.vue';
export default {
  components: {
    HeaderInternal,
    VueSlickCarousel,
    Video
  },
  head() {
    return {
      title: "Resources - PKT",
      meta: [{ hid: "description", name: "description", content: "Documentation, resources and video content about the PKT Network." }],
      link: [
        {
          rel: 'canonical',
          href: 'https://pkt.cash' + this.$route.path
        }
      ]
    };
  },
  data() {
    return {
      settings: {
        arrows: true,
        dots: false,
        infinite: true,
        slidesToShow: 3,
        slidesToScroll: 1,
        responsive: [
          {
            breakpoint: 992,
            settings: {
              slidesToShow: 2,
            }
          },
          {
            breakpoint: 767,
            settings: {
              slidesToShow: 1,
            }
          },
        ]
      },
      podcast_list: [
        {
          url: "_EeWHeY-omQ",
          title: "PKT Podcast Episode 1:<br />What is PKT",
          video: "Video_1",
          image_default: "/img/resources-episode-1.jpeg"
        },
        {
          url: "tCBKBEtFmfw",
          title: "PKT Podcast Episode 2:<br />Token vs Koin",
          video: "Video_2",
          image_default: "/img/resources-episode-2.jpeg"
        },
        {
          url: "IBTjANISzM4",
          title: "PKT Podcast Episode 3:<br />PKT Wallet",
          video: "Video_3",
          image_default: "/img/resources-episode-3.jpeg"
        },
        {
          url: "CFxgIKFL0DM",
          title: "PKT Podcast Episode 5:<br />Talking about PKT With Vishnu Seesahai (WPKT Dev)",
          video: "Video_4",
          image_default: "/img/resources-episode-5.jpeg"
        }, 
      ],
      howto_list: [
        {
          url: "OAVtdfmf3Cs",
          title: "Import PKT Wallet from Seed",
          image_default: "/img/resources-howto-1.jpeg"
        },
        {
          url: "kTtZeI_b5jM",
          title: "PKT Zulu Wallet Installation for MacOS",
          image_default: "/img/resources-howto-2.jpeg"
        },
        {
          url: "Snbw3WbiLJQ",
          title: "How to Mine PKT with a Docker Image",
          image_default: "/img/resources-howto-3.jpeg"
        },
      ],
      popular_list : [
        {
          url: "MckyQmnl35A",
          title: "PKT Road Map Premiere + AMA",
          image_default: "/img/resources-popular-1.jpeg"
        },
        {
          url: "5pt0QMjPk_Q",
          title: "PKT Cash Explained",
          image_default: "/img/resources-popular-2.jpeg"
        },
        {
          url: "8wT9lhNTQQk",
          title: "PKT Network is Connecting The Next Billion People To The Internet",
          image_default: "/img/resources-popular-3.jpeg"
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.v-resources {
  // Top section
  & .v-header-section {
    & .c-internal-header {
      @include for-width(+desktop-er) {
        padding-top:rem(50);
      }
      @include for-width(-small-lg) {
        height:100vh;
      }
      &__sub-title {
        max-width:55%;
        margin:rem(25) auto rem(35);
        @include for-width(+desktop-er) {
          margin:0 auto rem(10);
        }
        @include for-width(-desktop-lg) {
          max-width:50%;
        }
        @include for-width(-small-lg) {
          max-width:95%;
          margin:rem(15) auto rem(25);
          font-size: rem(20);
          line-height:rem(32);
        }
      }
      &__title {
        padding-top:rem(35);
      }
      &__links {
        @include for-width(+desktop-er) {
          margin-top:rem(30);
        }
        @include for-width(-desktop-lg) {
          margin-top:rem(35);
        }
        @include for-width(-small-lg) {
          margin-bottom:0;
          margin-top:rem(25);
        }
        & .button_new {
          @include for-width(-small-lg) {
            padding:rem(10) 0;
            width:48%;
            margin:0;
            display:block;
          }
        }
      }
      & .desktop_view {
        @include for-width(-desktop-lg) {
          margin-top:rem(45);
        }
      }
    }
  }
  // Common
  &-section {
    padding:rem(100) 0;
    @include for-width(-desktop-lg) {
      padding:rem(75) 0;
    }
    @include for-width(-laptop) {
      padding:rem(50) 0;
    }
    & .container {
      @extend %container_new;
      @include for-width(-tablet) {
        max-width:100%;
        width:100%;
        padding:0 rem(25);
      }
      @include for-width(-small-lg) {
        padding:0 rem(20);
      }
    }
    &__left {
      @extend %t-left;
      width:50%;
      @include for-width(-tablet) {
        width:100%;
        text-align:center;
      }
    }
    &__right {
      @extend %t-right;
      width:50%;
      @include for-width(-tablet) {
        width:100%;
        text-align:center;
      }
    }
    &__title {
      @extend %heading-mlarge;
      @extend %heading-gradient-dark;
      margin-bottom:rem(50);
      @include for-width(-laptop) {
        margin-bottom:rem(25);
      }
    }
    &__title_small {
      @extend %heading_internal;
      @extend %heading-gradient-dark;
      margin-bottom:rem(35);
      @include for-width(-laptop) {
        margin-bottom:rem(25);
      }
      @include for-width(-small-lg) {
        font-size:rem(36);
        line-height:rem(42);
      }
    }
    &__subtitle {
      @extend %heading-super-small;
      margin-bottom:rem(50);
      @include for-width(-laptop) {
        margin-bottom:rem(25);
      }
    }
    &__text {
      @extend %pn;
      margin:0 auto rem(35);
    }
    &__links {
      @extend %df;
      @extend %aic;
      @extend %jcs;
    }
    &__button {
      @extend %btn-new;
      @extend %btn_blue_new;
      padding:rem(15) rem(50);
      display:inline-block;
      width:auto;
      @include for-width(-laptop) {
        padding:rem(12) rem(35);
      }
      @include for-width(-small-lg) {
        padding:rem(10) rem(25);
      }
    }
    &__videos {
      margin-bottom:rem(15);
      & .slick-arrow {
        background-repeat:no-repeat;
        background-size:contain;
        background-position:center;
        width: rem(30);
        height: rem(30);
        z-index:99;
        @include for-width(-laptop) {
          width: rem(20);
          height: rem(20);
        }
        @include for-width(-small-lg) {
          width: rem(18);
          height: rem(18);
        }
        &:before {
          display:none;
        }
      }
      & .slick-track {
        display: flex !important;
      }
      & .slick-slide {
        height: auto;
        & > div {
          height:100%;
          padding:0 rem(10) rem(25);
          @include for-width(-laptop) {
            padding:rem(10);
          }
          @include for-width(-tablet) {
            padding:rem(5);
          }
        }
      }
      & .slick-prev {
        background-image:url(/img/slick-arrow-prev.svg);
        left:-55px;
        @include for-width(-laptop) {
          left:-25px;
        }
        @include for-width(-tablet) {
          left:-15px;
        }
        @include for-width(-small-lg) {
          left:-10px;
        }
      }
      & .slick-next {
        background-image:url(/img/slick-arrow-next.svg);
        right:-55px;
        @include for-width(-laptop) {
          right:-25px;
        }
        @include for-width(-tablet) {
          right:-15px;
        }
        @include for-width(-small-lg) {
          right:-10px;
        }
      }
    }
    &__videos_item {
      background:$white;
      box-shadow: 0px 4px 12px rgba(0, 0, 0, 0);
      -webkit-transition: all .25s ease-out;
      -moz-transition: all .25s ease-out;
      -o-transition: all .25s ease-out;
      transition: all .25s ease-out;
      padding:rem(35) rem(20);
      height:100%;
      @include for-width(-laptop) {
        box-shadow: 0px 2px 8px rgba(0, 0, 0, 0);
        padding:rem(15);
      }
      @include for-width(-tablet) {
        padding:rem(15) rem(10);
      }
      &:hover {
        background:$light_bg;
        box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.19);
        @include for-width(-laptop) {
          box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.19);
        }
      }
      &__title {
        @extend %heading-super-small;
        @extend %t-left;
        padding-top:rem(15);
        color:$black_new;
        @include for-width(-laptop) {
          padding-top:rem(10);
          font-size: rem(16);
          line-height:rem(24);
        }
      }
    }
  }
  // Sections
  &-section__whitepapers {
    background-color:$light_bg;
    background-image:url(/img/resources-whitepaper.png);
    background-repeat:no-repeat;
    background-size:40% auto;
    background-position:center right;
    @include for-width(+desktop-xxl) {
      background:$light_bg;
    }
    @include for-width(-small-lg) {
      background-position:bottom right;
      padding-bottom:rem(125);
      background-size:60% auto;
    }
    & .container {
      @extend %df;
      @extend %aic;
      @extend %jcsb;
      @include for-width(+desktop-xxl) {
        background-image:url(/img/resources-whitepaper.png);
        background-repeat:no-repeat;
        background-size:50% auto;
        background-position:center right;
      }
      @include for-width(-tablet) {
        display:block;
      }
    }
    & .v-resources-section__text {
      padding-right:rem(100);
      @include for-width(-laptop) {
        padding-right:rem(50);
        margin-bottom:rem(15);
      }
      @include for-width(-tablet) {
        padding-right:rem(175);
      }
      @include for-width(-small-lg) {
        padding-right:0;
      }
    }
    & .v-resources-section__button {
      margin-bottom:rem(45);
      @include for-width(-laptop) {
        margin-bottom:rem(25);
      }
    }
  }
  &-section__documentation {
    background-color: $dark_blue_new;
    & .container {
      @extend %df;
      @extend %aic;
      @extend %jcsb;
      @include for-width(-tablet) {
        display:block;
        text-align:center;
      }
    }
    & .v-resources-section__title_small {
      @extend %heading-gradient-light;
      margin-bottom:rem(65);
      @include for-width(-laptop) {
        margin-bottom:rem(35);
      }
    }
    & .v-resources-section__right {
      @extend %t-center;
      position:relative;
      & img {
        width:85%;
        margin-bottom:-100px;
        @include for-width(-desktop-lg) {
          margin-bottom:-75px;
        }
        @include for-width(-laptop) {
          margin-bottom:-50px;
          width:75%;
        }
        @include for-width(-tablet) {
          width:55%;
        }
        @include for-width(-small-lg) {
          width:65%;
        }
      }
    }
    & .v-resources-section__links {
      margin-bottom:rem(35);
      @include for-width(-laptop) {
        margin-bottom:rem(25);
      }
      @include for-width(-tablet) {
        justify-content: center;
      }
      & .v-resources-section__button {
        width:rem(225);
        @include for-width(-laptop) {
          width:rem(200);
        }
        &:nth-child(odd) {
          margin-right:rem(35);
          @include for-width(-laptop) {
            margin-right:rem(25);
          }
        }
      }
    }
  }
  &-section__videos_wrap {
    @include for-width(-desktop-medium) {
      padding:rem(115) 0 rem(100);
    }
  }
  &-section__videos {
    background-color: $white;
    @extend %t-center;
    @include for-width(-laptop) {
      padding-bottom:0;
    }
    & .v-resources-section__subtitle {
      background-color: #222450;
      color:$white;
      padding:rem(20);
      @include for-width(-laptop) {
        padding:rem(10);
      }
    }
  }
}
</style>
