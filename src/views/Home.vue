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
	<transition name="fade">

	<h4 v-if="show">Terimakasih bruh</h4>
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
 	}
 } 
};
</script>
<style type="text/css">
	.fade-enter-active, .fade-leave-active{
		transition: opacity .5s;
	}
	.fade-enter, .fade-leave-to{
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