<template>
  <div class="v-devcenter">
    <section class="v-header-section">
      <SpotAInternal 
      :title="this.$t('dev_central.title')"
      :text="this.$t('dev_central.text')" 
      :button_1="this.$t('dev_central.button_1')"
      :button_2="this.$t('dev_central.button_2')"
      button_1_link="/network-steward"
      button_2_link="https://docs.pkt.cash/"
      button_2_target="_blank"  />
    </section>
    <section class="v-simple-section">
      <SimpleText :list="simple_block" />
    </section>
    <section class="v-block-links-section">
      <div class="container">
        <div class="v-block-links-section__inner">
          <div class="v-block-links-section__single orange_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("dev_central.block_1_title") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("dev_central.block_1_text") }}</p></div>
            <a href="https://github.com/cjdelisle/cjdns" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("dev_central.block_button_1") }}</span></a>
          </div>
          <div class="v-block-links-section__single blue_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("dev_central.block_2_title") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("dev_central.block_2_text") }}</p></div>
            <a href="https://pkt.world/mining" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("dev_central.block_button_2") }}</span></a>
          </div>
          <div class="v-block-links-section__single green_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("dev_central.block_3_title") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("dev_central.block_3_text") }}</p></div>
            <a href="https://docs.pkt.cash/en/latest/mining/pool_setup_guide/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("dev_central.button_2") }}</span></a>
          </div>
        </div>
        <div class="v-block-links-section__inner">
          <div class="v-block-links-section__single dark_blue_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("dev_central.block_4_title") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("dev_central.block_4_text") }}</p></div>
            <a href="https://docs.pkt.cash/en/latest/pktd/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("dev_central.block_button_1") }}</span></a>
          </div>
          <div class="v-block-links-section__single grey_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("dev_central.block_5_title") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("dev_central.block_5_text") }}</p></div>
            <a href="https://github.com/cjdelisle/PKT-Lightning-Wallet" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("common.learn_more") }}</span></a>
          </div>
          <div class="v-block-links-section__single rose_bg">
            <div><h3 class="v-block-links-section__title">{{ $t("dev_central.block_6_title") }}</h3>
            <p class="v-block-links-section__descr">{{ $t("dev_central.block_6_text") }}</p></div>
            <a href="https://docs.pkt.cash/en/latest/cjdns_websites/" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>{{ $t("common.learn_more") }}</span></a>
          </div>
        </div>
      </div>
    </section>
    <section class="v-join-section">
      <JoinCommunity />
    </section>
  </div>
</template>

<script>
import SpotAInternal from "~/components/Common/SpotAInternal";
import SimpleText from "~/components/Common/SimpleText";
import JoinCommunity from "~/components/Common/JoinCommunity";
export default {
  components: {
    SpotAInternal,
    SimpleText,
    JoinCommunity
  },
  data() {
    return {
      simple_block: [
        {
          single_title: this.$t("dev_central.block_button_2"),
          single_text: this.$t("dev_central.simple_text"),
        }
      ]
    };
  },
  head() {
    return {
      title: 'Developer Central | PKT Cash',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'PKT is a community project. All the technology in the ecosystem is developed by contributors and/or community member companies inspired by PKT’s mission. Here you will find all the documentation you need to begin building within the ecosystem.'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Developer Central | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'PKT is a community project. All the technology in the ecosystem is developed by contributors and/or community member companies inspired by PKT’s mission. Here you will find all the documentation you need to begin building within the ecosystem.'
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
.v-devcenter {
  background-color:$black_blue;
  position:relative;
  background-image:url(/img/developer-center-top.webp);
  background-position:right top;
  background-size:rem(600);
  background-repeat:no-repeat;
  @include for-width(-desktop-med) {
    background-size:rem(550);
  }
  @include for-width(-desktop-med) {
    background-size:rem(550);
  }
  @include for-width(-tablet) {
    background-size:rem(450);
  }
  @include for-width(-small-lg) {
    background-size:100%;
    background-image:url(/img/developer-center-top-mobile.webp);
    background-position:right top;
  }
  &:before {
    content:'';
    background-image:url(/img/pkt-network-before.webp);
    position:absolute;
    top:5%;
    left:0;
    width:85%;
    height:85%;
    background-position:left top;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
    @include for-width(-small-lg) {
      background-size:cover;
      width:100%;
    }
  }
  &:after {
    content:'';
    background-image:url(/img/pkt-network-after.webp);
    position:absolute;
    bottom:0;
    right:0;
    width:65%;
    height:60%;
    background-position:right bottom 60%;
    background-size:cover;
    background-repeat:no-repeat;
    z-index:1;
    @include for-width(-small-lg) {
      display:none;
    }
  }
  & > section {
    z-index:3;
    position:relative;
  }
  & .c-spot-a-internal {
    @include for-width(-small-lg) {
      padding:rem(120) 0 rem(70);
    }
    &__title {
      max-width:rem(475);
      @include for-width(-small-lg) {
        max-width:rem(200);
      }
    }
  }
  .v-simple-section {
    .c-common-simple {
      & .container {
        padding: rem(54) rem(105) rem(60);
        @include for-width(-laptop) {
          padding: rem(35) rem(100) rem(40);
        }
        @include for-width(-tablet) {
          padding: rem(35) rem(50) rem(40);
        }
        @include for-width(-small-lg) {
          padding: rem(35) rem(25);
        }
      }
    }
  }
  .v-block-links-section {
    padding:rem(150) 0 rem(0);
    @include for-width(-tablet) {
      padding:rem(100) 0 0;
    }
    &__inner {
      @extend %df;
      @extend %jcsb;
      @extend %fw;
      padding-bottom:rem(60);
      &:last-child {
        padding-bottom:0;
      }
      @include for-width(-tablet) {
        display:block;
        padding-bottom:0;
      }
    }
    &__single {
      width:31.5%;
      border-radius:rem(20);
      padding:rem(20) rem(30) rem(40);
      @extend %df;
      @extend %jcsb;
      @extend %fdc;
      @extend %ais;
      @include for-width(-laptop) {
        padding:rem(25) rem(30);
      }
      @include for-width(-tablet) {
        width:100%;
        margin-bottom:rem(20);
      }
      @include for-width(-small-lg) {
        padding:rem(20) rem(30);
      }
    }
    &__title {
      font-size: rem(40);
      line-height: rem(50);
      color:$black_blue;
      @extend %inter_bold;
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
      padding:rem(10) 0 rem(20);
      @include for-width(-small-lg) {
        font-size: rem(16);
        line-height: rem(24);
      }
    }
  }
}
</style>