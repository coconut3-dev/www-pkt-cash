<template>
<header class="c-header">
  <div class="container">
    <nav class="c-navigation">
        <div class="nav__logo">
          <div class="nav__logo">
            <a :href="localePath('index')" title="PKT Cash">
              <img src="/img/logo-new.svg" alt="PKT Cash" />
            </a>
          </div>
        </div>
        <div class="nav__menu">
            <ul class="nav__menu-list">
              <li v-for="(item, index) of nav_list" :key="index" class="nav__menu-item dropdown">
                <template v-if="item.dropdown === true">
                    <a class="nav__menu-link btn-nav dropdown-toggle" @click="show = show === index ? null : index" :class="{ active: show }">
                      <span class="nav__menu-text">{{ $t(item.name) }}</span>
                    </a>
                    <transition name="slide">
                      <ul class="nested-drop dropdown-menu" v-if="show === index">
                        <li v-for="(item, index) of item.children" :key="index">
                          <template v-if="item.external === true">
                            <div @click="closeDropdown">
                              <a :href="item.route_link" target="_blank" class="c-footer__menu-link">
                                <span class="c-footer__menu-text">{{ $t(item.name) }} </span>
                              </a>
                            </div>
                          </template>
                          <template v-else>
                            <div @click="closeDropdown">
                              <nuxt-link :to="localePath(item.route_link)" class="c-footer__menu-link">
                                <span class="c-footer__menu-text">{{ $t(item.name) }} </span>
                              </nuxt-link>
                              </div>
                          </template>
                        </li>
                      </ul>
                    </transition>
                  </template>
                  <template v-else>
                  <nuxt-link :to="localePath(item.route_link)" class="nav__menu-link btn-nav">
                    <span class="nav__menu-text">{{ $t(item.name) }}</span>
                  </nuxt-link>
                </template>
              </li>
            </ul>
        </div>
        <div class="nav__languages">
          <button v-on:click="isHidden = !isHidden" class="nav__menu-lang_switch_trigger">{{ $i18n.locale }}<img src="/img/common/icons/arrow-down-white.svg" />
          </button>
          <div class="nav__menu-lang_switch_drop_down" v-if="isHidden" v-model="$i18n.locale">
            <p v-on:click="isHidden = !isHidden">
              <nuxt-link :click="$i18n.setLocaleCookie(locale)" v-for="locale in availableLocales" :key="locale.code" :to="switchLocalePath(locale.code) + '/'">{{ locale.name }}</nuxt-link>
            </p>
          </div>
          <a href="https://pkt.cash/1ea983ba3453631d914755e7ad96840d/overview" target="_blank" class="c-common-button c-common-button__filled">
            <span>Stake PKT</span>
          </a>
        </div>
        <div class="nav__menu_mobile">
          <div class="nav__burger" @click="showMenu()" ref="navbar"></div>
          <ul class="nav__menu-list" :class="this.showMobileMenu ? 'open-menu' : 'closed-menu'">
              <li v-for="(item, index) of nav_list" :key="index" class="nav__menu-item dropdown">
                <template v-if="item.dropdown === true">
                    <a class="nav__menu-link btn-nav dropdown-toggle" @click="showMobileDropdown = showMobileDropdown === index ? null : index">
                      <span class="nav__menu-text">{{ $t(item.name) }}</span>
                    </a>
                    <transition name="slide">
                      <ul class="nested-drop dropdown-menu" v-if="showMobileDropdown === index">
                        <li v-for="(item, index) of item.children" :key="index">
                          <template v-if="item.external === true">
                            <div @click="showMenuNested()">
                              <a :href="item.route_link" target="_blank" class="c-footer__menu-link">
                                <span class="c-footer__menu-text">{{ $t(item.name) }} </span>
                              </a>
                            </div>
                          </template>
                          <template v-else>
                            <div @click="showMenuNested()">
                              <nuxt-link :to="item.route_link" class="c-footer__menu-link">
                                <span class="c-footer__menu-text">{{ $t(item.name) }} </span>
                              </nuxt-link>
                            </div>
                          </template>
                        </li>
                      </ul>
                    </transition>
                  </template>
                  <template v-else>
                  <nuxt-link :to="item.route_link" class="nav__menu-link btn-nav">
                    <span class="nav__menu-text">{{ $t(item.name) }}</span>
                  </nuxt-link>
                </template>
              </li>
              <li class="nav_additional">
                <ul class="c-navigation__top_links_social">
                  <template>
                    <li v-for="(item, index) of social_links" :key="index" class="c-footer__menu-item">
                      <a :href="item.route_link" target="_blank" class="c-footer__menu-link">
                          <span class="c-footer__menu-text"><img :src="item.img" :alt="item.name" width="24" /></span>
                      </a>
                    </li>
                  </template>
                </ul>
              </li>
              <li class="nav_languages">
                <button v-on:click="isHidden = !isHidden" class="nav__menu-lang_switch_trigger">{{ $i18n.locale }}<img src="/img/common/icons/arrow-down-white.svg" /></button>
                <div class="nav__menu-lang_switch_drop_down" v-if="isHidden" v-model="$i18n.locale">
                  <p v-on:click="isHidden = !isHidden">
                    <nuxt-link :click="$i18n.setLocaleCookie(locale)" v-for="locale in availableLocales" :key="locale.code" :to="switchLocalePath(locale.code) + '/'">{{ locale.name }}</nuxt-link>
                  </p>
                </div>
              </li>
              <a href="https://pkt.cash/1ea983ba3453631d914755e7ad96840d/overview" target="_blank" class="c-common-button c-common-button__filled">
                <span>Stake PKT</span>
              </a>
            </ul>
        </div>
    </nav>
  </div>
</header>
</template>

<script>
import { isMobile } from 'mobile-device-detect';
const OFFSET = 60;
export default {
  name: "Header",
  data() {
    return {
      isHidden: false,
      nav_open: false,
      show: false,
      isBodyClassActive: false,
      showMobileMenu: false,
      showMobileDropdown: false,
      mClass: isMobile ? 'mobile_block' : '',
      showNavbar: true,
      lastScrollPosition: 0,
      scrollValue: 0,
      nav_list: [
        {
          name:"get_pkt.started_button",
          route_link: "/utility",
          dropdown: true,
          children: [
            {
              name:"Stake",
              route_link: "/stake",
            },
            {
              name:"header.utility",
              route_link: "/utility",
            },
            {
              name:"home.scroll_section_block_1_title",
              route_link: "/pkt-network",
            },
            // {
            //   name:"home.scroll_section_block_1_title",
            //   route_link: "/tech",
            // },
            {
              name:"header.pkt_cash",
              route_link: "/pkt-cash",
            },
            {
              name:"resources.heading_button_4",
              route_link: "https://docsend.com/view/ayf5d3tz5rymn8fv",
              external: true
            },
            {
              name:"goodnews.good_news",
              route_link: "/goodnews",
            },
          ]
        },
        {
          name:"footer_new.menu_2_title",
          route_link: "/build",
          dropdown: true,
          children: [
            {
              name:"header_new.dev_dev_center",
              route_link: "/developer-central",
            },
            // {
            //   name:"header_new.dev_dev_center",
            //   route_link: "/resources",
            // },
            {
              name:"header_new.dev_tech_docs",
              route_link: "https://docs.pkt.cash/",
              external: true
            },
            {
              name:"header.roadmap",
              route_link: "/roadmap",
            },
            // {
            //   name:"header.roadmap",
            //   route_link: "/build",
            // },
            {
              name:"header_new.dev_yellowpaper",
              route_link: "https://pkt.cash/PacketCrypt-2020-09-04.pdf",
              external: true
            },
            {
              name:"header.whitepaper",
              route_link: "https://docsend.com/view/prnv2q3bifzd44rt",
              external: true
            },
          ]
        },
        {
          name: "Network",
          route_link: "/stake",
          dropdown: true,
          children: [
            {
              name:"Infrastructure",
              route_link: "/infrastructure",
            },
            {
              name:"header.network_st",
              route_link: "/network-steward",
            },
            {
              name:"footer_new.wallets",
              route_link: "/wallet",
            },
            {
              name:"header.ecosystem",
              route_link: "/ecosystem",
            },
            {
              name:"Tokenomics",
              route_link: "https://docs.pkt.cash/tokenomics/tokenomics",
              external: true
            },
            {
              name:"header.cjdns",
              route_link: "/cjdns",
            },
            // {
            //   name:"Cjdns",
            //   route_link: "/origin-story",
            // },
          ]
        },
        {
          name:"footer_new.menu_4_title",
          route_link: "/tech",
          dropdown: true,
          children: [
            {
              name:"header.explorer",
              route_link: "https://packetscan.io/",
              external: true
            },
            {
              name:"header.community",
              route_link: "/community",
            },
            {
              name:"header.blog",
              route_link: "https://crypto.pkt.cash/",
              external: true
            },
            {
              name:"Media",
              route_link: "/media",
            }
          ]
        }
      ],
      social_links: [
        {
          name: "pkt.chat",
          route_link: "https://pkt.chat",
          img: "/img/common/icons/pkt-chat.svg",
        },
        {
          name: "Youtube",
          route_link: "https://www.youtube.com/c/PKTCash/",
          img: "/img/common/icons/youtube.svg",
        },
        {
          name: "Instagram",
          route_link: "https://www.instagram.com/pktcash/",
          img: "/img/common/icons/instagram.svg",
        },
        {
          name: "Twitter",
          route_link: "https://twitter.com/pktcash",
          img: "/img/common/icons/x.svg",
        },
        {
          name: "Discord",
          route_link: "https://discord.gg/bjJutHm9CN",
          img: "/img/common/icons/discord.svg",
        },
        {
          name: "Github",
          route_link: "https://github.com/pkt-cash/",
          img: "/img/common/icons/github.svg",
        }
      ],
    };
  },
  mounted () {
    this.lastScrollPosition = window.pageYOffset
    window.addEventListener('scroll', this.onScroll)
    const viewportMeta = document.createElement('meta')
    viewportMeta.name = 'viewport'
    viewportMeta.content = 'width=device-width, initial-scale=1'
    document.head.appendChild(viewportMeta)
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    onScroll () {
      if (window.pageYOffset < 0) {
        return
      }
      if (Math.abs(window.pageYOffset - this.lastScrollPosition) < OFFSET) {
        return
      }
      this.showNavbar = window.pageYOffset < this.lastScrollPosition
      this.lastScrollPosition = window.pageYOffset
    },
    showMenu() {
      this.showMobileMenu = !this.showMobileMenu;
      this.isBodyClassActive = !this.isBodyClassActive;
    },
    closeDropdown: function() {
      this.show = !this.show;
    },
    showMenuNested() {
      this.showMobileDropdown = !this.showMobileDropdown;
      this.showMobileMenu = !this.showMobileMenu;
    }
  },
  watch: {
    isBodyClassActive(newVal) {
      if (newVal) {
        document.body.classList.add("disableScroll");
      } else {
        document.body.classList.remove("disableScroll");
      }
    },
  },
  computed: {
    availableLocales () {
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
    }
  }
};
</script>

<style lang="scss">
.c-header {
  padding:rem(10) 0;
  position:absolute;
  top:0;
  left:0;
  width:100%;
  z-index:10;
  @include for-width(-tablet) {
    background: rgba(0, 5, 47, 0.5);
    backdrop-filter: blur(5px);
  }
  &:before {
    @include for-width(-small-lg) {
      content:'';
      position:absolute;
      top:0;
      left:0;
      height:100%;
      width:100%;
      display:block;
      filter: blur(5px);
      -webkit-filter: blur(5px);
    }
  }
  & .container {
    @include for-width(-desktop-med) {
      max-width:100%;
      padding:rem(10) rem(30);
    }
    @include for-width(-small-lg) {
      max-width:100%;
      padding:0 rem(15);
    }
    & .c-navigation {
      background-color: transparent;
      width:100%;
      @extend %df;
      @extend %jcsb;
      @extend %aic;
      position:relative;
      & > div {
        width:25%;
      }
      & .nav__logo img {
        vertical-align:middle;
        @include for-width(-desktop-medium) {
          max-width:rem(100);
        }
        @include for-width(-laptop_small) {
          max-width:rem(115);
        }
        @include for-width(-tablet) {
          position:relative;
          z-index:10;
        }
        @include for-width(-small-lg) {
          max-width:rem(75);
        }
      }
      & .nav__menu {
        width:auto;
        @include for-width(-tablet) {
          display: none;
        }
        &-list {
          @extend %df;
          @extend %jcc;
          @extend %aic;
          background-color:$black_blue_light;
          padding:0 rem(30);
          border-radius:60px;
          @include for-width(-desktop-medium) {
            padding:0 rem(24);
          }
        }
        &-item {
          @extend %t-center;
          & a {
            color:$white;
            font-size: rem(16);
            line-height: rem(20);
            @extend %inter_semibold;
            @extend %dib;
            padding:rem(20);
            @include for-width(-desktop-medium) {
              padding:rem(16) rem(20);
            }
          }
        }
        .nested-drop {
          position: absolute;
          top: 100%;
          margin-left:0;
          -webkit-backdrop-filter: blur(10px);
          backdrop-filter: blur(10px);
          box-shadow: 0 10px 10px rgba(0,0,0,.25);
          border-radius: 5px;
          background-color:$black_blue_light;
          padding: 0 0 rem(15);
          min-width: 15vw;
          border:1px solid $black_blue;
          & li {
            padding:rem(15) rem(20) 0;
            @extend %t-left;
            & a {
              color: $white;
              @extend %p-common;
              padding:0;
              @include for-width(-laptop) {
                font-size: rem(14);
              }
            }
          }
          @include for-width(-tablet) {
            position: relative;
            top: 0;
            margin-left:0;
          }
        }
      }
      & .nav__languages {
        width:auto;
        position:absolute;
        right:0;
        @include for-width(-tablet) {
          display: none;
        }
        & .nav__menu-lang_switch_trigger {
          background:$black_blue_light;
          backdrop-filter: blur(5px);
          border-radius: 60px;
          color:$white;
          @extend %inter_semibold;
          font-size: rem(16);
          text-transform:uppercase;
          padding:rem(20) rem(30);
          margin-right:rem(16);
          @include for-width(-desktop-medium) {
            padding:rem(16) rem(30);
          }
          & img {
            vertical-align:middle;
            margin-left:rem(10);
          }
        }
        & .nav__menu-lang_switch_drop_down {
          position:absolute;
          top: 102%;
          left:0;
          -webkit-backdrop-filter: blur(10px);
          backdrop-filter: blur(10px);
          box-shadow: 0 10px 10px rgba(0, 0, 0, 0.25);
          border-radius: 5px;
          background-color: $black_blue_light;
          width:100%;
          min-width:rem(150);
          padding:rem(5) 0;
          @include for-width(-laptop) {
            min-width:rem(110);
          }
          & p {
            & a {
              @extend %db;
              @extend %t-left;
              padding:rem(5) rem(10) rem(5) rem(30);
              color:$white;
              @include for-width(-laptop) {
                padding:rem(5) rem(10);
                font-size: rem(14);
              }
            }
          }
        }
        & .c-common-button {
          padding:rem(13.75) rem(23);
          @include for-width(-desktop-medium) {
            padding:rem(9.75) rem(23);
          }
        }
      }
      & .nav__menu_mobile {
        @extend %t-right;
        & .nav__burger {
          display: none;
          cursor: pointer;
          z-index: 10;
          position:relative;
          background-image:url(/img/common/icons/mobile_menu.svg);
          background-repeat:no-repeat;
          background-position:center center;
          background-size:contain;
          height:rem(40);
          width:rem(80);
          margin-right:0;
          margin-left:auto;
          @include for-width(-tablet) {
            display: block;
          }
        }
        & .nav__menu-list {
          display: none;
          z-index: 9;
          position: fixed;
          top:0;
          left:0;
          width:100vw;
          height:100vh;
          border-radius:0;
          padding: 1.5625rem 2.1875rem;
          background-color: $dark_blue_new;
          padding-bottom:15vh;
          transform: scaleX(0);
          transform-origin: right;
          transition: 0.3s all ease;
          @extend %jcc;
          @extend %aic;
          @extend %fdc;
          @include for-width(-tablet) {
            display: -webkit-flex;
            display: -moz-flex;
            display: -ms-flex;
            display: -o-flex;
            display: flex;
            justify-content: center;
            -ms-align-items: center;
            align-items: center;
          }
          @include for-width(-small-lg) {
            padding-bottom:rem(100);
          }
          & .nav__menu-item {
            @extend %t-center;
            & a {
              color:$white;
              font-size: rem(20);
              line-height: rem(30);
              @extend %inter_semibold;
              padding:rem(5);
              @include for-width(-small-lg) {
                padding:rem(3) 0;
              }
            }
            & .nested-drop {
              margin:rem(5) 0 rem(25);
              @include for-width(-small-lg) {
                margin:0 0 rem(10);
              }
              & li a {
                color:$white;
                font-size: rem(16);
                line-height: rem(26);
                @extend %inter_regular;
                padding:rem(5);
                @include for-width(-small-lg) {
                  padding:0;
                }
              }
            }
          }
        }
        & .open-menu {
          transform: scaleX(1);
        }
        & .closed-menu {
          transform: scaleX(0);
          transform-origin: right;
          transition: 0.3s all ease;
        }
        & .nav_additional {
          position:absolute;
          bottom:15vh;
          left:0;
          right:0;
          margin: 0 auto;
          @extend %t-center;
          @include for-width(-small-lg) {
            bottom:rem(115);
          }
          & .c-navigation__top_links_social {
            width:100%;
            @extend %df;
            @extend %jcc;
            @extend %aic;
            padding:rem(25) 0 rem(10);
            & .c-footer__menu-text {
              width: 40px;
              height: 40px;
              line-height: 40px;
              @extend %db;
              @extend %t-center;
              margin-right:rem(20);
              background-color:rgba(255,255,255,.15);
              border-radius:rem(50);
              @include for-width(-laptop_small) {
                width: rem(36);
                height: rem(36);
                line-height: rem(36);
                margin-right:rem(12);
              }
              @include for-width(-small-lg) {
                width: 40px;
                height: 40px;
                line-height: 40px;
              }
            }
            & img {
              width:24px;
              height: 20px;
              object-fit:contain;
              object-position:center;
              vertical-align:middle;
              @include for-width(-laptop_small) {
                width:20px;
                height:18px;
              }
              @include for-width(-small-lg) {
                width:24px;
                height: 20px;
              }
            }
          }
        }
        & .nav_languages {
          padding-top:rem(20);
          padding-bottom:rem(20);
          @extend %t-center;
          & .nav__menu-lang_switch_trigger {
            color:$white;
            font-size: rem(18);
            line-height: rem(26);
            @extend %inter_semibold;
            text-transform:uppercase;
            & img {
              margin-left:rem(10);
              vertical-align:middle;
            }
          }
          & .nav__menu-lang_switch_drop_down {
            & p a {
              color:$white;
              font-size: rem(16);
              line-height: rem(26);
              @extend %inter_medium;
              @extend %db;
              @extend %t-center;
              padding:rem(5) rem(10);
              color:$white;
            }
          }
        }
      }
    }
  }
}
.slide-enter-active {
  transition: all .35s;
  opacity: 1;
}
.slide-enter {
  transform: none;
  opacity:0;
  transition: none;
}
.slide-leave-to {
  transform: none;
  opacity:0;
  transition: none;
}
.disableScroll {
  overflow:hidden;
}
.ru {
  & .c-header {
    & .nav__menu-list {
      & .nav__menu-item a {
        white-space: nowrap;
      }
    }
  }
}
</style>