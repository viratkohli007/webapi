<template>
  <div>
    <h1>Hello</h1>
    <!-- <app-home :api="info"></app-home> -->
    <!-- <button @click="switchcomp='app-home'">Home</button> -->

<hr>
<!-- <component :is="switchcomp" :api='info' :com='comments'></component> -->
<app-home :api='info'></app-home>
  </div>
</template>

<script>
import Home from '@/components/Home'
//import Comments from '@/components/Comments'
import axios from 'axios'
export default {
components: {
  'app-home': Home
  //'app-com' : Comments
},
  data(){

    return{
      info: null,


    }
  },
     created(){
      axios.get('https://jsonplaceholder.typicode.com/posts')
      .then((response)=>(this.info = response.data))


     }
 }

</script>




