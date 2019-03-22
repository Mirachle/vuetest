<template>
  <div>
    <p :class="labelClass">
      {{text}}</p>
    <div class="input-eye">
      <input @keyup="$emit('changed', password)" v-model="password" @blur="blured" @focus="inputClicked" :type="type" :placeholder="placeholder" :class="[inputClass, isEmailValid, 'input']">
      <img @click="eyeClicked()" v-if="type == 'password' || type == 'text'" :src="eyeImage.img" alt="eye">
      <div class="strength-meter" v-if="type == 'password' || type == 'text'">
        <span :class="[strength > 3 ? 'strength-4' : '']"></span>
        <span :class="[strength > 2 ? 'strength-3' : '']"></span>
        <span :class="[strength > 1 ? 'strength-2' : '']"></span>
        <span class="strength-1"></span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "LoginInput",
  props: ["text", "type", "placeholder"],

  data() {
    return {
      labelClass: "passive-color",
      inputClass: "passive-input",
      eyeImage: { img: require("@/assets/fa-eye-slash.png") },
      eyeSlashImage: { img: require("@/assets/fa-eye-slash.png") },
      eyeFaImage: { img: require("@/assets/fa-eye.png") },
      password: "",
      email: "",
      reg: /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,24}))$/    };
  },

  computed: {
    strength() {
      if (this.password.length > 8 && ( (this.password.match(/[A-Z]+/)) && (this.password.match(/[0-9]+/)) ) ) {
        return 4;
      } else if ( (this.password.length > 5) && ( (this.password.match(/[A-Z]+/)) || (this.password.match(/[0-9]+/)) ) ) {
        return 3;
      } else if (this.password.length > 3) {
        return 2;
      }
      return 1;
    },

    isEmailValid(){
      if(this.type == "email"){
        this.email = this.password;
        (this.email == "")? "" : (this.reg.test(this.email)) ? (this.labelClass = "success-color") : (this.labelClass = "warning-color");
        (this.email == "")? "" : (this.reg.test(this.email)) ? (this.inputClass = "success-input") : (this.inputClass = "warning-input");
        }
    }

  },

  methods: {
    eyeClicked() {
      this.type = this.type === "password" ? "text" : "password";
      this.eyeImage =
        this.type === "password" ? this.eyeSlashImage : this.eyeFaImage;
    },

    inputClicked() {
      this.labelClass = "active-color";
      this.inputClass = "active-input";
    },

    blured() {
      this.labelClass = "passive-color";
      this.inputClass = "passive-input";
    },

  }
};
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
span {
  width: 5px;
  border-radius: 50%;
  border: 0;
  height: 5px;
  background-color: #e0e0e0;
  margin-top: 5px;
}

.strength-meter {
  display: flex;
  flex-direction: column;
  position: absolute;
  right: 0px;
  top: -20px;
}

.input-eye {
  position: relative;
  display: flex;
}

img {
  position: absolute;
  right: 0px;
  top: 0px;
  margin-right: 10px;
  cursor:pointer;
}

.input {
  width: 100%;
  border: 0px;
  margin-bottom: 2vw;
  box-shadow: 0 2px 0 0 #e5e5e5;
}

.passive-input {
  box-shadow: 0 2px 0 0 #e5e5e5;
}

.active-input {
  box-shadow: 0 2px 0 0 #4a90e2;
}

.success-input {
  box-shadow: 0 2px 0 0 green;


}.warning-input {
  box-shadow: 0 2px 0 0 red;
}

.passive-color {
  color: #a1a1a1;
}

.active-color {
  color: #4a90e2;
}

.success-color{
  color: green;
}

.warning-color{
  color: red;
}

p {
  margin-bottom: 0vw;
}

.strength-1 {
  background-color: red;
}

.strength-2 {
  background-color: orange;
}

.strength-3 {
  background-color: yellow;
}

.strength-4 {
  background-color: greenyellow;
}
</style>
