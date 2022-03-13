<template>
  <div class="container">
   <v-app id="login">
      <v-main>
         <v-container fluid fill-height>
            <v-layout align-center justify-center>
               <v-flex xs12 sm8 md4>
                 
                  <v-card class="elevation-12">
                     <v-card-text>
                        <v-form ref="form" v-model="valid" lazy-validation>
                           <v-text-field
                              prepend-inner-icon="mdi-account"
                              v-model="email"
                              :rules="emailRules"
                              label="E-mail"
                              required
                            ></v-text-field>
                           <v-text-field
                              id="password"
                              v-model="password"
                              :rules="passwordRules"
                              prepend-inner-icon="mdi-lock"
                              name="password"
                              label="Password"
                              type="password"
                              
                           ></v-text-field>
                            
                        </v-form>
                      
                     </v-card-text>
                    
                         <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn
                              :disabled="!valid"
                              color="success"
                              class="mr-4"
                              @click="validate"
                              to="/Map"
                            >
                              로그인
                            </v-btn>

                            <v-btn
                              color="error"
                              class="mr-4"
                              @click="reset"
                            >
                              초기화
                            </v-btn>
                        </v-card-actions>
                  </v-card>
               </v-flex>
            </v-layout>
         </v-container>
      </v-main>
   </v-app>
   </div>
</template>

<script>
export default {
  name: 'Login',
  methods:{
    validate () {
        this.$refs.form.validate()
        console.log(this.email,this.password);
      },
      reset () {
        this.$refs.form.reset()
      },
  
  },
  computed:{
  
  },
  data(){
    return{
      valid: true,
      email: '',
      emailRules: [
        v => !!v || '이메일을 입력해주세요!',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      password: '',
      passwordRules: [
        v => !!v || '패스워드를 입력해주세요!'
      ],

    }
  },
   props: { }
}
</script>

