<template>
  <div id="app">
		<div class="header">
			<v-header :seller="seller"></v-header>
		</div>
		<div class="tab border-1px">
			<div class="tab-item"><router-link to="/goods">商品</router-link></div>
			<div class="tab-item"><router-link to="/ratings">评论</router-link></div>
			<div class="tab-item"><router-link to="/seller">商家</router-link></div>
		</div>
		<div class="content">
      <keep-alive><router-view :seller="seller"></router-view> </keep-alive>
		</div>
  </div>
</template>

<script>
	import header from './components/headeer/header.vue';
  import {urlParse} from './common/js/util.js'
  import data from './common/json/data.json'
	// const ERR_OK=0;
	export default {
	  name: 'App',
	  data() {
	  	return {
	  		seller:{
	  		  id:(() =>{
	  		    let queryParam =urlParse();
              return queryParam.id
            }
          )()
        }
	  	}
	  },
	  created() {
	  //   const url ='http://ustbhuangyi.com/sell/api/seller'
	  // 	this.$http.get('/api/seller'+ '?id=' + this.seller.id).then((response) => {
		// 	response=response.body;
		// 	if(response.errno===ERR_OK){
		// 		this.seller=response.data;
    //     this.seller = Object.assign({}, this.seller, response.data)
    //      console.log(this.seller.id)
		// 	}
		// })
      this.seller =data.seller
    },
	  components: {
	  	"v-header":header
	  },

	}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
	@import "./common/stylus/mixin.styl"

	#app{
		.tab{
			display:flex;
			width:100%;
			height:40px;
			line-height:40px;
			border-1px(rgba(7,17,27,0.1))
			.tab-item{
				flex:1;
				text-align:center;

				a{
					display:block;
					font-size:14px;
					color:rgb(77,85,93);
				}
				a.router-link-exact-active{
					color:rgb(240,20,20);
				}
			}
		}
	}

</style>
