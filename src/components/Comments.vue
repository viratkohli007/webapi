<template>
	<div>
    <div class="container card" v-if="com && com.length" >
    	<div >
    	<div class="card-body text-center"><b>{{this.data.title}}</b><br>post</div>
    	<div class="card-body">
    		 {{this.data.body}}
    	</div>
    	<div class="card-body" v-for="comm in com" >
    		 {{comm.body}}
    		 <!-- {{this.data.id}} -->
    	</div>

    	</div>
     </div>
    </div>
	</div>
</template>

<script >
import axios from 'axios'
	export default{
		props: ['data'],
  data(){
  		console.log(this.data.body, '---')

  	return{
     com:null
  	}
  },
  mounted(){
  	console.log(this.props, this.data, '-------')
  	axios.get('https://jsonplaceholder.typicode.com/comments?postId='+this.data.id)
      .then((response)=>{
      	console.log(response)
      	this.com = response.data})
  }
	}
</script>
