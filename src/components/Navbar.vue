<template>
  <nav>
    <v-snackbar v-model="snackbar" color="success" top>
      <span>Nice!! You just added a new task</span>
      <v-btn depressed small color="success" class="red--text text-darken-5" @click="snackbar = !snackbar">X</v-btn>
    </v-snackbar>
    <!-- nav-bar -->
    <v-app-bar app>
      <v-app-bar-nav-icon @click="sideBar = !sideBar">
      </v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase mx-3">
        <span class="grey--text text-lighten-2">Task</span>
        <span>Tracker</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <!-- dropdown -->
      <!-- <div class="text-center">
        <v-menu offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-btn class="mx-4" elevation="0.5" rounded small
              v-bind="attrs"
              v-on="on"
             >
              <v-icon
                class="left"
                light
              >
                mdi-arrow-down
              </v-icon>
              <span>Menu</span>
            </v-btn>
          </template>
          <v-list>
            <router-link :to='link.route' v-for="(link, i) in links" :key="i">
              <v-list-item
              >
                <v-list-item-title>{{ link.text }}</v-list-item-title>
              </v-list-item>
              <v-divider></v-divider>
            </router-link>
          </v-list>
        </v-menu>
      </div> -->

      <v-btn depressed class="info lighten-3 black--text">Sign out</v-btn>
    </v-app-bar>

    <!-- sidebar -->
    <v-navigation-drawer app class="info lighten-2" v-model="sideBar">
      <v-list
      >
        <!-- User avatar -->
        <v-row>
          <v-col class="my-4 text-center">
            <v-avatar size="100">
              <v-img style="height:100px;" src="https://images.pexels.com/photos/1222271/pexels-photo-1222271.jpeg?auto=compress&cs=tinysrgb&w=400" height="200px" />
            </v-avatar>
            <h3 class="caption">Chinex</h3>

           <div class="my-4">
            <popup @projectAdded="snackbar = true"/>
           </div>
          </v-col>
        </v-row>
        <!-- nav-links -->
        <router-link :to="link.route"
            v-for=" (link, i) in links "
            :key="i">
          <v-list-item-group
          >
          <!-- active-class="deep-purple--text text--accent-4" -->
            <v-list-item>
              <v-list-item-icon>
                <v-icon>{{link.icon}}</v-icon>
              </v-list-item-icon>
              <v-list-item-title>{{link.text}}</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </router-link>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import Popup from './popUp'
export default {
  name: 'Navbar',
  props: {
    showBar: Boolean
  },
  components: {
    Popup
  },
  // method: {
  //   showSideBar: !this.sideBar
  // },
  data () {
    return {
      sideBar: false,
      links: [
        { icon: 'mdi-home', text: 'Dashboard', route: '/' },
        { icon: 'mdi-folder', text: 'My projects', route: '/projects' },
        { icon: ' mdi-book', text: 'Team', route: '/team' }
      ],
      snackbar: false
    }
  }
}
</script>

<style scoped>
  a{
    text-decoration: none;
  }
</style>
