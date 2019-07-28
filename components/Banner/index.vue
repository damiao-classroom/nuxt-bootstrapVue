<template>
  <div>
    <b-card
        overlay
        :img-src="img"
        img-alt="Jokes Image"
        text-variant="white"
        :title="title"
        class="jokes-banner"
      >
      <b-card-text>
        {{ para }}
      </b-card-text>
    </b-card>
  </div>
</template>

<script scoped> 
  export default{
    props: {
      img:{
        type: String,
        default: '/images/banner_jokes.jpg'
      },
      title: {
        type: String,
        default: 'Damiao Page'
      },
      para: {
        type: String,
        default: 'This is a damiao website page.'
      }
    },
    name: 'Banner'
  }
</script>

<style scoped>
  .jokes-banner{ border:none; border-radius: 0; }
</style>
