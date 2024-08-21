<template>
  <div class="v-index">
    <section class="v-top-section">
      <div class="container">
        <h1 class="v-top-section__heading">{{ $t("home_new.top_heading_1") }} <br />{{ $t("home_new.top_heading_2") }}</h1>
        <p class="v-top-section__description">PKT is a media network built on Base and powered by the people. <br />Stake to earn PKT and get paid to power the network.</p>
        <div class="v-top-section__links">
          <a href="https://uniswap.org/" target="_blank" class="c-common-button c-common-button__filled">
            <span>Buy PKT</span>
          </a>
          <a href="https://pkt.cash/1ea983ba3453631d914755e7ad96840d/overview" target="_blank" class="c-common-button c-common-button__bordered">
            <span>Stake PKT</span>
          </a>
        </div>
      </div>
      <div class="v-top-section__solutions">
        <div class="container">
          <p>Built on Base and powered by the people.</p>
          <div class="v-top-section__solutions_carousel">
            <ImgBlock :list="solutions_img_list" />
          </div>
        </div>
      </div>
    </section>
    <section class="v-indexes-section">
      <div class="container">
        <h2 class="v-indexes-section__heading">{{ $t("home_new.indexes_1") }} <br />{{ $t("home_new.indexes_2") }}</h2>
        <div class="v-indexes-section__inner">
          <IndexHeader />
        </div>
      </div>
    </section>
    <section class="v-asymetrical-section">
      <div class="container">
        <div class="v-asymetrical-section__heading">
          <h2>A Next Gen Network</h2>
          <a href="https://docs.pkt.cash/utility" target="_blank" class="c-common-button c-common-button__filled">
            <span>{{ $t("common.learn_more") }}</span>
          </a>
        </div>
        <div class="v-asymetrical-section__inner">
          <BlockAsymmetrical :listFirst="asymetrical_block_list" :listSecond="asymetrical_block_list_second" />
        </div>
        <nuxt-link class="c-common-button c-common-button__filled mobile_only" to="/roadmap">
          <span>{{ $t("common.learn_more") }}</span>
        </nuxt-link>
      </div>
    </section>
    <section class="v-powering-section">
      <div class="container">
        <h2 class="v-powering-section__heading">The Three Pillars of PKT</h2>
        <div class="v-powering-section__inner">
          <CardsCommon :list="cards_list" />
        </div>
      </div>
    </section>
    <section class="v-chess-section">
      <BlocksChessCommon :list="blocks_list" />
    </section>
    <section class="v-index-section">
      <JoinCommunity />
    </section>
  </div>
</template>

<script>
import ImgBlock from "~/components/Common/ImgBlock";
import IndexHeader from "~/components/Home/IndexHeader";
import BlockAsymmetrical from "~/components/Common/BlockAsymmetrical";
import CardsCommon from "~/components/Home/CardsCommon";
import BlocksChessCommon from "~/components/Common/BlocksChessCommon";
import JoinCommunity from "~/components/Common/JoinCommunity";
export default {
  components: {
    ImgBlock,
    IndexHeader,
    BlockAsymmetrical,
    CardsCommon,
    BlocksChessCommon,
    JoinCommunity
  },
  data() {
    return {
      asymetrical_block_list: [
        {
          single_title: "Decentralized Physical Infrastructure",
          single_descr: "PKT is a globally accessible media network with no central infrastructure. Pkteers like you are economically incentivized to build the network.",
          color: "orange_dot"
        },
        {
          single_title: "Global Networking",
          single_descr: "All content is accessible globally peer-to-peer and through traditional browsers without geofencing.",
          color: "green_dot"
        }
      ],
      asymetrical_block_list_second: [
        {
          single_title: "Stake to Earn",
          single_descr: "Earn daily yields by staking PKT and assigning it to infrastructure that powers the network.",
          color: "green_dot"
        },
        {
          single_title: "Safe and Secure",
          single_descr: "The PKT Network backbone is supported by cjdns, which is a high speed, permissionless, encrypted mesh network.",
          color: "orange_dot"
        }
      ],
      blocks_list: [
        {
          text_direction: "text_right",
          single_title: "Governance",
          single_descr: "Twenty percent of all daily yields are allocated into a treasury that to fund the project roadmap. Every week the community elects a Network Steward who campaigns on how to allocate resources the available funds to the growth of the network.",
          single_url: "https://docs.pkt.cash/governance",
          single_link: this.$t("common.learn_more"),
          single_img: "/img/home/chess-1.webp",
          external: true
        },
        {
          text_direction: "text_left",
          single_title: this.$t("home_new.block_list_title_2"),
          single_descr: "PKT is now live on Base! Buy now from Uniswap. PKT will  relaunch soon on MEXC and BitMart. Previous holders of Packetcrypt can claim their first airdrop by following the directions on the Docs.",
          single_url: "https://docs.pkt.cash/buy-pkt",
          single_link: "Buy now",
          single_img: "/img/home/chess-2.webp",
          external: true
        }
      ],
      solutions_img_list: [
        {
          img_url: "/img/home/home-solutions-1.svg",
          single_alt: "Base",
          img_width: 92,
          img_height: 24
        },
        {
          img_url: "/img/home/home-solutions-2.svg",
          single_alt: "Coinbase",
          img_width: 144,
          img_height: 26
        },
        {
          img_url: "/img/home/home-solutions-3.svg",
          single_alt: "Akash",
          img_width: 132,
          img_height: 26
        },
        {
          img_url: "/img/home/home-solutions-4.svg",
          single_alt: "Uniswap",
          img_width: 140,
          img_height: 41
        },
        {
          img_url: "/img/home/home-solutions-5.svg",
          single_alt: "Anode",
          img_width: 88,
          img_height: 24
        },
        {
          img_url: "/img/home/home-solutions-6.svg",
          single_alt: "Routie",
          img_width: 110,
          img_height: 30
        },
      ],
      cards_list: [
        {
          single_title: "Media",
          single_descr: "PKT Network is a fully decentralized media network. Anyone can distribute media content with global accessibility, censorship-resistance and built-in payments.",
          single_url: "https://docs.pkt.cash/utility",
          single_link: this.$t("common.learn_more"),
          external: true
        },
        {
          single_title: "Infrastructure",
          single_descr: "Participants are paid to power the network by staking the PKT cryptocurrency and operating nodes. This supports the network’s connectivity and traffic routing.",
          single_url: "https://docs.pkt.cash/utility",
          single_link: this.$t("common.learn_more"),
          external: true
        },
        {
          single_title: "Payments Transparency",
          single_descr: "Built-in blockchain payments and smart contracts provide the revenue transparency and automated payment processing that is desperately needed in media distribution.",
          single_url: "https://docs.pkt.cash/utility",
          single_link: this.$t("common.learn_more"),
          external: true
        },
      ],
    };
  },
  head() {
    return {
      title: "PKT Cash - The Future of Internet Access",
      meta: [{ hid: "description", name: "description", content: "A decentralized physical infrastructure (DePIN) ecosystem supporting open internet access & powering the decentralized web" }],
      link: [
        {
          rel: 'canonical',
          href: 'https://pkt.cash' + this.$route.path
        }
      ]
    };
  },
  async middleware({ store }) {
    await store.dispatch('pkt-analytics/load')
  },
  async mounted() {
    await this.$store.dispatch('pkt-analytics/load')
  }
};
</script>
<style lang="scss">
.v-index {
  background-color: #00042c;
  &:before {
    content:'';
    background-image:url(/img/home/home-assets.webp);
    position:absolute;
    top:10%;
    left:0;
    width:100%;
    height:70%;
    background-position:center center;
    background-size:cover;
    z-index:1;
    @include for-width(-small-lg) {
      background-size:auto;
      background-position:left center;
    }
  }
  & > section {
    z-index:3;
    position:relative;
  }
  .v-top-section {
    @extend %t-center;
    padding:20vh 0 10vh;
    background-image:url(/img/home/home-top-bg.webp);
    background-position: top center;
    background-size: cover;
    background-repeat: no-repeat;
    @include for-width(-desktop-lg) {
      background-size: 100% 100%;
    }
    @include for-width(-tablet) {
      padding:15vh 0 10vh;
      background-position: top 0 left -175px;
      background-size: cover;
    }
    @include for-width(-small-lg) {
      padding:rem(180) 0 rem(60);
      background-position: top 0 left -75px;
      background-size: 200%;
    }
    & .container {
      padding: 0 rem(210);
      @include for-width(-laptop) {
        padding: 0 rem(125);
      }
      @include for-width(-tablet) {
        padding: 0;
      }
    }
    &__heading {
      @extend %h1-common;
      @include for-width(-small-lg) {
        padding: 0 rem(55);
      }
    }
    &__description {
      @extend %p-big-common;
      padding:rem(20) 0 rem(35);
      @include for-width(-small-lg) {
        padding:rem(25) rem(20) rem(35);
        max-width:rem(360);
        margin:0 auto;
      }
    }
    &__links {
      & .c-common-button {
        margin:0 rem(10);
      }
    }
    &__solutions {
      margin-top:10vh;
      @include for-width(-desktop-medium) {
        margin-top:10vh;
      }
      @include for-width(-desktop-med) {
        padding:0 rem(30);
      }
      @include for-width(-tablet) {
        margin-top:8vh;
      }
      @include for-width(-small-lg) {
        margin-top:rem(95);
        padding:0;
      }
      & p {
        @extend %p-common;
        margin-bottom:rem(20);
        @include for-width(-small-lg) {
          margin-bottom:rem(10);
        }
      }
      & .container {
        padding: 0;
      }
      &_carousel {
        width:100%;
        border-radius: 20px;
        background-color:$black_blue_light;
        padding:rem(15) rem(68) rem(12);
        @include for-width(-tablet) {
          padding:rem(15) rem(15) rem(12);
        }
        @include for-width(-small-lg) {
          border-radius: 0;
          padding:rem(24) rem(14);
        }
        & .c-images-single {
          margin:0 rem(10);
          @include for-width(-tablet) {
            margin:rem(7) 1%;
            max-width:16%;
          }
          @include for-width(-small-lg) {
            margin:rem(6) rem(8);
            max-width:50%;
          }
        }
      }
    }
  }
  .v-indexes-section {
    padding-bottom::23vh;
    @include for-width(-tablet) {
      padding-bottom::10vh;
    }
    @include for-width(-small-lg) {
      padding-bottom::rem(70);
    }
    & .container {
      @extend %df;
      @extend %jcsb;
      @extend %ais;
      @include for-width(-tablet) {
        display:block;
      }
    }
    &__heading {
      @extend %h2-common;
      width:25%;
      @include for-width(-tablet) {
        width:100%;
        padding-bottom:rem(35);
      }
    }
    &__inner {
      width:70%;
      @include for-width(-tablet) {
        width:100%;
      }
    }
  }
  .v-asymetrical-section {
    & .container {
      @extend %df;
      @extend %jcsb;
      @extend %ais;
      @include for-width(-tablet) {
        display:block;
      }
      & .c-common-button {
        @include for-width(-small-lg) {
          display:none;
        }
      }
      & .mobile_only {
        display:none;
        @include for-width(-small-lg) {
          display:block;
          margin-top:rem(25);
        }
      }
      & .c-asymetrical-block {
        @include for-width(-small-lg) {
          width:90%;
        }
        & .first {
          width:45%;
          padding-right:rem(40);
          @include for-width(-small-lg) {
            padding-top:0;
            width:100%;
            padding-right:0;
          }
        }
        & .second {
          width:55%;
          @include for-width(-small-lg) {
            width:100%;
          }
        }
        & .second > div {
          padding-left:0;
          padding-right:rem(175);
          @include for-width(-small-lg) {
            padding-right:0;
          }
        }
      }
    }
    &__heading {
      & h2 {
        @extend %h2-common;
        padding-bottom:rem(35);
        @include for-width(-small-lg) {
          padding-bottom:0;
        }
      }
      width:25%;
      @include for-width(-tablet) {
        width:100%;
        padding-bottom:rem(35);
      }
      @include for-width(-small-lg) {
        padding-bottom:rem(15);
      }
    }
    &__inner {
      width:70%;
      @include for-width(-tablet) {
        width:100%;
      }
    }
  }
  .v-powering-section {
    padding:25vh 0 20vh;
    @include for-width(-tablet) {
      padding:10vh 0;
    }
    @include for-width(-small-lg) {
      padding:rem(100) 0;
    }
    &__heading {
      @extend %h2-common;
      padding-bottom:rem(50);
      @include for-width(-tablet) {
        padding-bottom:rem(35);
      }
      @include for-width(-small-lg) {
        padding-bottom:rem(15);
        width:rem(250);
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
}
</style>