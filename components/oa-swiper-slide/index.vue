<template>
	<view class="oa-swiper-slide">
		<slot name="header" v-if="list.length > 0"></slot>
		<swiper
			class="oa-swiper"
			:indicator-dots="indicatorDots"
			:autoplay="autoplay"
			:interval="interval"
			:duration="duration"
			vertical="true"
		>
			<swiper-item
				class="oa-swiper-item"
				@tap="navTo"
				v-for="(item, index) in list"
				:key="index"
			>
				<view class="text in1line">
					<text class="newsTitle">{{
						item.title || `${item.member_nickname} 拼团成功`
					}}</text>
				</view>
				<text class="iconfont iconyou"></text>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
export default {
	name: 'oa-swiper-slide',
	data() {
		return {
			indicatorDots: false,
			autoplay: true,
			interval: 2000,
			duration: 500
		};
	},
	props: {
		list: {
			type: Array,
			default() {
				return [];
			}
		}
	},
	methods: {
		navTo() {
			this.$emit('navTo');
		}
	}
};
</script>

<style scoped lang="scss">
.oa-swiper-slide {
	display: flex;
	justify-content: space-between;
	align-items: center;
	height: 80upx;
	padding: 0 $spacing-lg;
	background-color: $color-white;
	.oa-swiper {
		height: 100%;
		flex: 1;
		margin-left: 30upx;
		.oa-swiper-item {
			display: flex;
			justify-content: space-between;
			.text,
			.iconfont {
				height: 80upx;
				line-height: 80upx;
			}
			.iconfont {
				color: $font-color-light;
			}
		}
	}
}
</style>
