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
import Swal from 'sweetalert2'

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
        let timerInterval
        if(r.data.result){
          if(r.data.result["id"] == undefined){
            Swal.fire({
              title: 'Oops...',
              text: 'Something went wrong! Try again!',
              type: 'error',
              heightAuto: false,
              showConfirmButton: false,
              timer: 3000,
              onClose: () => {
                clearInterval(timerInterval)
              }
            })
          }
          else{
            Swal.fire({
              title: 'Your data:',
              html: "Id: " + JSON.stringify(r.data.result["id"]) +
                  ("<br/>Email: " + JSON.stringify(r.data.result["email"])  +
                    "<br/>Name: " + JSON.stringify(r.data.result["name"]) +
                    "<br/>Address: " + JSON.stringify(r.data.result["address"])).replace(/"/g, ''),
              type: 'success',
              heightAuto: false,
              confirmButtonText: "Tovább",
            }).then((result) => {
              if (result.value) {
                //this.router.navigate('profile/');
                alert('yes!');
              }
            })
          }
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
