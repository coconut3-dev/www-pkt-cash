<template>
  <div class="c-common-join">
    <div class="container">
      <h3 class="c-common-join__title">{{ $t("home.join_community_title") }}</h3>
      <div class="c-common-join__links">
        <a class="c-common-button c-common-button__bordered" href="https://discord.gg/pkt" target="_blank">
          <span>PKT Discord</span>
        </a>
        <a class="c-common-button c-common-button__bordered" href="https://x.com/pktcash" target="_blank">
          <span>PKT Twitter</span>
        </a>
        <a class="c-common-button c-common-button__bordered" href="https://t.me/pktcash" target="_blank">
          <span>PKT Telegram</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "JoinCommunity",
};
</script>

<style lang="scss">
.c-common-join {
  padding:rem(150) 0 rem(130);
  @include for-width(-desktop-med) {
    padding:rem(125) rem(30);
  }
  @include for-width(-tablet) {
    padding:10vh rem(30);
  }
  @include for-width(-small-lg) {
    padding:rem(85) rem(20);
  }
  & .container {
    border-radius:rem(20);
    background-color:$black_blue_light;
    padding: rem(50);
    @extend %df;
    @extend %jcsb;
    @extend %ais;
    @include for-width(-small-lg) {
      display:block;
      padding:rem(35) rem(15);
      background:none;
    }
  }
  &__title {
    @extend %h3-common;
    color:$white;
    @include for-width(-small-lg) {
      text-align:center;
      font-size: rem(18);
      font-family: "Inter-Regular", sans-serif;
      line-height: rem(26);
      padding-bottom:rem(15);
    }
  }
  &__links {
    @include for-width(-small-lg) {
      // display: -webkit-flex;
      // display: -moz-flex;
      // display: -ms-flex;
      // display: -o-flex;
      // display: flex;
      // justify-content: space-between;
      // -ms-align-items: center;
      // align-items: center;
    }
    .c-common-button {
      @extend %db;
      margin-top:rem(20);
      @include for-width(-small-lg) {
        margin:rem(20) auto 0;
      }
      &:first-child {
        margin-top:0;
        // @include for-width(-small-lg) {
        //   margin-top:0;
        // }
      }
    }
  }
}
</style>