<template>
  <section>

    <!-- Banner -->
    <Banner title="Jokes Page" para="this is a jokes search page." img="/images/banner_jokes.jpg"></Banner>

    <!-- search box -->
    <div class="search-box">
        <b-input-group prepend="Search" class="mt-3">
            <b-form-input placeholder="please enter joke's name" v-model="searchWord"></b-form-input>
          </b-input-group>
          <b-input-group prepend="Limit" class="mt-3">
            <b-form-input placeholder="please enter limit number and max <= 30" v-model="perPage"></b-form-input>
          </b-input-group>
          <b-button block variant="info" class="mt-3" @click="getJokesData">Click search jokes</b-button>
    </div>

    <!-- loading -->
    <div class="loading-box" v-if="loading">
        <h3>loading…</h3>
    </div>

    <!-- jokes list -->
    <div class="jokes-list-box" v-if="!loading">
        <b-list-group>
          <b-list-group-item v-for="it,index in jokes" :key="index">{{it}}</b-list-group-item>
        </b-list-group>
    </div>
    
    <!-- pagination -->
    <div class="pagination-box">
        <b-pagination
          v-model="page"
          :total-rows="rows"
          :per-page="perPage"
          first-text="First"
          prev-text="<"
          next-text=">"
          last-text="Last"
          align="center"
          variant="info"
          @click.native="getJokesData"
        ></b-pagination>
    </div>

  </section>
</template>

<script>

import Banner from '@/components/Banner'
import axios from 'axios'

export default {
  data(){
    return {
        loading: true,
        jokes: [],
        page: 1,
        rows: 100,
        perPage: 10,
        searchWord: 'list all jokes'
    }
  },
  created(){
    this.getJokesData()
  },
  methods: {
    async getJokesData(){
        const config = {
            headers: {
                'Accept': 'application/json'
            },
            params:{
                page: this.page,
                limit: this.perPage,
                term: this.searchWord
            }
        };

        this.loading = true;
        const res = await axios.get('https://icanhazdadjoke.com/search', config)
        this.loading = false;
        console.log(res.data)
        this.jokes  = res.data.results.map(v => v.joke)
        this.rows = res.data.total_jokes
    }
  }, 
  head(){
    return {
      title: 'jokes page',
      meta: [{
        hid: "description",
        name: "description",
        content: "funny jokes page"
      }]
    }
  },
  components: {
    Banner
  }
}
</script>

<style>
    .pagination-box{ margin-top: 30px; margin-bottom: 30px; }
    .loading-box h3{ text-align: center; line-height: 150px; height: 150px;}
    .search-box{  width:96%; height: auto;  margin: 0 auto; padding-bottom: 20px; }
</style>
