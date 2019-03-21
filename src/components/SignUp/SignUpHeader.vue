<template>
  <div>
    <h2>{{title}}</h2>
    <h4>{{subtitle}}</h4>
  </div>
</template>

<script>

export default {
  name: 'SignUpHeader',
  data() {
    return {
      title: "Do you already have an account?",
      subtitle: "That's awesome! You can login by clicking on the button below. To skip this next time, you can ask us to remember your login creditials.",
    };
  },
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h2{
    margin-top: 2vw;
    margin-bottom: 1vw;
}

</style>
