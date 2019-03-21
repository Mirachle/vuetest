<template>
  <div class="row">
    <h5 @click="boxClicked()">
      <span :class="circle"/>
      {{text}}
    </h5>
  </div>
</template>

<script>
export default {
  name: "LoginCheckbox",
  data() {
    return {
      text: "Remember me.",
      circle: "span-blue"
    };
  },

  methods: {
    boxClicked() {
      this.circle = this.circle === "span-blue" ? "span-white" : "span-blue";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h5 {
  color: #a1a1a1;
  font-size: 1.3vw;
  cursor:pointer;
}

.span-blue {
  width: 1vw;
  border-radius: 50%;
  border: 2px solid #4a90e2;
  height: 1vw;
  margin-right: 0.5vw;
  margin-left: 1.3vw;
  display: inline-block;
  background-color: #4a90e2;
}

.span-white {
  width: 1vw;
  border-radius: 50%;
  border: 2px solid #4a90e2;
  height: 1vw;
  margin-right: 0.5vw;
  margin-left: 1.3vw;
  display: inline-block;
  background-color: white;
}

@media only screen and (max-width: 650px) {
  h5 {
    font-size: 3vw;
  }

.span-white {
  width: 2vw;
  height: 2vw;
  margin-left: 4vw;
  }

  .span-blue {
  width: 2vw;
  height: 2vw;
  margin-left: 4vw;
  }

}
</style>
