<template>
  <div class="buttons">
   <button v-for="(emoticons, index) in emoticons"
   :key="index"
   :id="emoticons"
   :value="emoticons"
   class="btn-emoticon"
   :class="{active:emoticons == emoticonsClick}"
   :disabled="isDisable"
   @click="vote">
   
   </button>
 
  </div>
</template>

<script>
// @ is an alias to /src
import moment from "moment";

export default {
  name: "Vote",
  props: {
  	voteProp :{
  		type : Function
  	}
   },
  data: function () {
  	return{
  		emoticons:['very-bad','bad','ok','good','very-good'],
  		emoticonsClick:''
  	}
  },
  methods:{

  	vote(e){
  		var voted = e.target.value;
  		this.isDisable=true;
  		this.emoticonsClick=voted;
  		var waktu = moment().format('DD-MM-YYYY hh:mm:ss '); // January 9th 2021, 11:21:23 am
  		var keyStorage = moment().format('DDMMYYYYhhmmss ');

  		var data={
  			vote: voted,
  			create_at : waktu
  		}
  	
  		var jsonToString = JSON.stringify(data);
  		
  		localStorage.setItem(keyStorage,jsonToString);
  		this.voteProp();
  	}
  },
  computed:{
  	isDisable : function(){
  		return this.emoticonsClick.length === 0? false : true;
  	}
  }

};
</script>
<style type="text/css">
	.buttons{
		display: flex;
		
	}
	.btn-emoticon{
		background: url('~@/assets/emoticon.png');
		width: 101px;
		height: 100px;
		border: none;
		margin: 0px 10px;
		outline: none;
		cursor: pointer;

	}
	#very-bad{
		background-position: 0px 0px;
	}
	#very-bad:hover{
		background-position: 0px -100px;
	}
	#very-bad.active,
	#very-bad:active{
		background-position: 0px -200px;
	}	
	#bad{
		background-position: -101px 0px;
	}
	#bad:hover{
		background-position: -101px -100px;
	}	
	#bad.active,
	#bad:active{
		background-position: -101px -200px;
	}	
	#ok{
		background-position: -202px 0px;
	}
	#ok:hover{
		background-position: -202px -100px;
	}	
	#ok.active,
	#ok:active{
		background-position: -202px -200px;
	}
	#good{
		background-position: -303px 0px;
	}
	#good:hover{
		background-position: -303px -100px;
	}	
	#good.active,
	#good:active{
		background-position: -303px -200px;
	}	
	#very-good{
		background-position: -404px 0px;
	}
	#very-good:hover{
		background-position: -404px -100px;
	}	
	#very-good.active,
	#very-good:active{
		background-position: -404px -200px;
	}
</style>