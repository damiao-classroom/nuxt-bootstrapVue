<template>
  <div>
    
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">Damiao Jokes</b-navbar-brand>
      
       <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>

        <b-navbar-nav>
          <b-nav-item href="/">Home</b-nav-item>
          <b-nav-item href="/jokes">Jokes</b-nav-item>
          <b-nav-item href="/about">About</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <!-- <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search" v-model="searchValue"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" @click="searchJokes">Search</b-button>
          </b-nav-form>
        </b-navbar-nav> -->

      </b-collapse>
    </b-navbar>

  </div>
</template>

<script scoped> 
  export default{
    name: 'AppHeader',
  }
</script>

<style>
</style>
