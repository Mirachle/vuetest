<template>
     <div class="row max" >

        <div class="col-12 col-lg-6 first">
          <login/>
        </div>

        <div class="col-12 col-lg-6 last">
          <signup/>
        </div>

    </div>
</template>

<script>
import LoginPage from '@/components/Login/LoginPage';
import SignUpPage from '@/components/SignUp/SignUpPage';
export default {
  name: 'Auth',
  data() {
    return {

    };
  },
  components: {
    "login": LoginPage,
    "signup": SignUpPage,
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.max {
   height: 100%;
   width: 100%;
   margin: 0px;
   padding: 0%;
}

.first {
    background-color: #f7f7f7;
}

.last {
    background: url('https://farm9.staticflickr.com/8554/8703185923_e29a479ae9.jpg');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

</style>
