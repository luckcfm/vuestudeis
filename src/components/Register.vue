 <template>
     <v-layout>
         <v-flex xs12 sm6 offset-sm3>
             <v-form v-model="valid" ref="form" lazy-validation>
                 <v-text-field
                         label="Full Name"
                         v-model="register.fullName"

                         :counter="50"
                         required></v-text-field>

                 <v-text-field
                         label="Image"
                         v-model="register.senha"

                         :counter="10"
                         required></v-text-field>

                 <v-text-field
                         label="Email"
                         v-model="register.email"

                         :counter="50"
                         required></v-text-field>

                 <v-text-field
                         label="Password"
                         v-model="register.password"
                         :rules="passwordRules"
                         :counter="50"
                         required></v-text-field>
                 <v-text-field
                         label="Confirm password"
                         v-model="register.passwordConfirmation"
                         :rules="confirmRules"
                         :counter="50"
                         required></v-text-field>

                 <v-btn @click="submit('save')">
                        <!--:disabled="!valid">-->
                     Save
                </v-btn>
                 <v-btn @click="submit('cancel')">
                     <!--:disabled="!valid">-->
                     Cancel
                 </v-btn>
                 <v-btn @click="submit">
                     <!--:disabled="!valid">-->
                     Clear Form
                 </v-btn>
             </v-form>
         </v-flex>
     </v-layout>
 </template>
 <script>
     export default {
         methods: {
            submit(operation){
                switch(operation){
                    case "cancel":
                        this.$emit('unregister');
                        break;
                    case "save":
                        axios.post("http://novus-api.azurewebsites.net/api/v1/account",this.$data)
                        .then(function(data){
                            console.log(data)
                    })
                        .catch(function(error){
                            console.log(error);
                        })
                        break;

                }

            }

         },
         data(){
             return { register: {
                 fullName: '',
                 base64Image: '',
                 email: '',
                 password: '',
                 passwordConfirmation: '',
             },
                 valid: true,
                 confirmRules: [
                     (v) => !!v || 'Name is required',
                     (v) => v && v.length >= 6 || 'Name must be less than 10',
                     (v) => v === this.register.password || 'Password must be equals'
                 ],
                 passwordRules: [
                     (v) => !!v || 'Name is required',
                     (v) => v && v.length >= 6 || 'Password must be greater than 6 digits',

                 ],
             }
         }
     }


 </script>