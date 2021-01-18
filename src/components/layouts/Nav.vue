<!-- Navbar Component -->

<template>
    <nav>
        <v-app-bar app color="light-blue darken-3">
            <v-toolbar-title class="white--text">Login System</v-toolbar-title>
            <v-spacer></v-spacer>
            <router-link v-if="!user" to="/login"><v-btn text class="white--text">Login</v-btn></router-link>
            <router-link v-if="user" to="/"><v-btn text class="white--text">Home</v-btn></router-link>
            <a href="javascript:void(0)" v-if="user" @click="logout"><v-btn text class="white--text">Logout</v-btn></a>
        </v-app-bar>
    </nav>
</template>


<script>

import {mapGetters} from 'vuex'

export default {
    name: 'Nav',
    methods: {
        logout() {
            localStorage.removeItem('user')
            this.$router.push('/login').catch(()=>{})
        }
    },
    computed: {
        ...mapGetters(['user'])
    }
}
</script>