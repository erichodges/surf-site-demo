<template>
  <v-app light>
    <v-navigation-drawer
      :mini-variant.sync="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
      hidden-lg      
    >
      <v-list>
        <v-list-tile
          router
          :to="item.to"
          :key="i"
          v-for="(item, i) in items"
          exact
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>      
    </v-navigation-drawer>

    <v-toolbar app :clipped-left="clipped" dense flat color="transparent">
        <v-toolbar-side-icon hidden-md @click="drawer = !drawer"></v-toolbar-side-icon>
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

    <div class="div-with-background">
      
      <nuxt />
      <Footer />
    </div>
  </v-app>
</template>

<script>
  import Footer from '~/components/Footer'
  export default {
    components: {
      Footer
    },
    data () {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [{},
          { icon: 'apps', title: 'Welcome', to: '/' },
          { icon: 'bubble_chart', title: 'Inspire', to: '/inspire' }
        ],
        miniVariant: false,
        right: false,
        rightDrawer: false,
        title: 'Nuxt/Vuetify'
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
