<!-- Footer Component -->

<template>
    <footer>
        <v-footer padless>
            <v-col class="text-center" cols="12">
            {{ new Date().getFullYear() }} — <strong>Login System</strong>
            </v-col>
        </v-footer>
    </footer>
</template>

<script>
export default {
    name: 'Footer'
}
</script>