<template>
  <div class="v-network">
    <section class="v-header-section">
      <SpotAInternal 
      :title="this.$t('pkt_network.title')"
      :text="this.$t('pkt_network.text')" 
      :button_1="this.$t('header.ecosystem')"
      :button_2="this.$t('header.roadmap')"
      button_1_link="/ecosystem"
      button_2_link="/build" />
    </section>
    <!-- <section class="v-analytics-section">
      <AnalyticsDataNetwork />
    </section> -->
    <section class="v-simple-section">
      <SimpleText :list="simple_block" />
    </section>
    <section class="v-asymetrical-section">
      <div class="container">
        <div class="v-asymetrical-section__heading">
          <h2>{{ $t("pkt_network.assym_title") }}</h2>
        </div>
        <div class="v-asymetrical-section__inner">
          <BlockAsymmetrical :listFirst="asymetrical_block_list" :listSecond="asymetrical_block_list_second" />
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
// import AnalyticsDataNetwork from "~/components/Network/AnalyticsDataNetwork";
import SimpleText from "~/components/Common/SimpleText";
import BlockAsymmetrical from "~/components/Common/BlockAsymmetrical";
import JoinCommunity from "~/components/Common/JoinCommunity";
export default {
  components: {
    SpotAInternal,
    // AnalyticsDataNetwork,
    SimpleText,
    BlockAsymmetrical,
    JoinCommunity
  },
  data() {
    return {
      simple_block: [
        {
          single_title: this.$t("pkt_network.simple_title"),
          single_text: this.$t("pkt_network.simple_text"),
        }
      ],
      asymetrical_block_list: [
        {
          single_title: this.$t("pkt_network.assym_1_title"),
          single_descr: this.$t("pkt_network.assym_1_text"),
          color: "blue_dot"
        },
        {
          single_title: this.$t("pkt_network.assym_2_title"),
          single_descr: this.$t("pkt_network.assym_2_text"),
          color: "green_dot"
        }
      ],
      asymetrical_block_list_second: [
        {
          single_title: this.$t("pkt_network.assym_second_1_title"),
          single_descr: this.$t("pkt_network.assym_second_1_text"),
          color: "green_dot"
        },
        {
          single_title: this.$t("pkt_network.assym_second_2_title"),
          single_descr: this.$t("pkt_network.assym_second_2_text"),
          color: "blue_dot"
        }
      ],
    };
  },
  head() {
    return {
      title: 'Scaling the PKT Network | PKT Cash',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'PKT Network is a high speed, VPN-based network. The network’s decentralized physical infrastructure (DePIN) is designed to support open internet access and empower people to build websites where the web URL is also a PKT payment address.'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Scaling the PKT Network | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'PKT Network is a high speed, VPN-based network. The network’s decentralized physical infrastructure (DePIN) is designed to support open internet access and empower people to build websites where the web URL is also a PKT payment address.'
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
.v-network {
  background-color:$black_blue;
  position:relative;
  background-image:url(/img/pkt-network-before.webp);
  background-position:left center;
  background-size:70%;
  background-repeat:no-repeat;
  &:before {
    content:'';
    background-image:url(/img/pkt-network-top-asset.webp);
    position:absolute;
    top:0;
    right:0;
    width:75%;
    height:75%;
    background-position:right -300px top -175px;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
    @include for-width(-desktop-medium) {
      width:70%;
      height:70%;
      background-position:right -200px top -125px;
    }
    @include for-width(-tablet) {
      width:90%;
    }
    @include for-width(-small-lg) {
      width:100%;
      height:30%;
      background-position:left bottom 300px;
      background-size:cover;
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
      background-size:contain;
    }
  }
  & > section {
    z-index:3;
    position:relative;
  }
  & .c-spot-a-internal {
    @include for-width(-small-lg) {
      padding:rem(100) 0 rem(50);
    }
    &__title {
      max-width:rem(475);
      @include for-width(-small-lg) {
        max-width:rem(250);
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
          padding: rem(35);
        }
      }
    }
  }
  .v-asymetrical-section {
    & .first {
		  padding-top:rem(95);
      @include for-width(-tablet) {
        padding-top:0;
      }
	  }
    & .second {
		  & .green_dot:before {
        background-color: #0D4AE7;
      }
      & .blue_dot:before {
        background-color: #00B127;
      }
	  }
    & .container {
      @extend %df;
      @extend %jcsb;
      @extend %ais;
      padding:rem(190) 0 0;
      @include for-width(-laptop) {
        padding:rem(75) 0 rem(35);
      }
      @include for-width(-tablet) {
        display:block;
      }
      @include for-width(-small-lg) {
        padding:rem(95) rem(20) 0;
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
      width:35%;
      @include for-width(-tablet) {
        width:100%;
        padding-bottom:rem(35);
      }
      @include for-width(-small-lg) {
        padding-bottom:rem(15);
      }
    }
    &__inner {
      width:65%;
      @include for-width(-tablet) {
        width:100%;
      }
      @include for-width(-small-lg) {
        padding:0 rem(20);
      }
    }
  }
}
</style>