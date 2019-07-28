<template>
  <section>

    
    <!-- Banner -->
    <Banner title="About Page" para="this is a jokes about page." img="/images/banner_about.jpg"></Banner>

    <h1 align="center" class="about-title">About Jokes <span class="badge badge-secondary">API</span></h1>

    
    <div class="mt-3 about-content">
      <b-card-group deck>
        
        <b-card border-variant="info" text-variant="#333" header="Jokes api website" class="text-center">
          <b-card-text>URL <em>https://icanhazdadjoke.com/api</em> get all jokes api.</b-card-text>
        </b-card>

        <b-card border-variant="info" text-variant="#333" header="Fetch a random joke" class="text-center">
          <b-card-text>GET <em>https://icanhazdadjoke.com/</em> fetch a random dad joke.</b-card-text>
        </b-card>

        <b-card border-variant="info" text-variant="#333" header="Fetch a  joke" class="text-center">
          <b-card-text>GET <em>https://icanhazdadjoke.com/j/joke_id</em> fetch a specific dad joke.</b-card-text>
        </b-card>

        <b-card border-variant="info" text-variant="#333" header="Search for jokes" class="text-center">
          <b-card-text>GET <em>https://icanhazdadjoke.com/search</em> - search for dad jokes.</b-card-text>
        </b-card>
      </b-card-group>
    </div>

  </section>
</template>

<script>
  
import Banner from '@/components/Banner'
export default {
  head(){
    return {
      title: 'about page',
      meta: [{
        hid: "page description",
        name: "description",
        content: "funny jokes about page"
      }]
    }
  },
  components: {
    Banner
  }
}
</script>

<style>
  .about-title{ height: 100px; line-height: 100px; }
  .about-content{ width: 92%; margin: 0 auto; margin-bottom: 20px; }
</style>
