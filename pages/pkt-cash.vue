<template>
  <div class="v-cash">
    <section class="v-header-section">
      <SpotAInternal 
      :title="this.$t('pkt_cash.cash_title')"
      :text="this.$t('pkt_cash.cash_text')"
       />
    </section>
    <!-- <section class="v-analytics-section">
      <div class="c-analytics">
        <div class="container">
          <div class="c-analytics_data orange_bg">
            <p class="c-analytics_data__value">{{ already_mined | displayed_stats_data | commafy }}</p>
            <hr />
            <h3 class="c-analytics_data__title">Coins Mined</h3>
          </div>
          <div class="c-analytics_data blue_bg">
            <p class="c-analytics_data__value">6,000,000,000</p>
            <hr />
            <h3 class="c-analytics_data__title">Max Supply</h3>
          </div>
          <div class="c-analytics_data green_bg">
            <p class="c-analytics_data__value">60 sec</p>
            <hr />
            <h3 class="c-analytics_data__title">Blocktime</h3>
          </div>
        </div>
      </div>
    </section> -->
    <section class="v-simple-section">
      <SimpleText :list="simple_block" />
    </section>
    <section class="v-chess-section">
      <div class="container">
        <h2>{{ $t("pkt_cash.cash_chess_title") }}</h2>
      </div>
      <BlocksChessCommon :list="chess_list" />
    </section>
    <section class="v-index-section">
      <JoinCommunity />
    </section>
  </div>
</template>

<script>
import SpotAInternal from "~/components/Common/SpotAInternal";
import SimpleText from "~/components/Common/SimpleText";
import BlocksChessCommon from "~/components/Common/BlocksChessCommon";
import JoinCommunity from "~/components/Common/JoinCommunity";
//import { mapFields } from "vuex-map-fields";
export default {
  components: {
    SpotAInternal,
    SimpleText,
    BlocksChessCommon,
    JoinCommunity
  },
  // computed: {
  //   ...mapFields("pkt-analytics", [
  //     "already_mined",
  //   ])
  // },
  data() {
    return {
      //timeout: null,
      simple_block: [
        {
          single_title: this.$t("pkt_cash.cash_simple_title"),
          single_text: this.$t("pkt_cash.cash_simple_text"),
        }
      ],
      chess_list: [
        {
          text_direction: "text_left",
          single_title: this.$t("pkt_cash.cash_chess_title_1"),
          single_descr: this.$t("pkt_cash.cash_chess_descr_1"),
          single_url: "https://play.google.com/store/apps/details?id=co.anode.anodium.playstore",
          single_link: this.$t("common.learn_more"),
          external: true,
          single_img: "/img/pkt-cash-1.webp",
        },
        {
          text_direction: "text_right",
          single_title: this.$t("pkt_cash.cash_chess_title_2"),
          single_descr: this.$t("pkt_cash.cash_chess_descr_2"),
          single_url: "https://docs.pkt.cash/en/latest/cjdns_websites/",
          external: true,
          single_link: this.$t("common.learn_more"),
          single_img: "/img/pkt-cash-2.webp",
        },
        {
          text_direction: "text_left",
          single_title: this.$t("pkt_cash.cash_chess_title_3"),
          single_descr: this.$t("pkt_cash.cash_chess_descr_3"),
          single_url: "https://pkt.cash/PacketCrypt-2020-09-04.pdf",
          external: true,
          single_link: this.$t("header_new.dev_yellowpaper"),
          single_img: "/img/pkt-cash-3.webp",
        },
        {
          text_direction: "text_right",
          single_title: this.$t("pkt_cash.cash_chess_title_4"),
          single_descr: this.$t("pkt_cash.cash_chess_descr_4"),
          single_url: "https://pkt.cash/PKT_Network_v1.0_2021.02.01.pdf",
          external: true,
          single_link: this.$t("common.learn_more"),
          single_img: "/img/pkt-cash-4.webp",
        },
        {
          text_direction: "text_left",
          single_title: this.$t("pkt_cash.cash_chess_title_5"),
          single_descr: this.$t("pkt_cash.cash_chess_descr_5"),
          single_url: "https://pkt.cash/PKT_Network_v1.0_2021.02.01.pdf",
          external: true,
          single_link: this.$t("header.whitepaper"),
          single_img: "/img/pkt-cash-1.webp",
        }
      ]
    };
  },
  // filters: {
  //   displayed_pkt_price(value) {
  //     if (value > 0.01)
  //       return (Number(value)).toFixed(2);
  //     return (Number(value)).toFixed(4);
  //   },
  //   displayed_stats_data(value) {
  //     return (Number(value) / 0x40000000).toFixed(0);
  //   },
  //   displayed_enc(value) {
  //     return Math.round(value * 100) / 100;
  //   },
  //   displayed_kb(value) {
  //     if (value > 1 << 30)
  //       return `${parseFloat(value / 1073741824).toFixed(2)} Gb/s`;
  //     if (value > 1 << 20)
  //       return `${parseFloat(value / 1048576).toFixed(2)} Mb/s`;
  //     if (value > 1 << 10)
  //       return `${parseFloat(value / 1048576).toFixed(2)} Kb/s`;
  //     return `${value} bits/s`;
  //   },
  //   commafy(value) {
  //     return ("" + value).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
  //   },
  // },
  // mounted() {
  //   if (process.client) {
  //     this.timeout = setInterval(
  //       () => this.$store.dispatch("pkt-analytics/update_data"),
  //       60 * 1000
  //     );
  //   }
  // },
  // beforeDestroy() {
  //   clearInterval(this.timeout);
  //   this.timeout = null;
  // },
  // async middleware({ store }) {
  //   await store.dispatch('pkt-analytics/load')
  // },
  // async mounted() {
  //   await this.$store.dispatch('pkt-analytics/load')
  // },
  head() {
    return {
      title: "PKT Cash is currency for bandwidth | PKT Cash",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'PKT Cash is a proof-of-work mined community coin. Miners are paid in PKT when running PacketCrypt, which powers the physical infrastructure of the PKT Network. The PKT cryptocurrency is designed as payment rails for microtransactions with near-instant settlement and near-zero gas fees.'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'PKT Cash is currency for bandwidth | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'PKT Cash is a proof-of-work mined community coin. Miners are paid in PKT when running PacketCrypt, which powers the physical infrastructure of the PKT Network. The PKT cryptocurrency is designed as payment rails for microtransactions with near-instant settlement and near-zero gas fees.'
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
.v-cash {
  background-color:$black_blue;
  position:relative;
  background-image:url(/img/pkt-cash-top.webp);
  background-size:rem(800);
  background-position:top right;
  background-repeat:no-repeat;
  @include for-width(-desktop-lg) {
    background-size:rem(740);
  }
  @include for-width(-desktop-medium-default) {
    background-size:rem(650);
  }
  @include for-width(-tablet) {
    background-position:top -275px right -150px;
  }
  @include for-width(-small-lg) {
    background-position:top -225px right -200px;
  }
  &:before {
    content:'';
    background-image:url(/img/pkt-cash-bg-1.webp);
    position:absolute;
    top:7%;
    right:0;
    width:90%;
    height:85%;
    background-position:right top;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
  }
  &:after {
    content:'';
    background-image:url(/img/pkt-cash-bg-2.webp);
    position:absolute;
    bottom:0;
    left:0;
    width:80%;
    height:70%;
    background-position:left -50% bottom;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
  }
  & > section {
    z-index:3;
    position:relative;
  }
  & .c-spot-a-internal {
    @include for-width(-small-lg) {
      padding:rem(120) 0 rem(70);
    }
  }
  & .v-simple-section {
    & .c-common-simple {
      & .container {
        padding: rem(54) rem(115) rem(60);
        @include for-width(-laptop) {
          padding: rem(35) rem(100) rem(40);
        }
        @include for-width(-tablet) {
          padding: rem(35) rem(50) rem(40);
        }
        @include for-width(-small-lg) {
          padding: rem(35);
        }
      }
    }
  }
  & .v-analytics-section {
    & .c-analytics {
      padding-bottom:rem(125);
      @include for-width(-small-lg) {
        padding-bottom:0;
      }
      & .container {
        @extend %df;
        @extend %jcsb;
        @extend %fw;
        @include for-width(-small-lg) {
          display:block;
          padding-bottom:rem(90);
        }
      }
      &_data {
        width:32%;
        border-radius: rem(20);
        padding:rem(30);
        @extend %t-center;
        @include for-width(-desktop-med) {
          padding:rem(30) rem(10);
        }
        @include for-width(-tablet) {
          width:100%;
          margin-bottom:rem(20);
        }
        @include for-width(-small-lg) {
          padding:rem(20);
        }
        &__value {
          color:$black_blue;
          @extend %h2-common;
          @include for-width(-laptop_small) {
            font-size: rem(36);
            line-height: rem(46);
          }
          @include for-width(-small-lg) {
            font-size: rem(30);
            line-height: rem(36);
          }
        }
        & hr {
          background-color:$black_blue;
          border:0;
          width:rem(120);
          height:rem(1);
          padding:0;
          margin:rem(20) auto rem(22);
          @include for-width(-small-lg) {
            display:none;
          }
        }
        &__title {
          color:$black_blue;
          font-size: rem(16);
          line-height: rem(24);
          @extend %inter_semibold;
        }
      }
    }
  }
  & .v-chess-section {
    padding-top:rem(175);
    @include for-width(-tablet-lg) {
      padding-top:rem(125);
    }
    @include for-width(-small-lg) {
      padding-top:rem(100);
    }
    & h2 {
      @extend %h2-common;
      @extend %t-center;
      margin-bottom:rem(100);
      @include for-width(-small-lg) {
        margin-bottom:rem(85);
        text-align:left;
        max-width:rem(220);
      }
    }
    & .c-chess-block {
      & .text_left .c-chess-block_inner_single {
        padding-right:0;
        @include for-width(-small-lg) {
          text-wrap: pretty;
        }
      }
      & .text_right .c-chess-block_inner_single {
        padding-left:0;
        @include for-width(-small-lg) {
          text-wrap: pretty;
        }
      }
      &_inner_single_img {
        img {
          border-radius:rem(20);
        }
      }
      & .c-common-button {
        min-width:rem(175);
        width:auto;
      }
    }
  }
}
</style>