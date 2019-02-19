<template>
	<div>
    <div class="container card" v-if="com && com.length" >

    	<div class="card-body text-center"><b>{{data.title}}</b><br>post</div>
    	<div class="card-body">
    		 {{data.body}}
    		 <hr>
    	</div>
    	<div class="card-body" v-for="comm in com">

    		 {{comm.body}}

    		 <!-- {{this.data.id}} -->
    	</div>
        <app-auth :data="data"></app-auth>

     </div>
    </div>
	</div>
</template>

<script >
import axios from 'axios'
import Author2 from '@/components/Author'
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
  },
  components: {
  	'app-auth': Author2
  }
	}
</script>
