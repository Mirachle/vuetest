<template>
    <div id="app" class="full" style="height:100%; margin:0%; padding:0px;">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.full {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
@media only screen and (max-width: 655px) {
    h1{
        font-size:6vw;
    }

    h2{
        font-size:6vw;
    }

    h4{
        font-size:3vw;
    }

    h6{
        font-size:3vw;
    }

  }

</style>
