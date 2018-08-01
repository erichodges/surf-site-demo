<template>
  <v-app light>
    <div class="div-with-background">
      <v-toolbar dense flat color="transparent">
        <v-toolbar-title>
          <v-btn to="/" color="transparent" flat>
          <h2 class="black--text">Site Logo</h2></v-btn>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items>
          <v-btn to="/signin" flat color="blue"><h3>Sign In</h3></v-btn>
          <v-btn to="/signup" flat color="blue"><h3>Sign Up</h3></v-btn>
        </v-toolbar-items>
      </v-toolbar>

      
        
          <nuxt />
        
      

      <v-footer :fixed="fixed" app class="white">
        <span>&copy; 2018</span>
      </v-footer>
    </div>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: false,
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
  #app .btn {
    text-transform: none;
  }

</style>
