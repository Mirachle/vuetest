<template>
  <div class="row kiegeszito">
    <p class="param">
      <img class="logos" src="@/assets/copyright-symbol.png"/>{{param}}</p>
    <p class="terms">{{terms}}
        <span id="1"></span>
        <span></span>
        <span></span>
    </p>
  </div>
</template>

<script>

export default {
  name: 'LoginText',
  data() {
    return {
     param: " 2015 Acme, Inc ",
     terms: ". Terms Privacy ",

    };
  },

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p {
  margin-bottom: 0vw;
}

.kiegeszito {
  padding-left: 18%;
  color: #a1a1a1;
  padding-top: 3vw;
  font-size: 1vw;
}

.terms {
  word-spacing: 10px;
  display: flex;
  align-items: center;
  font-weight: bold;
}

.logos {
  width: 12px;
  height: 12px;
}

span {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background-color: #a1a1a1;
  margin-left: 5px;
}

span[id = "1"]{
  margin-left: 10px;
}

@media only screen and (max-width: 650px) {
    .kiegeszito{
        font-size:3vw;
    }
  }

</style>
