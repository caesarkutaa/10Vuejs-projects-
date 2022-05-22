<template>
  <section> 
    <div class="flex">
      <div class="m-auto bg-white p-2 rounded shadow">
        <div class="p-2 border">
          <h1 class="text-3xl font-bold text-center">Vue Login</h1>
          <form class="p-2 my-2" @submit.prevent="submit"> 
            <div class="my-4">
              <label> FirstName:</label><br>
              <input  v-model="form.firstName" class="rounded shadow p-2" @keyup="validateFirstName"/><br>
              <p class="text-sm text-red-600 pl-1" v-if="getFirstNameErrMssg.length">{{getFirstNameErrMssg}}</p>
            <p class="text-sm text-green-600 pl-1" v-else-if="getFirstNameSuccMssg.length">{{getFirstNameSuccMssg}}</p>
              <label >LastName:</label><br>
              <input v-model="form.lastName" class="rounded shadow p-2" @keyup="validateLastName"/><br>
               <p class="text-sm text-red-600 pl-1" v-if="getLastNameErrMssg.length">{{getLastNameErrMssg}}</p>
            <p class="text-sm text-green-600 pl-1" v-else-if="getLastNameSuccMssg.length">{{getLastNameSuccMssg}}</p>
              <label>Email:</label><br>
              <input v-model="form.email" class="rounded shadow p-2"/><br>
            </div>
            <div class="my-4">
              <label>Password</label><br>
              <input v-model="form.password" class="rounded shadow p-2" type="password" @keyup="validatePassword"/><br>
              <p class="text-sm text-red-600 pl-1" v-if="getPasswordErrMssg.length">{{getPasswordErrMssg}}</p>
            <p class="text-sm text-green-600 pl-1" v-else-if="getPasswordSuccMssg.length">{{getPasswordSuccMssg}}</p>
              <label>Confirm Password</label><br>
              <input v-model="form.confirmpassword"   class="rounded shadow p-2 w-full" type="password" @keyup="validateConfirmPassword"/><br>
              <p class="text-sm text-red-600 pl-1" v-if="getConfirmPasswordErrMssg.length">{{getConfirmPasswordErrMssg}}</p>
            <p class="text-sm text-green-600 pl-1" v-else-if="getConfirmPasswordSuccMssg.length">{{getConfirmPasswordSuccMssg}}</p>
            </div>
      
            <div class="my-4">
              <button type="submit" class="w-full rounded shadow-md bg-graient from-orange-800 to bg-red-500 text-white p-2">Login</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>



<script>
import { getGlobalThis } from '@vue/shared';

export default { 
  data(){
    return{
     form: {
        firstName:"",
        lastName:"",
        email:"",
        password:"",
        confirmPassword:"",
      
       },
     firstNameMssg:
      {
        error: "", success: ""
      },
       lastNameMssg: 
      {
        error: "", success: ""
      },
      emailMssg: 
      {
        error: "", success: ""
      },
      passwordMssg:
      {
        error: "", success: ""
      },
      confirmPasswordMssg:
      {
        error: "", success: ""
      },
    };
  },
   
  methods:{
     submit(){
      //  submit the form
    },
    validateFirstName(){
      this.firstNameMssg.error = "";
      this.firstNameMssg.success = "";
      if((this.form.firstName).length <= 3){ 
        return this.firstNameMssg.error="Firstname should me more than 3"

      }
      else{
       return this.firstNameMssg.success="First name validated"
      } 
    },

     validateLastName(){
      this.lastNameMssg.error = "";
      this.lastNameMssg.success = "";
      if((this.form.lastName).length <= 3){ 
        return this.lastNameMssg.error="Lastname should me more than 3"

      }
      else{
       return this.lastNameMssg.success="Last name validated"
      } 
    },
     
    validatePassword() {
          this.passwordMssg.error = "";
          this.passwordMssg.success = "";
          let passwordValid = new RegExp('((?=.*[a-z])(?=.*[0-9])(?=.*[^A-Za-z0-9])(?=.{7,}))');
          this.validateConfirmPassword();
          if(passwordValid.test(this.form.password)) {
            return this.passwordMssg.success = "Password validated"
          }
          else{
          return this.passwordMssg.error = "Password must be more than 6 words length and must contain at least 1 alphabet, number and symbol"
          }
        },
    
    validateConfirmPassword(){
      this.confirmPasswordMssg.error="";
      this.confirmPasswordMssg.success="";
      if(this.form.password === this.form.confirmPassword){
        return this.confirmPasswordMssg.success ="passwords match"
      }
     else{
       return this.confirmPasswordMssg.error = "passwords not matching"
     }


     
    }

    
    
  },



  computed: {
    
    getFirstNameSuccMssg() {
      return this.firstNameMssg.success
    },
    getFirstNameErrMssg() {
      return this.firstNameMssg.error
    },
    getLastNameSuccMssg() {
      return this.lastNameMssg.success
    },
    getLastNameErrMssg() {
      return this.lastNameMssg.error
    },
    getEmailSuccMssg() {
      return this.emailMssg.success
    },
    getEmailErrMssg() {
      return this.emailMssg.error
    },
    getPasswordSuccMssg() {
      return this.passwordMssg.success
    },
    getPasswordErrMssg() {
      return this.passwordMssg.error
    },
    getConfirmPasswordSuccMssg() {
      return this.confirmPasswordMssg.success
    },
    getConfirmPasswordErrMssg() {
      return this.confirmPasswordMssg.error
    },
  },

}
  
   


</script>

<style>

</style>