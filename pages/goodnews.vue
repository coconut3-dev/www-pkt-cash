<template>
  <div class="v-goodnews">
    <section class="v-main-section">
      <h1 class="v-main-section__heading">{{ $t("goodnews.title_1") }}<br /><span class="white">{{ $t("goodnews.title_2") }}</span></h1>
      <h2 class="v-main-section__subheading">{{ ann_number }}</h2>
      <div class="v-main-section__timer">
        <span class="v-main-section__timer_el">{{ timerOutput_days }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_1") }}</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput_hours }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_2") }}</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput_mins }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_3") }}</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput_secs }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_4") }}</span></span>
      </div>
      <div class="v-main-section__roadmap">
        <img src="/img/good_news/pkt-good-news-roadmap.svg" alt="Roadmap" width="800" height="475" />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Project GOOD NEWS | PKT Cash",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Announcement 3 of 7'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Project GOOD NEWS | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'Announcement 3 of 7'
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: '/img/featured_meta/pktcash-goodnews.jpeg'
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
  data() {
    return {
      countDownToTime : new Date("Jun 26, 2024 10:00:00").getTime(),
      timerOutput_days:  0,
      timerOutput_hours:  0,
      timerOutput_mins:  0,
      timerOutput_secs:  0,
      ann_number: 'Announcement 3 of 7',
    }
  },
  methods: {
    startTimer: function() {
      const timeNow = new Date().getTime();
      const timeDifference = this.countDownToTime - timeNow;

      if (timeDifference <= 0) {
        this.countDownToTime = this.getNewCountDownTime();
        timeDifference = this.countDownToTime - timeNow;
      }

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
    },

    getNewCountDownTime: function() {
      const newTime = new Date("Jul 10, 2024 10:00:00").getTime();
      this.ann_number = 'Announcement 4 of 7';
      return newTime;
    },

  },
  mounted () {
    this.timer = setInterval(this.startTimer, 1000);
    document.getElementById('__nuxt').classList.add('goodnews');
    // setInterval(() => { this.startTimer() }, 1000);
  },
  beforeDestroy() {
    clearInterval(this.timer);
  }
};
</script>

<style lang="scss">
.goodnews {
  // overflow: hidden;
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
}
.v-goodnews {
  background-image:url(/img/goodnews-bg.webp);
  background-repeat:no-repeat;
  background-size:cover;
  background-position:center center;
  width:100%;
  min-height:100vh;
  height:auto;
  padding:rem(150) 0 rem(75);
  @extend %df;
  @extend %jcc;
  @extend %fdc;
  @extend %aic;
  @include for-width(-desktop-medium) {
    padding:rem(100) 0 rem(50);
  }
  @include for-width(-small-lg) {
    background-image:url(/img/goodnews-bg-mobile.webp);
    height:100vh;
    padding:0;
  }
  & .v-main-section {
    @extend %t-center;
    @include for-width(-small-lg) {
      margin-bottom:0;
    }
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
        padding-top:0;
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
        margin-top:rem(15);
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
    &__roadmap {
      padding-top:rem(50);
      @include for-width(-desktop-medium) {
        padding-left: rem(40);
        padding-right: rem(40);
      }
      @include for-width(-small-lg) {
        padding:rem(40) rem(25) 0;
      }
      img {
        width:rem(800);
        height:rem(475);
        @include for-width(-small-lg) {
          width:100%;
          height:auto;
        }
      }
    }
  }
}
</style>
