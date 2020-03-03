<template>
	<div class="share">
    <el-aside width="120px" class="aside h">
      <a href="#" @click="qqFriend" class="qqFriend"><img :src="logoUrl1" class="logo" alt="" ></a>
      <a href="#" @click="qqZone" class="qqZone"><img :src="logoUrl2" class="logo" alt="" ></a>
      <a href="#" @click="sinaWeiBo" class="sinaWeiBo"><img :src="logoUrl3" class="logo" alt=""></a>
    </el-aside>
	</div>
</template>

<script>

  import logo1 from "@/assets/1.png";
  import logo2 from "@/assets/2.png";
  import logo3 from "@/assets/3.png";

export default {
	data() {
	return{
	  requstUrl:'',
    logoUrl1: logo1,
    logoUrl2: logo2,
    logoUrl3: logo3
	  }
	},
	methods: {
		//qq好友分享
		qqFriend: function() {
			var p = {
				/*获取URL，可加上来自分享到QQ标识，方便统计*/
				url: this.requstUrl,
				desc: '',
				//分享标题(可选)
				title: '好的网站，一起分享',
				/*分享摘要(可选)*/
				summary: '还不赶紧点击进来观看',
				/*分享图片(可选)*/
				pics: '',
				/*视频地址(可选)*/
				flash: '',
				/*分享来源(可选) 如：QQ分享*/
				site: '',
				style: '201',
				width: 32,
				height: 32
			};
			var s = [];
			for (var i in p) {
				s.push(i + '=' + encodeURIComponent(p[i] || ''));
			}
			var url = "http://connect.qq.com/widget/shareqq/index.html?" + s.join('&');
			window.open(url);
		},
		qqZone: function() {
			var p = {
				url: this.requstUrl,
				showcount: '1' /*是否显示分享总数,显示：'1'，不显示：'0' */,
				desc: '' /*默认分享理由(可选)*/,
				summary: '还不赶紧点击进来观看' /*分享摘要(可选)*/,
				title: '好的网站，一起分享',
				site: 'this.requstUrl' /*分享来源 如：腾讯网(可选)*/,
				pics: '',
				style: '203',
				width: 98,
				height: 22
			};
			var s = [];
			for (var i in p) {
				s.push(i + '=' + encodeURIComponent(p[i] || ''));
			}
			var url = "http://sns.qzone.qq.com/cgi-bin/qzshare/cgi_qzshare_onekey?" + s.join('&');
			window.open(url);
		},
		sinaWeiBo: function() {
			var p = {
				// 表示是否显示当前页面被分享数量(1 显示)(可选， 允许为空)
				count: '1',
				//将页面地址转成短域名， 并显示在内容文字后面。(可选， 允许为空)
				url: this.requstUrl,
				//用于发布微博的来源显示， 为空则分享的内容来源会显示来自互联网。(可选， 允许为空)
				appkey: '',
				//分享时所示的文字内容， 为空则自动抓取分享页面的title值(可选， 允许为空)
				title: '好的网站，一起分享',
				//自定义图片地址， 作为微博配图(可选， 允许为空)
				pic: '',
				//转发时会 @相关的微博账号(可选， 允许为空)
				ralateUid: '',
				//语言设置(zh_cn | zh_tw)(可选)
				language: 'zh_cn'
			};

			var s = [];
			for (var i in p) {
				s.push(i + '=' + encodeURIComponent(p[i] || ''));
			}
			var url = "http://service.weibo.com/share/share.php?" + s.join('&');
			window.open(url);
		}
	},
	created() {
		this.requstUrl = window.location.href;
	},
};
</script>

<style>
	.share{
		position: absolute;
		bottom: 110px;
		right: 200px;
	}
	.qqFriend{
		 /*background:url(/static/share.jpg) ; */
	}
  .logo {
    width: 40px;
    height: 40px;
    display: block;
    background-color: #fff;
    border-radius: 50%;
    margin: 25px auto;
  }
	@media screen and (max-width: 600px){
	  .share{
	  	position: absolute;
	  	bottom: 20px;
	  	right: 20px;
	  }
	}
</style>
