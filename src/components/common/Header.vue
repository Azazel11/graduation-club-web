<template>
	<div>
		<div class="header-wrap">
			<el-menu :default-active="activeIndex" class="header computerNav" background-color="#9a0e14" mode="horizontal" text-color="#fff" active-text-color="#ffd04b">
				<el-menu-item index="1"><router-link :to="{ name: 'Home' }">首页</router-link></el-menu-item>
				<el-submenu index="2">
					<template slot="title">
						社团概况
					</template>
					<el-menu-item index="2-1"><router-link :to="{ name: 'Passage', params: { id: 115 } }">社团联简介</router-link></el-menu-item>
				</el-submenu>
				<el-submenu index="3">
					<template slot="title">
						社团快讯
					</template>
					<el-menu-item index="3-1"><router-link :to="{ name: 'PassageList', query: { passageTypeId: 1 } }">重要通知</router-link></el-menu-item>
					<el-menu-item index="3-2"><router-link :to="{ name: 'PassageList', query: { passageTypeId: 2 } }">社团要闻</router-link></el-menu-item>
          <el-menu-item index="3-3"><router-link :to="{ name: 'PassageList', query: { passageTypeId: 4 } }">社团招新</router-link></el-menu-item>
        </el-submenu>
				<el-submenu index="4">
					<template slot="title">
						社团风采
					</template>
					<el-menu-item index="4-1"><router-link :to="{ name: 'ActivityList', query: { typeId: 1 } }">活动预告</router-link></el-menu-item>
					<el-menu-item index="4-2"><router-link :to="{ name: 'ActivityList', query: { typeId: 2 } }">精彩活动回顾</router-link></el-menu-item>
				</el-submenu>
				<el-menu-item index="5"><router-link :to="{ name: 'ClubList', query: { typeId: 1 } }">社团检索</router-link></el-menu-item>
				<el-menu-item index="6"><router-link :to="{ name: 'FileList', query: { fileTypeId: 3 } }">资料下载</router-link></el-menu-item>
				<el-submenu index="7">
					<template slot="title">
						社团反馈
					</template>
					<el-menu-item index="7-1">
						<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=947705747&site=qq&menu=yes">
							<img border="0" src="http://wpa.qq.com/pa?p=2:947705747:51" alt="点击这里给我发消息" title="QQ交流" />
						</a>
					</el-menu-item>
					<el-menu-item index="7-2">
            <a target="_blank" href="http://mail.qq.com/cgi-bin/qm_share?t=qm_mailme&email=1_7j4ODn4uDj4Jempvm0uLo" style="text-decoration:none;">
              <img src="http://rescdn.qqmail.com/zh_CN/htmledition/images/function/qm_open/ico_mailme_02.png"/>
            </a>
					</el-menu-item>
				</el-submenu>
				<el-menu-item index="8" class="rightMenu"><a href="#" @click="goAdminUrl">登录</a></el-menu-item>
			</el-menu>
		</div>
	</div>
</template>

<script>
const OK = 200;
export default {
	data() {
		return {
			activeIndex: '1',
			adminAccessUrl: 'http://118.89.228.250:8012'
		};
	},
	methods: {
		getAdminUrl: function() {
			this.$axios.get('/api/system/adminUrl').then(res => {
				if (res.data.code == OK) {
					this.adminAccessUrl = res.data.data;
				}
			});
		},
		goAdminUrl: function() {
			// window.location.href = this.adminAccessUrl
			window.open(this.adminAccessUrl, '_blank');
		}
	},
	created: function() {
		this.getAdminUrl();
	},
	mounted: function() {}
};
</script>

<style scoped="scoped">
.header-wrap {
	background-color: #9a0e14;
	min-width: 1024px;
}
.phone-nav {
		display: none;
	}
.header {
	width: 1024px;
	height: 70px;
	line-height: 70px;
	margin: 0 auto;
}

.el-menu.el-menu--horizontal a {
	color: #fff;
}
.rightMenu {
	float: right;
	height: 70px;
	line-height: 70px;
	background-color: #000000;
}
a {
	text-decoration: none;
	color: #eee;
	font-size: 16px;
}
/* @media screen and (min-width: 1196px) {
	.phone-nav {
		display: none;
	}
} */
/* @media screen and (max-width: 600px) {
	.computerNav {
		display: none;
	}
	.phone-nav {
		display: block;
	}
} */
</style>
