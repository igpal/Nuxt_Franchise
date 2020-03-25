<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <v-list-item-group v-model="item" color="purple darken-2">
              <v-list-item 
                  v-for="item in items"
                  :key="item.text"
                  :selectable = true
                  @click="toLink(item.link)"
                >

                  <v-list-item-action>
                    <v-icon>{{ item.icon }}</v-icon>
                  </v-list-item-action>
                  <v-list-item-content>
                    <v-list-item-title>
                      {{ item.text }}
                    </v-list-item-title>
                  </v-list-item-content>
            </v-list-item>
        </v-list-item-group> 
      </v-list>
    </v-navigation-drawer>

    <v-app-bar  
      app
      clipped-left
      dense
    >
    
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-spacer />
        <v-row
          align="center"
          style="max-width: 650px"
        >  
      </v-row>
    
    <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon @click="toBoard">
        <v-icon>dashboard</v-icon>
      </v-btn>

      <v-btn icon @click="toProfile">
        <v-icon>mdi-account</v-icon>
      </v-btn>

    </v-app-bar>

    <v-content>
      <v-container>
        <v-row>
          <v-col>

          <div class="my-3">
            <nuxt />
          </div>  
          

          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      item: 0,
      drawer: null,
      items: [
        { icon: 'dashboard', text: 'Dashboard',link:'/dashboard' },
        { icon: 'mdi-account', text: 'User Profile',link:'/userprofile' },
        { icon: 'mdi-clipboard-outline', text: 'Regular Tables',link:'/regulartables' },
        { icon: 'mdi-format-font', text: 'Typograpthy',link:'/typograpthy' },
        { icon: 'mdi-chart-bubble', text: 'Icons',link:'/icons' },
        { icon: 'mdi-map-marker', text: 'Google Maps',link:'/GoogleMaps' },
        { icon: 'mdi-bell', text: 'Notifications',link:'/notifications' },
      ]
    }),
    methods:{
      toLink(link){
        this.$router.push(`/md${link}`);
      },
      toBoard(){
        this.$router.push(`/md/dashboard`);
      },
      toProfile(){
        this.$router.push(`/md/userprofile`);
      }
    }
  }
</script>