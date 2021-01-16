<template>
  <v-app>
    
    <Nav />

    <v-main>
      <v-container fill-height fluid>
        <v-flex>
          <router-view />
        </v-flex>
      </v-container>
    </v-main>

    <Footer />
  </v-app>
</template>



<script>

import Nav from './components/layouts/Nav'
import Footer from './components/layouts/Footer'
import user from './user'

export default {
  name: 'App',
  components: {
    Nav,
    Footer
  },
  created() {
      const userStored = localStorage.getItem('user')
      if(userStored == user.email){
          this.$store.dispatch('user', user)
      }
      else{
          this.$router.push('/login').catch(()=>{})
      }
  }
}

</script>
