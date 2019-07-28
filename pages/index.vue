<template>
  
  <div class="content-page">
    
    <!-- slider -->
    <b-carousel
      id="carousel-1"
      :interval="4000"
      img-width="1024"
      img-height="480"
      fade
      indicators
      background="#ababab"
      style="text-shadow: 1px 1px 2px #333;"
    >
      <!-- Text slides with image -->
      <b-carousel-slide
        :caption="it.caption"
        :text="it.text"
        :img-src="it.img"
        v-for="it,index in sliders"
        :key="index"
      ></b-carousel-slide>
      
    </b-carousel>
    
    <!-- title -->
    <h1 align="center" class="index-title">Damiao Jokes <span class="badge badge-secondary">New</span></h1>
    
    <!-- card info -->
    <div class="card-info">

      <b-card-group deck v-if="jokes.length > 0">
        <b-card v-for="it,index in jokes" :key="index">
          <b-card-text>{{ it }}</b-card-text>
        </b-card>
      </b-card-group>

      <b-spinner label="Spinning" class="spinner-box" variant="info" v-else></b-spinner>

    </div>


  </div>
</template>

<script>

import axios from 'axios'

export default {
  data(){
    return {
      jokes: [ ],
      sliders: [ 
        { img: 'images/slider_01.jpg',  caption: 'Damiao Jokes', text: 'icanhazdadjoke.com is the largest selection of dad jokes on the internet.' },
        { img: 'images/slider_02.jpg',  caption: 'Damiao Jokes', text: 'icanhazdadjoke.com is the largest selection of dad jokes on the internet.' },
        { img: 'images/slider_03.jpg',  caption: 'Damiao Jokes', text: 'icanhazdadjoke.com is the largest selection of dad jokes on the internet.' } 
      ]
    }
  },
  head(){
    return {
      title: 'jokes home page',
      meta: [{
        hid: "description",
        name: "description",
        content: "this is funny jokes home page"
      },{
        hid: 'viewport',
        name: 'viewport',
        content: 'width=device-width, initial-scale=1.0'
      }]
    }
  },
  async created(){
    const config = {
      headers: {
        Accept: 'application/json'
      }
    };

    const res = await axios.get('https://icanhazdadjoke.com/search?limit=10', config)
    this.jokes = res.data.results.map(v => v.joke)
  },
  components: { },

}
</script>

<style scoped>
.content-page {
  margin: 0;
  width:100%;
}
.index-title{
  height: 80px; line-height: 80px;
}
.card-info{
  width: 92%; margin: 0 auto; margin-bottom: 30px;
}
.spinner-box{
 display: block; margin: 0 auto; margin-top: 50px;
}
</style>
