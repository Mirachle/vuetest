<template>
<div>
 <div class="card">
    <login-header/>
    <login-input :text="email" :type="emailType" :placeholder="emailPlaceholder" @changed="emailChange"/>
    <login-input :text="password" :type="passwordType" :placeholder="passwordPlaceholder" @changed="passwordChange"/>
    <login-checkbox/>
    <login-button @clicked="onClickChild"/>
  </div>
    <login-text/>
</div>
</template>

<script>
import LoginHeader from '@/components/Login/LoginHeader';
import LoginInput from '@/components/Login/LoginInput';
import LoginCheckbox from '@/components/Login/LoginCheckbox';
import LoginButton from '@/components/Login/LoginButton';
import LoginText from '@/components/Login/LoginText';
import axios from 'axios'

export default {
  name: 'LoginPage',
  data() {
    return {
      email: "Email",
      emailType: "email",
      emailPlaceholder: "marcelpatoulachi@gmail.com",
      password: "Password",
      passwordType: "password",
      passwordPlaceholder:"42plodoc|",
    };
  },

components: {
    "login-header": LoginHeader,
    "login-input": LoginInput,
    "login-checkbox": LoginCheckbox,
    "login-button": LoginButton,
    "login-text": LoginText,
    },


  methods: {
    onClickChild() {
      this.postNow();
    },

    emailChange(value) {
      this.emailValue = value;
    },

    passwordChange(value) {
      this.passwordValue = value;
    },

    postNow(){
      axios.post('https://us-central1-ria-server-b1103.cloudfunctions.net/authenticate',
      {data:{
        password: this.passwordValue,
        email: this.emailValue,
      }}).then((r) =>{

        if(r.data.result){
          alert(JSON.stringify(r.data.result))
        }else{
           alert(r.data.result.error)
        }
      });
    }

  }

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
    padding: 5%;
    margin: 15%;
    margin-bottom: 0%;
    text-align: left;
    box-shadow:0px 0px 6px #e0e0e0;
    border: 0px;
    }
</style>
