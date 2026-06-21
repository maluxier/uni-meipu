<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
			this.syncTabBarMarks()
		},
		onShow: function() {
			console.log('App Show')
			this.syncTabBarMarks()
		},
		onHide: function() {
			console.log('App Hide')
		},
		methods: {
			syncTabBarMarks() {
				setTimeout(function() {
					uni.setTabBarBadge({
						index: 1,
						text: '3'
					})
					uni.showTabBarRedDot({
						index: 2
					})
				}, 100)
			}
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
