<template>
  <v-app>
    <v-app-bar app class="d-flex justify-end">
    <div class="mx-2">
          <v-btn 
            color="blue-grey lighten-4"
            rounded
            @click="loginToAdmin"
            >
            Войти
        </v-btn>
    </div>
    
    <div class="mx-2"> 
      <v-btn 
          color="pink darken-3"
          rounded
          @click="goToMD"
          >
          Material Design
      </v-btn> 
    </div>    
</v-app-bar>

    <v-content>
      <nuxt />
    </v-content>

    <v-footer>
      
    </v-footer>

  </v-app>
</template>

<script>
export default {
  data () {
    return {
      
    }
  },
  methods: {
    loginToAdmin(){
        this.$router.push(`/admin/login`)
    },
    goToMD(){
        this.$router.push(`/md/dashboard`)  
    }
    
}
}
</script>
