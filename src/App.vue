<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    	<shouye ref="swiperRef" :imgData="girl"></shouye>
    <!--<router-view/>-->
  </div>
</template>

<script>
	import shouye from './components/shouye'

export default {
  name: 'App',
  data(){
  	return{
  		num:0,
  		i:'',
  		girl: []
  	}
  },
  components:{
  	shouye
  },
  mounted(){
//	console.log(this.item)
  },
created(){
	this.$axios.get('/api/girl')
	.then(res=>{
		res=res.data
		if(res.errno === 0){
			this.girl = res.data
      this.$refs.swiperRef.imgs = this.girl
		}
	})
}
}

</script>

<style>
#app {
  /*font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;*/
}
</style>
