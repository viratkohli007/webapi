<template>
	<div>
		 <h1>user</h1>
		 <div v-if="uinfo && uinfo.length">
      <p>@{{uinfo[0].username}}</p>
      <p>{{uinfo[0].name}}</p>
      <p>{{uinfo[0].email}}</p>
      <p>{{uinfo[0].address.street}},{{uinfo[0].address.suite}},{{uinfo[0].address.city}},{{uinfo[0].address.zipcode}}</p>
      <p>{{uinfo[0].phone}}</p>
      <p>{{uinfo[0].website}}</p>
      <p>{{uinfo[0].company.name}}</p>
      </div>
	</div>

</template>

<script>
import axios from 'axios'

export default{
	props: ['id'],
	data(){
		return{
			uinfo:null
		}
	},

   mounted(){
   	axios.get('https://jsonplaceholder.typicode.com/users?id='+this.id)
      .then((response)=>this.uinfo=response.data)
    }
}
</script>
