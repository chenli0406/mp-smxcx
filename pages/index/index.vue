<template>
	<view class="content">
	  <!-- <uni-list>
	       <uni-list-item :title= "item.name" v-for="(item, index) in songList" :key="item.id">
	       </uni-list-item>
	   </uni-list> -->
			<van-button type="default" @click="getGoto">默认按钮</van-button>
		 <van-button  @click="getPagesA">pagesA</van-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			
				autoCode: '', //自动登录的code
				wxAutoInfo: '' //用户授权信息
				
			}
		},
		onLoad() {
			 // setTimeout(function () {
			 //            console.log('start pulldown');
			 //      }, 1000);
			 //  uni.startPullDownRefresh();
			// this.$api.banner({}).then((res)=>{
			// 	 console.log("111")
			// 	  console.log(res)
			// })
			wx.login({
				success(res) {
					if (res.code) {
						console.log(res)
						wx.getSetting({
							success(res) {
								if (res.authSetting['scope.userInfo']) {
									wx.getUserInfo({
										success: res => {
										 console.log(res)
										 
										}  
									});
								}
							}
						});
					}
				}
			});
		},
		onPullDownRefresh() {
		        console.log('refresh');
		        setTimeout(function () {
		            uni.stopPullDownRefresh();
		        }, 1000);
		},
		methods:{
		  getGoto(){
				uni.navigateTo({
					url: "../pagesB/set/set"
				})
			},
			getPagesA(){
				uni.navigateTo({
					url: "../pagesA/home/home"
				})
			}
		 }
	
	}
</script>

<style lang="scss">
</style>