<template>
  <div>
  	<h1>{{ title }}</h1>
    <h6>{{ subtitle }}</h6>
  </div>
</template>

<script>

export default {
  name: 'LoginHeader',
  data() {
    return {
      title: "Welcome to Acme.",
      subtitle: "Create your account by filling the form bellow.",
    };
  },
};

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: #757575;
}

h6 {
  color: #a1a1a1;
  margin-bottom: 3vw;
}

</style>
