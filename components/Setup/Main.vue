<template>
  <div>
    <div class="c-content-main">
      <div class="container">
        <div class="c-content-main__wrap">
          <!-- Navigation -->
          <div class="c-content-main__navigation">
            <ul class="c-content-main__navigation-list">
              <li class="c-content-main__navigation-item">
                <a href="#" class="c-content-main__navigation-link">{{ $t("setup.nav_01") }}</a>
              </li>
              <li class="c-content-main__navigation-item">
                <a href="#Ubuntu" @click="itm_link = 'Ubuntu'" :class="{ active: itm_link === 'Ubuntu' || itm_link === null, }" class="c-content-main__navigation-link">{{ $t("setup.nav_02") }}</a>
              </li>
              <li class="c-content-main__navigation-item">
                <a href="#Alpine-Linux" @click="itm_link = 'Alpine-Linux'" :class="{ active: itm_link === 'Alpine-Linux' }" class="c-content-main__navigation-link">{{ $t("setup.nav_03") }}</a>
              </li>
              <li class="c-content-main__navigation-item">
                <a href="#Apple-OSX" @click="itm_link = 'Apple-OSX'" :class="{ active: itm_link === 'Apple-OSX' }" class="c-content-main__navigation-link">{{ $t("setup.nav_04") }}</a>
              </li>
              <li class="c-content-main__navigation-item">
                <a href="#Begin-Mining" @click="itm_link = 'Begin-Mining'" :class="{ active: itm_link === 'Begin-Mining' }" class="c-content-main__navigation-link">{{ $t("setup.nav_05") }}</a>
              </li>
            </ul>
          </div>
          <!-- // Navigation -->

          <!-- Item 1 -->
          <div class="c-content-anchor" id="Ubuntu"></div>
          <div class="c-content-main__content">
            <div class="c-content-main__section">
              <h2 class="c-content-main__title">{{ $t("setup.nav_02") }}</h2>
              <p class="c-content-main__text">
                {{ $t("setup.nav_01_text_01") }}
              </p>
              <pre class="c-content-main__scroll">
sudo add-apt-repository universe
sudo apt-get update
sudo apt install pkg-config libsodium-dev autoconf-archive git libssl-dev build-essential</pre>
              <p class="c-content-main__text">
                {{ $t("setup.nav_01_text_02") }}
              </p>
              <pre class="c-content-main__scroll">
git clone https://github.com/cjdelisle/PacketCrypt cd PacketCrypt
./autogen.sh
./configure
make
npm install</pre>
            </div>
            <!-- // Item 1 -->

            <!-- Item 2 -->
            <div class="c-content-anchor" id="Alpine-Linux"></div>
            <div class="c-content-main__section">
              <h2 class="c-content-main__title">{{ $t("setup.nav_03") }}</h2>
              <p class="c-content-main__text">
                {{ $t("setup.nav_02_text_01") }}
              </p>
              <pre class="c-content-main__scroll">
sudo apk update
sudo apk add nodejs npm autoconf automake autoconf-archive build-base git libsodium-dev
openssl-dev</pre>
              <p class="c-content-main__text">
                {{ $t("setup.nav_01_text_02") }}
              </p>
              <pre class="c-content-main__scroll">
git clone https://github.com/cjdelisle/PacketCrypt
cd PacketCrypt
./autogen.sh
./configure
make
npm install</pre>
            </div>
            <!-- // Item 2 -->

            <!-- Item 3 -->
            <div class="c-content-anchor" id="Apple-OSX"></div>
            <div class="c-content-main__section">
              <h2 class="c-content-main__title">{{ $t("setup.nav_04") }}</h2>
              <p class="c-content-main__text">
                {{ $t("setup.nav_03_text_01") }}
              </p>
              <pre class="c-content-main__scroll">
brew install libsodium pkg-config autoconf-archive openssl</pre>
              <p class="c-content-main__text">
                {{ $t("setup.nav_01_text_02") }}
              </p>
              <pre class="c-content-main__scroll">
git clone https://github.com/cjdelisle/PacketCrypt
cd PacketCrypt
./autogen.sh
export PKG_CONFIG_PATH="$PKG_CONFIG_PATH:`echo /usr/local/Cellar/libsodium/*/lib/pkgconfig`"
export PKG_CONFIG_PATH="$PKG_CONFIG_PATH:`echo /usr/local/Cellar/openssl/*/lib/pkgconfig/`"
./configure
make
npm install</pre>
              <p class="c-content-main__more">
                {{ $t("setup.nav_03_text_02") }}
                <nuxt-link to="/">{{ $t("common.learn_more") }}</nuxt-link>
              </p>
            </div>
          </div>
          <!-- // Item 3 -->
        </div>
      </div>
    </div>
    <div class="c-setup-main">
      <div class="container">
        <h1 class="c-setup-main__title">{{ $t("setup.nav_05") }}</h1>
        <div class="c-setup-main__wrap grid">
          <div class="wrapper-text">
            <p class="c-setup-main__text">
              {{ $t("setup.nav_04_text_01") }}
            </p>
            <p class="c-setup-main__text">
              {{ $t("setup.nav_04_text_02") }}
            </p>
          </div>
          <div class="wrapper-text">
            <p class="c-setup-main__text">
              {{ $t("setup.nav_04_text_03") }}
            </p>
            <div class="c-setup-main__btns">
              <a href="https://github.com/cjdelisle/PacketCrypt " target="_blank" class="c-setup-main__link blue-btn-arrow">
                <span>{{ $t("setup.nav_04_link_01") }}</span>
              </a>
              <a href="https://pkteer.com/" target="_blank" class="c-setup-main__link blue-btn-arrow">
                <span>{{ $t("setup.nav_04_link_02") }}</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="c-content-main c-content-main-two">
      <div class="container">
        <div class="c-content-main__wrap">
          <!-- Item 4 -->
          <div class="c-content-anchor" id="Begin-Mining"></div>
          <div class="c-content-main__content">
            <div class="c-content-main__section">
              <h2 class="c-content-main__title">{{ $t("home.scroll_section_block_3_title") }}:</h2>
              <pre class="c-content-main__scroll">
node ./annmine.js --threads 2 --paymentAddr=pDSxcZunaUSUSxHrL6r8zpGJvoEropJ3Es http://pool.pkteer.com</pre>
              <h2 class="c-content-main__title">{{ $t("home.scroll_section_block_4_title") }}:</h2>
              <pre class="c-content-main__scroll">
node ./blkmine.js --threads 2 --paymentAddr=pDSxcZunaUSUSxHrL6r8zpGJvoEropJ3Es http://pool.pkteer.com</pre>
              <!--              <h2 class="c-content-main__title">Resources</h2>-->
              <!--              <ul class="c-content-main__list&#45;&#45;small">-->
              <!--                <li class="c-content-main__list&#45;&#45;small-item">Telegram: https://t.me/pktproject</li>-->
              <!--                <li class="c-content-main__list&#45;&#45;small-item">Matrix: #pkt:matrix.org</li>-->
              <!--                <li class="c-content-main__list&#45;&#45;small-item">IRC: #pkt@freenode.net</li>-->
              <!--                <li class="c-content-main__list&#45;&#45;small-item">Suggest an edit to this page</li>-->
              <!--                <li class="c-content-main__list&#45;&#45;small-item">Main</li>-->
              <!--              </ul>-->
            </div>
            <!-- // Item 4 -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SetupMain",
  props: {
    title: String,
    text: String,
    bg: String,
  },
  data() {
    return {
      itm_link: null,
    };
  },
  methods: {
    getCoords(name) {
      const box = document.querySelector(name).getBoundingClientRect();
      //
      return box.top + pageYOffset;
    },
  },
  mounted() {
    if (process.client) {
      document.addEventListener("scroll", () => {
        const condition = window.innerWidth > 1100 ? 80 : 60;
        const section_0 = this.getCoords("#Ubuntu") - condition;
        const section_1 = this.getCoords("#Alpine-Linux") - condition;
        const section_2 = this.getCoords("#Apple-OSX") - condition;
        let scroll_y =
          window.innerWidth > 1100 ? window.scrollY : window.scrollY + 30;
        if (scroll_y < section_0) {
          this.itm_link = null;
        }
        if (scroll_y >= section_0) {
          this.itm_link = "Ubuntu";
        }
        if (scroll_y >= section_1) {
          this.itm_link = "Alpine-Linux";
        }
        if (scroll_y >= section_2) {
          this.itm_link = "Apple-OSX";
        }
      });
    }
  },
};
</script>

<style lang="scss" scoped>
.c-content-main {
  & .container {
    width: 100%;
    max-width: rem(1182);
  }

  &__content {
    width: 100%;
    max-width: calc(100% - 440px);
    @include for-width(-tablet) {
      max-width: 100%;
    }
  }

  &__navigation {
    width: rem(220);
  }
}

.c-content-main-two {
  & .c-content-main .container {
    width: 100%;
    max-width: rem(1182);
  }

  & .c-content-main__wrap {
    justify-content: center;
  }

  & .c-content-main__content {
    width: 100%;
    max-width: calc(100% - 440px);
    @include for-width(-tablet) {
      max-width: 100%;
    }
  }
}

.c-setup-main {
  padding: rem(118) rem(80);
  @include for-width(-tablet) {
    padding: rem(25) rem(25) rem(30);
  }
  background-color: $dark_blue;
  color: $light_blue;
  & & .container {
    width: 100%;
    max-width: rem(1129);
    margin: 0 auto;
  }

  &__title {
    @extend %h1-title;
    margin-bottom: rem(50);
  }

  &__text {
    @extend %text-main;
    margin-bottom: rem(30);
    @include for-width(-tablet) {
      margin-bottom: rem(10);
    }
  }

  &__wrap {
    display: flex;
    flex-wrap: wrap;
    &.grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-gap: 20px;
      @include for-width(-tablet) {
        display: block;
      }
    }
  }

  &__link:not(:last-child) {
    margin-bottom: rem(20);
    margin-right: rem(30);
  }
}
</style>
