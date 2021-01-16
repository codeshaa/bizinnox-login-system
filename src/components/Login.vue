<!-- Login Component -->

<template>

    <v-card class="mx-auto pa-4" color="light-blue accent-1" max-width="600">
        <p class="text-h5 text-center">Login</p>
        <p v-if="error" class="text-caption font-weight-medium validation-error">{{error}}</p>
        <v-form ref="form" v-model="valid" lazy-validation>
                <v-text-field v-model="email" :rules="emailRules" label="E-mail" required></v-text-field>
                <v-text-field v-model="password" :rules="[rules.required, rules.min]" type="password" label="Password" hint="At least 8 characters" required></v-text-field>


            <v-btn color="success" class="mr-4 mt-4" @click.prevent="submitForm">
                Submit
            </v-btn>

        </v-form>
    </v-card>
</template>

<script>
import bcrypt from 'bcryptjs';
import user from '../user'


export default {
    name: 'Login',
    data() {
        return {
            error: '',
            email: '',
            password: '',
            rules: {
                required: value => !!value || 'Required.',
                min: v => v.length >= 8 || 'Min 8 characters',
            },
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+/.test(v) || 'E-mail must be valid',
            ],
        }
    },
    methods: {
        submitForm(){
            if(this.$refs.form.validate()){

                if (this.email == user.email){
                    if (bcrypt.compareSync(this.password, user.passwordhashed)){
                        localStorage.setItem('user', this.email)
                        this.$store.dispatch('user', user)
                        this.$router.push('/').catch(()=>{})
                    }
                    else {
                        this.error = 'Invalid credentials'
                    }   
                }
            }
       
        }

    }
}
</script>


<style scoped>
.validation-error{
    color: red;
}
</style>