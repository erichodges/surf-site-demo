<template>
  <v-app light>
    <v-navigation-drawer dark class="drawer"
      :mini-variant.sync="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      temporary
      disable-resize-watcher
      fixed
      app
      width=200
    >
     
      <v-list>
        <v-icon class="burger-drawer" @click="drawer = !drawer">close</v-icon>
        <!-- <v-toolbar-side-icon class="burger-drawer" @click="drawer = !drawer"></v-toolbar-side-icon> -->

        <ul class="sidenav-ul">
          
          <li v-scroll-to="'#section-2'" class="sidenav-link-style">Products</li>  
          <li v-scroll-to="'#section-3'" class="sidenav-link-style">About</li>
          <li v-scroll-to="'#section-4'" class="sidenav-link-style">Contact</li>
        </ul>
        <!-- <v-list-tile>
          <v-list-tile-content>
            <v-list-tile-title class="sidenav-link-style" v-scroll-to="'#section-2'" display-2>
              Section 2
            </v-list-tile-title>            
            <v-list-tile-title class="sidenav-link-style" v-scroll-to="'#section-3'" display-2>
              Section 3
            </v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile> -->

      </v-list>            
    </v-navigation-drawer>

<!-- Navigation Toolbar -->
  
    <v-toolbar  app scrollOffScreen :scrollThreshold="150" dense flat color="transparent">
        <v-toolbar-side-icon class="burger" hidden-md @click="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title>
          <v-btn to="/" v-scroll-to="'#section-1'" color="transparent" flat>
          <h1 class="black--text">Rad Boards</h1></v-btn>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="toolbar-items">
          <v-btn v-scroll-to="'#section-2'" flat color="black"><h2>Products</h2>
          </v-btn>          
          <v-btn v-scroll-to="'#section-3'" flat color="black"><h2>About</h2></v-btn>
          <v-btn v-scroll-to="'#section-4'" flat color="black"><h2>Contact</h2></v-btn>
          <div class="toolbar-spacer"></div>
        </v-toolbar-items>
    </v-toolbar>  
<!-- End Navigation Toolbar -->
    <div class="div-with-background">
      <v-btn v-scroll="handleScroll" v-scroll-to="'#section-1'" class="pageup-btn"
        color="primary"
        dark                   
        fixed
        bottom
        right
        nuxt
        fab
        transition
      >
        <v-icon>keyboard_arrow_up</v-icon>
      </v-btn>
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
    data: () => ({
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        { icon: 'apps', title: 'Welcome', to: '/' },
        { icon: 'bubble_chart', title: 'Inspire', to: '/' }
      ],
      miniVariant: false,
      right: false,
      rightDrawer: false,
      title: 'Nuxt/Vuetify'
    }),
    methods: {
      handleScroll (evt, el) {
        if (window.scrollY > 50) {
          el.setAttribute('style', 'opacity: 1; transform: translate3d(0, -10px, 0')
        } else if (window.scrollY < 50) {
          el.setAttribute('style', 'opacity: 0; transform: translate3d(0, 10px, 0')
        }
      }
    }
  }
</script>



<style>

/* disable-resize-watcher  - this keeps the app from adding the navigation-drawer on wider screens  */
.black--text {
  font-size: 3rem;
}

.v-toolbar__title:not(:first-child) {
      margin-left: 0 !important;
    }

@media only screen and (max-width: 56.25em) {
  .toolbar-items {    
    visibility: hidden !important;
    width: 0 !important;
  }
}

@media only screen and (min-width: 56.25em) {
  .burger {
    left: -1rem;
    visibility: hidden !important;
    width: 0 !important;   
  }
  .v-toolbar__content, .v-toolbar__extension {
  padding: 0 !important;
}

  }

.toolbar-spacer {
  margin-right: 2rem;
}


.burger-drawer {
  /* position: absolute; */
  margin-top: 5px;
  margin-left: 1.2rem;
}

/* Side Nav  */
.sidenav-ul {
  padding-left: 2.7rem;
}
.sidenav-link-style {
  cursor: pointer;
  font-size: 2rem;
  list-style: none;
  margin: 10px;
  text-decoration: none;
  
}
/* End Side Nav */

.pageup-btn {
  bottom: +2rem;
  opacity: 0;
}

.div-with-background {
  height: 100vh; 
  background-image: url('~/static/images/pexels-photo-416676.jpeg');      
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
}

/* this removes all caps from the buttons */
  #app .v-btn {
    text-transform: none;
    font-size: 1.5rem;
  }

</style>
