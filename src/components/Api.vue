<template >

  <div  id="up" class="search text-light">
    <h2 >Nasa Image Search</h2>
    <form class="w-50 m-auto input-group mb-3" v-on:submit.prevent="getResult(query)">
      <input class="form-control" type="text" placeholder="Type in your search" v-model="query" aria-label="Recipient's username" aria-describedby="button-addon2" />
    
    </form>
    <div class="container-fluid">
    <div  v-if="results" class="row m-auto ">
      <div class="col-md-3  " v-for="result in results" v-bind:key="result">
          <img class="w-100 mb-3  p-2 border border-white  " style="height:200px"  v-bind:src="result.links[0].href" />  
      </div>
    </div>
     
  </div>
</div>


</template>

<style >
*{
    background-color: rgb(68, 67, 67);
}
</style>


<script>
import axios from 'axios';
export default {
  name: 'Api',
  data () {
    return {
      msg: 'Api',
      query: '',
      results: ''
    }
  },
  methods: {
      getResult(query) {
        axios.get('https://images-api.nasa.gov/search?q=' + query + '&media_type=image').then( res => {
            // console.log(res.data.collection.items);
            this.results = res.data.collection.items;
        });
      }
  }
}
</script>