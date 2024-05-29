<template>
  <div class="v-goodnews">
    <section class="v-main-section">
      <h1 class="v-main-section__heading">Project<br /><span class="white">GOOD NEWS</span></h1>
      <h2 class="v-main-section__subheading">Announcement 1 of 7</h2>
      <div class="v-main-section__timer">
        <span class="v-main-section__timer_el">{{ timerOutput_days }}<span class="v-main-section__timer_label">Days</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput_hours }}<span class="v-main-section__timer_label">Hours</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput_mins }}<span class="v-main-section__timer_label">Mins</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput_secs }}<span class="v-main-section__timer_label">Secs</span></span>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Project GOOD NEWS - PKT",
      meta: [{ hid: "description", name: "description", content: "Announcement 1 of 7" }],
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
      countDownToTime : new Date("Jun 12, 2024 10:00:00").getTime(),
      timerOutput_days:  null,
      timerOutput_hours:  null,
      timerOutput_mins:  null,
      timerOutput_secs:  null
    }
  },
  methods: {
    startTimer: function() {
      const timeNow = new Date().getTime();
      const timeDifference = this.countDownToTime - timeNow;
      const millisecondsInOneSecond = 1000;
      const millisecondsInOneMinute = millisecondsInOneSecond * 60;
      const millisecondsInOneHour = millisecondsInOneMinute * 60;
      const millisecondsInOneDay = millisecondsInOneHour * 24;
      const differenceInDays = timeDifference / millisecondsInOneDay;
      const remainderDifferenceInHours = (timeDifference % millisecondsInOneDay) / millisecondsInOneHour;
      const remainderDifferenceInMinutes = (timeDifference % millisecondsInOneHour) / millisecondsInOneMinute;
      const remainderDifferenceInSeconds = (timeDifference % millisecondsInOneMinute) / millisecondsInOneSecond;
      const remainingDays = Math.floor(differenceInDays);
      const remainingHours = Math.floor(remainderDifferenceInHours);
      const remainingMinutes = Math.floor(remainderDifferenceInMinutes);
      const remainingSeconds =Math.floor(remainderDifferenceInSeconds);
      this.timerOutput_days = remainingDays;
      this.timerOutput_hours = remainingHours;
      this.timerOutput_mins = remainingMinutes;
      this.timerOutput_secs = remainingSeconds;
    }
  },
  mounted () {
    document.body.classList.add('goodnews');
    setInterval(() => { this.startTimer() }, 1000);
  },
};
</script>

<style lang="scss">
.goodnews {
  overflow: hidden;
  & .c-header {
    & .nav__logo {
      background-image:url(/img/logo-new-dark.svg);
      background-repeat:no-repeat;
      background-size:contain;
      background-position:left center;
      @include for-width(-small-lg) {
        background:none;
      }
      & img {
        opacity:0;
        visibility:hidden;
        @include for-width(-small-lg) {
          opacity:1;
          visibility:visible;
        }
      }
    }
  }  
  & .c-footer {
    display:none;
  }
}
.v-goodnews {
  background-image:url(/img/goodnews-bg.webp);
  background-repeat:no-repeat;
  background-size:cover;
  background-position:center center;
  width:100%;
  height:100vh;
  @extend %df;
  @extend %jcc;
  @extend %fdc;
  @extend %aic;
  @include for-width(-small-lg) {
    background-image:url(/img/goodnews-bg-mobile.webp);
  }
  & .v-main-section {
    @extend %t-center;
    &__heading {
      color:$black_blue;
      @extend %inter_black;
      font-size: rem(80);
      line-height: rem(98);
      text-transform:uppercase;
      padding-top:rem(35);
      @include for-width(-desktop-medium-default) {
        padding-top:rem(50);
      }
      @include for-width(-desktop-medium) {
        font-size: rem(70);
        line-height: rem(88);
        padding-top:rem(65);
      }
      @include for-width(-small-lg) {
        font-size: rem(42);
        line-height: rem(52);
        padding-top:rem(50);
      }
      & span {
        background-color:#F66020;
        border-radius:rem(6);
        line-height: rem(104);
        padding:0 rem(35);
        @include for-width(-desktop-medium) {
          line-height: rem(94);
          padding:0 rem(25);
        }
        @include for-width(-small-lg) {
          line-height: rem(52);
        }
      }
    }
    &__subheading {
      color:$black_blue;
      @extend %inter_medium;
      font-size: rem(46);
      line-height: rem(80);
      @include for-width(-desktop-medium) {
        font-size: rem(40);
      }
      @include for-width(-small-lg) {
        font-size: rem(24);
        line-height: rem(70);
      }
    }
    &__timer {
      margin-top:rem(50);
      color:$black_blue;
      @include for-width(-small-lg) {
        margin-top:rem(35);
      }
      &_el {
        @extend %inter_bold;
        @extend %dib;
        vertical-align:top;
        font-size: rem(64);
        line-height: rem(64);
        width:rem(90);
        @include for-width(-small-lg) {
          font-size: rem(36);
          line-height: rem(36);
          width:rem(54);
        }
      }
      &_label {
        @extend %inter_regular;
        @extend %db;
        font-size: rem(26);
        line-height: rem(26);
        padding-top:rem(20);
        @include for-width(-small-lg) {
          font-size: rem(14);
          line-height: rem(14);
          padding-top:rem(10);
        }
      }
      &_div {
        @extend %inter_bold;
        @extend %dib;
        vertical-align:top;
        font-size: rem(64);
        line-height: rem(64);
        padding:0 rem(5);
        @include for-width(-small-lg) {
          font-size: rem(36);
          line-height: rem(36);
        }
      }
    }
  }
}
</style>
