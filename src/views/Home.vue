<template>
  <div class="container">
   
     <section class="vote">
 	<h3 class="give-your-vote">Silahkan berikan penilaian anda terhadap pelayanan kami
 	</h3>

 	<div class="emoticons">
 		<Vote :voteProp="vote"/>
 	</div>
 </section>
<section class="finish">
	<transition name="fade" v-on:after-enter="Reset">

	<h4 v-if="show">Terimakasih telah mmenilai layanan kami bruh</h4>
</transition>
</section>
  </div>
</template>

<script>
// @ is an alias to /src
import Vote from "@/components/Vote.vue";

export default {
  name: "Home",
  data: function(){
  	return{
  		show:false
  	}
  },
  components: {
  Vote
  },
 methods:{
 	vote(){
 		this.show=true;
 	},
 	Reset(){
 		this.show=false;
 		this.$root.$emit('emitproccessDone')
 	}
 } 
};
</script>
<style type="text/css">
	.fade-enter-active, .fade-leave-active {
  transition: opacity .9s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
	.container{
		display: flex;
		flex-wrap: wrap;
		height: 100vh;
		align-items: center;
	}
	section{
		width: 100%;
	}
	.give-your-vote{
		font-size: 21px;
	}
	.emoticons{
		display: flex;
		justify-content: center;
	}
	.finish{
		position: absolute;
		bottom: 20px;
	}
</style>