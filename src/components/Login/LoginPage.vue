<template>
<div>
 <div class="card">
    <login-header/>
    <login-input :text="email" :type="emailType" :placeholder="emailPlaceholder"/>
    <login-input :text="password" :type="passwordType" :placeholder="passwordPlaceholder"/>
    <login-checkbox/>
    <login-button/>
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
