<template>

    <v-layout>
        <v-flex xs12 sm6 offset-sm3>
            <v-form v-model="valid" ref="form" lazy-validation>
                <v-text-field
                    label="Login"
                    v-model="login"
                    :rules="loginRules"
                    :counter="10"
                    required></v-text-field>

                <v-text-field
                        label="Senha"
                        v-model="senha"
                        :rules="senhaRules"
                        :counter="10"
                        required></v-text-field>

                <v-btn @click="submit"
                :disabled="!valid">
                    Entrar
                </v-btn>
                <v-btn @click="register">
                    Register
                </v-btn>
            </v-form>
        </v-flex>
    </v-layout>

</template>
<script>

    export default {
        components: {

        },
        data: () => ({
            valid: false,
            login: '',
            loginRules: [
                (v) => !!v || 'Name is required',
                (v) => v && v.length <= 10 || 'Name must be less than 10'
            ],
            senha: '',
            senhaRules: [
                (v) => !!v || 'Password is required'
            ]

        }),
        methods: {
            submit() {
                alert('Submiting');
            },
            register(){
               this.$emit('registered');
            }
        }
    }
</script>
<style>

</style>