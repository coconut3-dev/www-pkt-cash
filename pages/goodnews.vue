<template>
  <div class="v-goodnews">
    <section class="v-main-section">
      <h1 class="v-main-section__heading">{{ $t("goodnews.title_1") }}<br /><span class="white">{{ $t("goodnews.title_2") }}</span></h1>
      <h2 class="v-main-section__subheading">{{ ann_number }}</h2>
      <!-- <h2 class="v-main-section__subheading">{{ $t("goodnews.title_3") }}</h2> -->
      <div class="v-main-section__timer">
        <span class="v-main-section__timer_el">{{ timerOutput.days }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_1") }}</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput.hours }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_2") }}</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput.minutes }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_3") }}</span></span><span class="v-main-section__timer_div">:</span>
        <span class="v-main-section__timer_el">{{ timerOutput.seconds }}<span class="v-main-section__timer_label">{{ $t("goodnews.counter_4") }}</span></span>
      </div>
      <div class="v-main-section__roadmap">
        <img src="/img/good_news/pkt-good-news-roadmap.svg" alt="Roadmap" width="800" height="475" />
      </div>
      <h2 class="v-main-section__comingtitle">{{ $t("goodnews.title_4") }}</h2>
      <div class="v-main-section__coming_soon">
        <img src="/img/good_news/pkt-good-news-coming-soon.webp" alt="Coming Soon" width="800" height="475" />
      </div>
      <div class="v-main-section__coming_soon">
        <img src="/img/good_news/pkt-good-news-coming-soon-1.webp" alt="Coming Soon" width="800" height="475" style="border-radius:15px;" />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Project Good News | PKT Cash",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Announcement 6 of 7'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Project Good News | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'Announcement 6 of 7'
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: '/img/featured_meta/pktcash-goodnews.jpg'
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
      targetDate: '2024-07-24T10:00:00',
      timerOutput: {
        days: 0,
        hours: 0,
        minutes: 0,
        seconds: 0
      },
      ann_number: 'Announcement 5 of 7',
      targetTimeZone: 'America/Los_Angeles',
      timerInterval: null
    };
  },
  methods: {
    initializeTimer() {
      const countdown = () => {
        const targetDateTime = new Date(this.targetDate);
        const now = new Date();
        const nowInTargetTimeZone = new Date(now.toLocaleString('en-US', { timeZone: this.targetTimeZone }));

        let timeDifference = targetDateTime.getTime() - nowInTargetTimeZone.getTime();

        if (timeDifference <= 0) {
          clearInterval(this.timerInterval);
          this.handleCountdownCompletion();
          return;
        }

        const millisecondsInOneSecond = 1000;
        const millisecondsInOneMinute = millisecondsInOneSecond * 60;
        const millisecondsInOneHour = millisecondsInOneMinute * 60;
        const millisecondsInOneDay = millisecondsInOneHour * 24;

        this.timerOutput.days = Math.floor(timeDifference / millisecondsInOneDay);
        this.timerOutput.hours = Math.floor((timeDifference % millisecondsInOneDay) / millisecondsInOneHour);
        this.timerOutput.minutes = Math.floor((timeDifference % millisecondsInOneHour) / millisecondsInOneMinute);
        this.timerOutput.seconds = Math.floor((timeDifference % millisecondsInOneMinute) / millisecondsInOneSecond);
      };
      countdown();

      this.timerInterval = setInterval(countdown, 1000);
    },
    handleCountdownCompletion() {
      this.ann_number = 'Announcement 6 of 7';
      this.targetDate = '2024-08-07T10:00:00';
      this.initializeTimer();
    }
  },
  mounted() {
    this.initializeTimer();
  },
  beforeDestroy() {
    clearInterval(this.timerInterval);
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
  background-attachment: fixed;
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
    padding:rem(100) 0 rem(75);
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
    &__comingtitle {
      color:$black_blue;
      @extend %inter_medium;
      font-size: rem(46);
      line-height: rem(80);
      padding-top:rem(50);
      @include for-width(-desktop-medium) {
        font-size: rem(40);
      }
      @include for-width(-small-lg) {
        font-size: rem(24);
        line-height: rem(70);
        padding-top:rem(5);
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
    &__coming_soon {
      padding-top:rem(25);
      @include for-width(-desktop-medium) {
        padding-left: rem(40);
        padding-right: rem(40);
      }
      @include for-width(-small-lg) {
        padding:0 rem(20) 0;
      }
      img {
        width:rem(820);
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
