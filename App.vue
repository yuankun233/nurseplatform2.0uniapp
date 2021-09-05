<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	@import "uview-ui/index.scss";

	// body,html{
	// 	height: 97%;
	// }
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	// 解决边距塌陷
	uni-page-wrapper{
		overflow: hidden;
	}
</style>
