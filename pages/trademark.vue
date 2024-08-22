<template>
  <div class="v-trademark">
    <section class="v-header-section">
      <SpotAInternal 
      :title="this.$t('trademark.heading')"
       />
    </section>
    <section class="v-trademark-section">
		<div class="container">
			<p class="v-trademark-section__text">{{ $t("trademark.subtitle_1") }} <a :href="localePath('brand')">{{ $t("trademark.subtitle_2") }}</a> {{ $t("trademark.subtitle_3") }}:</p>
			<ol>
				<li>{{ $t("trademark.free_use_list_item_1") }}</li>
				<li>{{ $t("trademark.free_use_list_item_2") }}</li>
				<li>{{ $t("trademark.free_use_list_item_3") }}</li>
				<li>{{ $t("trademark.free_use_list_item_4") }}</li>
			</ol>
			<p class="v-trademark-section__text">{{ $t("trademark.notices") }}:</p>
			<ul>
				<li>{{ $t("trademark.notices_list_item_1") }}</li>
				<li>{{ $t("trademark.notices_list_item_2") }}</li>
				<li>{{ $t("trademark.notices_list_item_3") }} <a href="https://pkt.chat" target="_blank">http://pkt.chat</a></li>
				<li>{{ $t("trademark.notices_list_item_4") }}</li>
				<li>{{ $t("trademark.notices_list_item_5") }}</li>
			</ul>

			<h4 class="v-trademark-section__list-title">{{ $t("trademark.uses") }}</h4>
			<p class="v-trademark-section__text">{{ $t("trademark.you_may") }}:</p>
			<ul>
				<li>{{ $t("trademark.you_may_text") }}</li>
				<li>{{ $t("trademark.you_may_text_2") }}</li>
			</ul>
			
			<h4 class="v-trademark-section__list-title">{{ $t("trademark.unacceptable_uses") }}</h4>
			<p class="v-trademark-section__text">{{ $t("trademark.specific_things") }}:</p>
			<ul>
				<li>{{ $t("trademark.specific_item_1") }}</li>
				<li>{{ $t("trademark.specific_item_2") }}</li>
			</ul>
		</div>
    </section>
  </div>
</template>

<script>
import SpotAInternal from "~/components/Common/SpotAInternal";
export default {
  components: {
    SpotAInternal,
  },
  head() {
    return {
      title: "Trademark | PKT Cash",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t("trademark.meta_title")
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Trademark | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.$t("trademark.meta_title")
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
.v-trademark {
  background-color:$black_blue;
  position:relative;
  background-image:url(/img/media-top-asset.webp);
  background-size:rem(750);
  background-position:top right;
  background-repeat:no-repeat;
  @include for-width(-desktop-lg) {
    background-size:rem(600);
  }
  @include for-width(-small-lg) {
    background-size:rem(300);
    background-position:top 50px right -50px;
  }
  & > section {
    z-index:3;
    position:relative;
  }
  & .c-spot-a-internal {
	@include for-width(-tablet) {
		padding-bottom:rem(50);
	}
    @include for-width(-small-lg) {
      padding-top:rem(100);
	  padding-bottom:rem(10);
    }
  }
  & .v-trademark-section {
	padding-bottom:rem(100);
	@include for-width(-small-lg) {
		padding-bottom:rem(50);
	}
	&__text {
		@extend %p-big-common;
		margin-bottom:rem(25);
		color:$white;
		@include for-width(-tablet) {
		  margin-bottom: rem(10);
		}
	}
	& a {
		color:$green;
		&:hover {
			color:$green;
		}
		&:focus {
			color:$green;
		}
		&:visited {
			color:$green;
		}
	}
	&__list-title {
		font-size: rem(20);
		line-height: rem(30);
		@extend %inter_bold;
		color:$white;
		@include for-width(-small-lg) {
			font-size: rem(18);
			line-height: rem(24);
			margin-bottom:rem(25);
		}
	}
	&__list-subtitle {
		font-size: rem(20);
		line-height: rem(30);
		@extend %inter_bold;
		color:$white;
		@include for-width(-small-lg) {
			font-size: rem(18);
			line-height: rem(24);
			margin-bottom:rem(25);
		}
	}
	& ol,& ul {
		padding-left: rem(50);
		@extend %p-big-common;
		color:$white;
		margin-bottom: rem(20);
	}
	& ol li {
		display:list-item;
		list-style-type: decimal;
	}
	& ul li {
		display:list-item;
		list-style-type: disc;
	}
	& ul ul li {
		list-style-type: circle;
	}
  }
}
</style>