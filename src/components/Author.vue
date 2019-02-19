<template>
   <div v-if="user && user.length">
   	 <p id="side" class="btn btn-link">@{{user[0].name}}</p>
   </div>
</template>

<script>
import axios from 'axios'
	export default{
		props: ['data'],
   data(){
      return{
      	user: null
      }
   },
	mounted(){

  if(this.data){
  			axios.get('https://jsonplaceholder.typicode.com/users?id='+this.data.id)
  				.then((response)=>this.user=response.data)
  }
	},
methods: {

	}
}

</script>
<style>
#side{
		margin-left: 900px
	}
</style>
