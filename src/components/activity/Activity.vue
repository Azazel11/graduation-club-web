<template>
	<div class="" v-if="activity != null">
		<div class="title">{{ activity.activityName }}</div>
		<div class="wrap">
			<div class="time">
				活动举办时间:
				<span>{{ activity.holdTime }}</span>
			</div>
			<div class="site">
				活动举办地点:
				<span class="info">{{ activity.site }}</span>
			</div>
		</div>
		<div v-html="activity.introduce" class="introduce"></div>
		<Share class="down"></Share>
	</div>
</template>

<script>
import Share from '@/components/common/Share.vue';
const OK = 200;
export default {
	data() {
		return {
			activity: {},
			// fileList: []
		};
	},
	components: { Share },
	methods: {
		get: function() {
			var id = this.$route.params.id;
			this.$axios.get('/api/activities/' + id).then(res => {
				console.log(res.data);
				if (res.data.code == OK) {
					this.activity = res.data.data;
					// this.fileList = this.activity.fileList;
				} else {
					this.$layer.alert(res.data.data);
				}
			});
		},
		// isImage: function(fileName) {
		// 	var ext = fileName.substring(fileName.lastIndexOf('.') + 1);
		// 	if (ext == 'png' || ext == 'jpg') {
		// 		return true;
		// 	}
		// 	return false;
		// }
	},
	created() {
		this.get();
	},
	watch: {
		$route(to, from) {
			this.get();
		}
	}
};
</script>

<style scoped="scoped">
.title {
	display: block;
	font-size: 24px;
	color: #9a0e14;
	margin-top: 10px;
}
.wrap {
	float: right;
}
.time {
	margin-right: 100px;
	line-height: 20px;
}
.site {
	margin-right: 100px;
}
.site span {
	padding-left: 20px;
	font-size: 18px;
}
.introduce {
	line-height: 150%;
	padding: 50px;
	text-indent: 5px;
	/*text-align: left;*/
}
.down{
  /*bottom: auto;*/
}
</style>
