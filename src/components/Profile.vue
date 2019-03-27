<template>
  <div class="full">
    <div class="listStyle" v-for="(item,index) in list" :key="index">
      {{item}}
      <button @click="onDelete(index,item)">Delete</button>
    </div>
    <button @click="onAddEvent" class="onAdd">Add</button>
    <br>
    <router-link to="/auth">Back</router-link>
    <router-view/>
  </div>
</template>

<script>
import Swal from "sweetalert2";

export default {
  name: "Profile",
  data() {
    return {
      list: ["elso", "masodik", "harmadik", "negyedik"],
      inputText: ""
    };
  },
  methods: {
    onDelete(index, item) {
      this.list.splice(index, 1);
    },

    onAddEvent() {
      Swal.fire({
        input: "text",
        title: "Írd be az új elemet:",
      }).then(result => {
        if (result.value) {
          this.inputText = (JSON.stringify(result.value)).replace(/"/g, '');
          this.list.push(this.inputText);
        }
      });
    }
  }
};
</script>

<style>
.onAdd {
  position: relative;
  margin-top: 10vh;
}

button {
  font-variant: small-caps;
  color: white;
  font-weight: bold;
  background-color: rgba(2, 2, 2, 0.705);
  border: 0px;
  border-radius: 10%;
}

button:hover {
  color: black;
  background-color: white;
}

.listStyle {
  margin-top: 1vh;
}

.full {
  margin-top: 10vh;
}

a:hover {
  color: white;
  background-color: rgba(2, 2, 2, 0.705);
  text-decoration: none;
}

a {
  color: black;
  background-color: white;
  border: 0px;
  border-radius: 10%;
  font-weight: bold;
  font-variant: small-caps;
  text-decoration: none;
}
</style>
