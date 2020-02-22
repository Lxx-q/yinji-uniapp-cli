
<template>
	<!--真正意义上的主页面 -->
	<view>
		<web-view :src="baseUrl"></web-view>
	</view>
</template>

<script>
	/**
	 * 初始化 url的方法 initUrl 关键字【 INIT_URL_KEY]
	 */
	export default {
		data() {
			return {
				baseUrl:"http://localhost:8080/yinji/page/index/main",
				data:{}
			}
		},
		methods: {
			buildUrl:function( baseUrl , data ){ //生成对应的url的方法
				
				var urlBuilder = baseUrl ;
				
				if( this.isNull(data)){
					var first = false;
					for( key in data ){
						if( !first ){
							urlBuilder = urlBuilder + "?";
						}else{
							urlBuilder = urlBuilder + "&";	
						}
						var val = data[key];
						urlBuilder = urlBuilder + key 
					}
				}
				//暂时的操作
				return this.baseUrl;
			},isNull:function( val ){ // 判断一个值是否为空
				return val != undefined && val != null
			},init:function(){
				//初始化方法 ， 转载着初始化的方法
				this.initUrl();
			},initUrl:function(){ // 下面便是初始化 initUrl 的方法 INIT_URL_KEY
				var url = this.buildUrl(this.baseUrl , this.data );
				this.url = url;
			}
			
		},onLoad:function(){
			this.init();
			//初始化方法
			console.log(this.url);
		}
	}
</script>

<style>

</style>
