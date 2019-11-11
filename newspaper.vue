<template>
   <div>
       <h3 class="text-center">VueNews</h3> 
 <b-container class="bv-example-row">
       <b-jumbotron class="jumboFilter"> 
     <b-row>
         <h3 class="titleFilter">Filter by Category</h3>
    </b-row>
<b-row>
<b-col>
          <select v-model="section" class="dropitems">
                <option v-for="section in sections" :value="section" :key="section">{{ section }}</option>
          </select>
</b-col>
   <b-col @click="getPosts()" class="btn"><b-button> Retrive</b-button> </b-col>
</b-row>
  </b-jumbotron>
    </b-container>
<h4 class="text-center">TOP STORIES TODAY(31)</h4>
<b-container class="bv-example-row">
      <div class="card"  v-for="result in processedPosts" :key="result">
  
    <div class="card-divider">
       
      {{ result.title }}
      </div>
      <div class="img">
       <img  width="170px"   :src="result.image_url">
      </div>
    <div class="card-section">
      <p>{{ result.abstract }}.</p>
    </div>
  
</div>

</b-container>
</div> 
                      
</template>

<script>

import axios from 'axios'
export default {
    
     data() {
         const SECTIONS = "home, arts, automobiles, books, business, fashion, food, health, insider, magazine, movies, national, nyregion, obituaries, opinion, politics, realestate, science, sports, sundayreview, technology, theater, tmagazine, travel, upshot, world";

         return{
             
 results: [ ],
  sections: SECTIONS.split(', '), 
    section: 'home', 
    loading: true,
    title: ''
         }
   },
  mounted(){
    this.getPosts()
     },
    methods:{
 getPosts(){
 axios.get(`https://api.nytimes.com/svc/topstories/v2/${this.section}.json?api-key= BVGhfqMjXf4uYcjd4r2KwufJkR3Y07EM`)
    .then(response => {this.results = response.data.results})
  }
  },
   computed: {
    processedPosts() {
      let posts = this.results;
      posts.map(post => {
        let imgObj = post.multimedia.find(media => media.format === "superJumbo");
        post.image_url = imgObj ? imgObj.url : "http://placehold.it/300x200?text=N/A";
      });
      let i, j, chunkedArray = [], chunk = 4;
      for (i=0, j=0; i < posts.length; i += chunk, j++) {
        chunkedArray[j] = posts.slice(i,i+chunk);
      }
      return posts;
    }
  }

}
</script>
<style  scoped>
.titleFilter{
    color:rgb(3, 36, 36);
    margin: 0 auto;
    margin-bottom: 15px;
}
.dropitems{
    width:80%;
}
.jumboFilter{
    padding:20px !important;
}
.btn{
    width:80%;
    height:30px !important;
    line-height: 30px !important;

}
 .card{
width: calc(100% - 20px) ;
padding: 10px ;
margin:  10px 0;

} 
.bv-example-row{
  text-align: center;
}
.img{
  text-align: center;
}
</style>
