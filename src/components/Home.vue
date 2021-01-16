<!-- Home Component -->

<template>
    <section>
        
        <v-card class="mx-auto" max-width="600" color="light-blue accent-1">
          <v-list-item three-line>
            <v-list-item-content>
              <div class="overline mb-4">
                HOME PAGE
              </div>
              <v-list-item-title class="headline mb-1">
                Welcome, {{user.firstname + ' ' + user.lastname}}
              </v-list-item-title>
              <v-list-item-subtitle>Welcome to Home page.</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-card>
    </section>
</template>

<script>

import {mapGetters} from 'vuex'

export default {
    name: 'Home',
    computed: {
        ...mapGetters(['user'])
    }
    
}
</script>