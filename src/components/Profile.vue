<template>
  <div class="full">
    <div class="listStyle row" v-for="(item,index) in list" :key="index">
      <div class="col-5"></div>
      <div class="col-1" style="text-align:left;">{{item}}</div>
      <div class="col-6"><button @click="onDelete(index)" class="profile-btn" style="float:left;">Delete</button></div>
    </div>
    <button @click="onAddEvent" class="onAdd profile-btn">Add</button>
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
      list: ["elso", "masodik", "harmadik", "negyedik"]
    };
  },

  methods: {

    onDelete(index) {
      this.list.splice(index, 1);
    },

    onAddEvent() {
      Swal.fire({
        input: "text",
        title: "Írd be az új elemet:",
        confirmButtonColor: '#000000',
      }).then(result => {
        if (result.value) {
          this.list.push((JSON.stringify(result.value)).replace(/"/g, ''));
        }
      });
    },

  }

};

</script>


<style>

.onAdd {
  position: relative;
  margin-top: 10vh;
  margin-bottom: 10vh;
}

.profile-btn {
  font-variant: small-caps;
  color: white;
  font-weight: bold;
  background-color: rgba(2, 2, 2, 0.705);
  border: 0px;
  border-radius: 10%;
}

.profile-btn:hover {
  color: black;
  background-color: white;
}

.listStyle {
  margin-top: 1vh;
  color: black;
  background-color: white;
  border: 0px;
  border-radius: 10%;
  font-weight: bold;
  font-variant: small-caps;
  text-decoration: none;
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
