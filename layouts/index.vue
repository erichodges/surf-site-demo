<template>
  <v-app light>
    <div class="div-with-background">
      <Nav />
      <nuxt />
      <Footer />
    </div>
  </v-app>
</template>

<script>
  import Nav from '~/components/Nav'
  import Footer from '~/components/Footer'

  export default {
    components: {
      Nav,
      Footer
    },
    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'apps', title: 'Welcome', to: '/' },
          { icon: 'bubble_chart', title: 'Inspire', to: '/inspire' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vue with Vuetify.js'
      }
    }
  }
</script>


<style>

.div-with-background {
  height: 100vh; 
  background-image: url('~/static/images/1.jpg');      
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
}

/* this removes all caps from the buttons */
  #app .v-btn {
    text-transform: none;
  }

</style>
