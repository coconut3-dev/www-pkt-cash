<template>
  <div class="c-index-features">
    <div class="container">
      <h1 class="c-index-features__title">
        <svg width="40" height="39" viewBox="0 0 40 39" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M14 11.7979H40V32.2212C40 35.5349 37.3137 38.2212 34 38.2212H14V11.7979Z" fill="#98E0F9" />
          <rect x="1" y="10.7817" width="9" height="9.14648" fill="#98E0F9" />
          <rect y="0.618896" width="6" height="6.09766" fill="#98E0F9" />
          <rect x="15" y="1.63513" width="6" height="6.09766" fill="#98E0F9" />
          <rect x="9" y="2.65143" width="3" height="3.04883" fill="#98E0F9" />
        </svg>
        {{ $t("home.features_title") }}
      </h1>
      <div class="c-index-features__list">
        <ul class="c-index-features__list-list">
          <li class="c-index-features__list-item">
            <figure class="c-index-features__list-img">
              <img src="/img/features-1.png" alt />
            </figure>
            <h4 class="c-index-features__list-title">{{ $t("home.feature_1_title") }}</h4>
            <p class="c-index-features__list-text">{{ $t("home.feature_1_descr") }}</p>
          </li>
          <li class="c-index-features__list-item">
            <figure class="c-index-features__list-img">
              <img src="/img/features-2.png" alt />
            </figure>
            <h4 class="c-index-features__list-title">{{ $t("home.feature_2_title") }}</h4>
            <p class="c-index-features__list-text">{{ $t("home.feature_2_descr") }}</p>
          </li>
          <li class="c-index-features__list-item">
            <figure class="c-index-features__list-img">
              <img src="/img/features-3.png" alt />
            </figure>
            <h4 class="c-index-features__list-title">{{ $t("home.feature_3_title") }}</h4>
            <p class="c-index-features__list-text">{{ $t("home.feature_3_descr") }}</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexFeatures",
};
</script>

<style lang="scss">
.c-index-features {
  padding: rem(14) rem(0) rem(100);
  padding-bottom: 0;
  @include for-width(-tablet) {
    padding: rem(25) rem(25) rem(50);
  }

  .container {
    width: 100%;
    max-width: rem(1315);
    margin: 0 auto;
  }

  &__title {
    @extend %h1-title;
    margin-bottom: rem(10);
    padding: 0 rem(34);
    @include for-width(-tablet) {
      margin-bottom: rem(40);
      @include font_sizes(33, 43);
    }
    display: flex;
    align-items: flex-start;

    & svg {
      margin-top: rem(16);
      margin-right: rem(10);
      @include for-width(-tablet) {
        display: none;
      }
    }
  }

  &__list {
    flex: 0 0 100%;
    margin-top: rem(30);

    &-list {
      display: flex;
      @include for-width(-tablet-lg) {
        flex-wrap: wrap;
      }
    }

    &-item {
      flex: 0 0 33.33%;
      padding: 0 rem(50) rem(30);
      @include for-width(-tablet-lg) {
        flex: 0 0 100%;
        padding: 0 0 rem(50);
      }
      @include for-width(-tablet) {
        padding: 0 0 rem(30);
      }
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    &-title {
      @extend %h2-title;
      margin-bottom: rem(30);
      @include for-width(-tablet) {
        margin-bottom: rem(15);
        @include font_sizes(16, 26);
      }
    }

    &-text {
      @extend %text-main;
      @include for-width(-tablet) {
        text-align: center;
        @include font_sizes(16, 26);
      }
    }

    &-img {
      height: rem(100);
      margin: rem(50) auto;
      @include for-width(-tablet) {
        height: rem(100);
        margin-bottom: rem(50);
        text-align: center;
      }

      & img {
        max-width: 100%;
      }
    }
  }
}
</style>
