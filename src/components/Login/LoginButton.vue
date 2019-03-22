<template>
  <div>
    <button class="btn login-btn" style="float: right;" @click="$emit('clicked')">{{text}}</button>
  </div>
</template>

<script>

export default {
  name: 'LoginButton',
  data() {
    return {
      text: "Sign up",
    };
  },
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.login-btn {
    margin: auto;
    margin-right: 0%;
    text-align: center;
    padding-left: 2vw;
    padding-right: 2vw;
    background-color: #4a90e2;
    color: #ffffff;
}

</style>
