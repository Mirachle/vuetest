<template>
  <div class="image">
    <signup-img/>
    <signup-header/>
    <signup-button/>
  </div>
</template>

<script>
import SignUpImg from '@/components/SignUp/SignUpImg';
import SignUpHeader from '@/components/SignUp/SignUpHeader';
import SignUpButton from '@/components/SignUp/SignUpButton';

export default {
  name: 'SignUpPage',
  data() {
    return {

    };
  },

components: {
    "signup-img": SignUpImg,
    "signup-header": SignUpHeader,
    "signup-button": SignUpButton,
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.image {
    background: transparent;
    color: #ffffff;
    border: 0ch;
    background-color: transparent;
    padding: 5%;
    margin: 15%;
    margin-bottom: 0%;
    text-align: left;
}

</style>
