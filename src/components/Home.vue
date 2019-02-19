<template>
	<div>
		<div class="container card" v-if="api && api.length" v-for="info in api">
			<div v-if="seen">
			<div class="card-body" @click="expand(info)"><b>{{info.title}}</b></div>
			<div class="card-body">{{info.body}}</div>
			<div>
			 {{info.id}}
			</div>
      </div>

		</div>
		<app-com  :data="data" v-if="!seen"></app-com>
		<!-- <component :is="switchcomp" :api="api" v-if="!seen" :id="this.id"></component> -->
	</div>
</template>

<script>
import axios from 'axios'
import Comments from '@/components/Comments'
import Home from '@/components/Home'

export default{
	props: ['api'],
	data(){
		 return{
      switchcomp: 'app-home',
      seen: true,
      data:[]
    }
	},
	components:  {
     'app-com': Comments,
     'app-home': Home
	},
	methods:{
		expand(info){
			 	// this.switchcomp = 'app-com'
			 			 this.seen =! this.seen
			 			 this.data = info
			 			 console.log(this.data)
		}
	}

}
</script>
