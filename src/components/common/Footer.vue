<template>
	<div class="fooetr-wrap">
		<div class="fooetr">
			<p>欢迎访问社团管理系统</p>
			<p>这是一个简单的毕设作品</p>
			<p>Copyright RF All rights reserved.</p>
		</div>

	</div>
</template>

<script>
	export default {

	}
</script>

<style scoped="scoped">
	.fooetr-wrap {
		background-color:#9a0e14 ;
		min-width: 1024px;
	}

	.fooetr-wrap .fooetr {
		width: 1024px;
		margin: 0 auto;
		height: 70px;
	}
	.fooetr-wrap .fooetr p{
		line-height: 16px;
	}

	@media screen and (max-width: 600px){
	  .fooetr-wrap {
	  	padding: 2px 15px;
	  }
	}
</style>
