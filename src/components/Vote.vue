<template>
  <div class="buttons">
   <button v-for="(emoticons, index) in emoticons"
   :key="index"
   :id="emoticons"
   :value="emoticons"
   class="btn-emoticon"
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
  components: { },
  data: function () {
  	return{
  		emoticons:['very-bad','bad','ok','good','very-good'],isDisable: false
  	}
  },
  methods:{

  	vote(e){
  		this.isDisable=true;
  		var voted = e.target.value;
  		var waktu = moment().format('DD-MM-YYYY hh:mm:ss '); // January 9th 2021, 11:21:23 am
  		var keyStorage = moment().format('DDMMYYYYhhmmss ');

  		var data={
  			vote: voted,
  			create_at : waktu
  		}
  	
  		var jsonToString = JSON.stringify(data);
  		
  		localStorage.setItem(keyStorage,jsonToString);
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
	}	#very-bad:active{
		background-position: 0px -200px;
	}	
	#bad{
		background-position: -101px 0px;
	}
	#bad:hover{
		background-position: -101px -100px;
	}	#bad:active{
		background-position: -101px -200px;
	}	
	#ok{
		background-position: -202px 0px;
	}
	#ok:hover{
		background-position: -202px -100px;
	}	#ok:active{
		background-position: -202px -200px;
	}
	#good{
		background-position: -303px 0px;
	}
	#good:hover{
		background-position: -303px -100px;
	}	#good:active{
		background-position: -303px -200px;
	}	
	#very-good{
		background-position: -404px 0px;
	}
	#very-good:hover{
		background-position: -404px -100px;
	}	#very-good:active{
		background-position: -404px -200px;
	}
</style>