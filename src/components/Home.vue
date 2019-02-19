<template>
	<div >

		<div class=" card" v-if="api && api.length" v-for="info in api">
			<div v-if="seen">
			<div class="card-body btn btn-link" @click="expand(info)"><b>{{info.title}}</b></div>
			<div class="card-body">{{info.body}}</div>
      <app-author :id="info.id"></app-author>
			<div>
			 {{info.id}}
			</div>
      </div>
     </div>
		<app-com  :data="data" v-if="!seen && seen3" @click.native="a()"></app-com>
    <app-user v-if="seen2" :id="data.id"></app-user>
	</div>
</template>

<script>
import axios from 'axios'
import Comments from '@/components/Comments'
import Home from '@/components/Home'
import Author from '@/components/Author'
import User from '@/components/User'

export default{
	props: ['api'],
	data(){
		 return{
      seen: true,
      seen2: false,
      seen3: true,
      data:[]
    }
	},
	components:  {
     'app-com': Comments,
     'app-home': Home,
     'app-author': Author,
     'app-user': User

	},
	methods:{
		expand(info){
			 	// this.switchcomp = 'app-com'
			 			 this.seen =! this.seen
			 			 this.data = info
			 			 console.log(this.data)
		},
		a(){
			this.seen2 =!this.seen2
			this.seen3 =!this.seen3
		}
	}

}
</script scoped>
<style>
	b{
		color: blue
	}
	#side{
		margin-left: 900px
	}

</style>


