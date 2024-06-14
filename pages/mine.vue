<template>
  <div class="v-mining">
    <section class="v-header-section">
      <SpotAInternal
      :title="this.$t('mine.mine_title')"
      :text="this.$t('mine.mine_text')"
      :button_1="this.$t('mine.mine_button_1')"
      :button_2="this.$t('mine.mine_button_2')"
      :button_3="this.$t('mine.mine_button_3')"
      button_1_link="/wallet"
      button_2_link="https://pkt.watch/minr/"
      button_3_link="https://docs.pkt.cash/"
      button_2_target="_blank"
      button_3_target="_blank" />
    </section>
    <!-- <section class="v-analytics-section">
      <AnalyticsData />
    </section> -->
    <section class="v-chess-section">
      <BlocksChessCommon :list="chess_list" />
    </section>
    <section class="v-block-links-section">
      <div class="container">
        <div class="v-block-links-section__inner">
          <div class="v-block-links-section__single dark_blue_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("mine.mine_links_title_1") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("mine.mine_links_text_1") }}</p></div>
            <!-- <nuxt-link class="c-common-button c-common-button__bordered c-common-button__dark_blue" to="/setup">
              <span>Get started</span>
            </nuxt-link> -->
            <a href="https://docs.pkt.cash/en/latest/pktd/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("mine.mine_links_link_1") }}</span></a>
          </div>
          <div class="v-block-links-section__single green_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("mine.mine_links_title_2") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("mine.mine_links_text_2") }}</p></div>
            <a href="https://packetscan.io/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("mine.mine_links_link_2") }}</span></a>
          </div>
        </div>
        <div class="v-block-links-section__inner">
          <div class="v-block-links-section__single orange_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("mine.mine_links_title_3") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("mine.mine_links_text_3") }}</p></div>
            <a href="https://docs.pkt.cash/en/latest/mining/pool_setup_guide/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("mine.mine_links_link_3") }}</span></a>
          </div>
          <div class="v-block-links-section__single blue_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("mine.mine_links_title_4") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("mine.mine_links_text_4") }}</p></div>
            <a href="https://docs.pkt.cash/en/latest/mining/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("mine.mine_links_link_4") }}</span></a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import SpotAInternal from "~/components/Common/SpotAInternal";
// import AnalyticsData from "~/components/Mine/AnalyticsData";
import BlocksChessCommon from "~/components/Common/BlocksChessCommon";
export default {
  components: {
    SpotAInternal,
    // AnalyticsData,
    BlocksChessCommon
  },
  data() {
    return {
      chess_list: [
        {
          text_direction: "text_right",
          single_title: this.$t("mine.mine_chess_title_1"),
          single_subtitle: this.$t("mine.mine_chess_subtitle_1"),
          single_descr: this.$t("mine.mine_chess_descr_1"),
          single_url: "/pkt-cash",
          external: false,
          single_link: this.$t("common.learn_more"),
          single_img: "/img/mine/mine-1.webp",
        },
        {
          text_direction: "text_left",
          single_title: this.$t("mine.mine_chess_title_2"),
          single_subtitle: this.$t("mine.mine_chess_subtitle_2"),
          single_descr: this.$t("mine.mine_chess_descr_2"),
          single_url: "https://docs.pkt.cash/en/latest/",
          external: true,
          single_link: this.$t("mine.mine_links_link_4"),
          single_img: "/img/mine/mine-2.webp",
        }
      ]
    };
  },
  head() {
    return {
      title: "Mine | PKT Cash",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'The PKT Network is powered by miners who run PacketCrypt, the world’s first and only bandwidth-hard, proof of work, mining algorithm. PacketCrypt economically incentivizes miners to collaborate, operate and grow the fully decentralized PKT Network. Mining has never been easier. Get started today.'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Mine | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'The PKT Network is powered by miners who run PacketCrypt, the world’s first and only bandwidth-hard, proof of work, mining algorithm. PacketCrypt economically incentivizes miners to collaborate, operate and grow the fully decentralized PKT Network. Mining has never been easier. Get started today.'
        }
      ],
      link: [
        {
          rel: 'canonical',
          href: 'https://pkt.cash' + this.$route.path
        }
      ]
    };
  },
};
</script>
<style lang="scss">
.v-mining {
  background-color:$black_blue;
  position:relative;
  &:before {
    content:'';
    background-image:url(/img/mine/mine-bg.webp);
    position:absolute;
    bottom:0;
    right:0;
    width:80%;
    height:70%;
    background-position:left center;
    background-size:cover;
    background-repeat:no-repeat;
    z-index:1;
  }
  &:after {
    content:'';
    background-image:url(/img/mine-top-asset.webp);
    position:absolute;
    top:0;
    right:0;
    width:55%;
    height:55%;
    background-position:right top;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
    @include for-width(-desktop-medium) {
      width:60%;
      height:60%;
    }
    @include for-width(-small-lg) {
      width:100%;
      height:rem(800);
      background-size:cover;
      background-position:right -250px top -150px;
    }
  }
  & > section {
    z-index:3;
    position:relative;
  }
  .v-header-section {
    .c-spot-a-internal {
      @include for-width(-small-lg) {
        padding:rem(125) 0 rem(100);
      }
      &__title {
        max-width:rem(475);
        @include for-width(-small-lg) {
          max-width:rem(200);
        }
      }
      &__links {
        @include for-width(-small-lg) {
          margin-top:rem(35);
        }
        & .c-common-button {
          @include for-width(-small-lg) {
            width:47%;
          }
        }
        & .c-common-button__filled {
          @include for-width(-small-lg) {
            width:100%;
            margin-bottom:rem(20);
          }
        }
      }
    }
  }
  .v-chess-section {
    & .text_right {
      & .c-chess-block_inner_single_title {
        padding-right:rem(50);
        @include for-width(-small-lg) {
          padding-right:0;
        }
      }
    }
  }
  .v-block-links-section {
    padding:rem(150) 0;
    @include for-width(-small-lg) {
      padding:rem(110) 0 rem(80);
    }
    &__inner {
      @extend %df;
      @extend %jcsb;
      @extend %fw;
      padding-bottom:3%;
      &:last-child {
        padding-bottom:0;
      }
      @include for-width(-small-lg) {
        display:block;
        padding-bottom:0;
      }
    }
    &__single {
      width:48.5%;
      border-radius:rem(20);
      padding:rem(30) rem(40);
      @extend %df;
      @extend %jcsb;
      @extend %fdc;
      @extend %ais;
      @include for-width(-laptop) {
        padding:rem(25) rem(30);
      }
      @include for-width(-small-lg) {
        width:100%;
        padding:rem(20) rem(30);
        margin-bottom:rem(20);
      }
    }
    &__title {
      font-size: rem(40);
      line-height: rem(50);
      color:$black_blue;
      @extend %inter_semibold;
      @include for-width(-laptop) {
        font-size: rem(34);
        line-height: rem(44);
      }
      @include for-width(-small-lg) {
        font-size: rem(30);
        line-height: rem(36);
      }
    }
    &__descr {
      @extend %p-big-common;
      color:$black_blue;
      padding:rem(12) 0 rem(65);
      @include for-width(-small-lg) {
        font-size: rem(16);
        line-height: rem(24);
      }
    }
  }
}
</style>