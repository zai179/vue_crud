<template>
  <div>
    <h3>Crud in vuejs</h3>
    <adduser />
    <table border="">
      <tr>
        <th>Name:</th>
        <th>Action:</th>
      </tr>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.title }}</td>
          <td><deleteuser v-bind:userid="user.id" /></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import adduser from "../components/AddUser.vue";
import deleteuser from "./DeleteUser.vue";
import axios from "axios";
export default {
  components: {
    adduser,
    deleteuser,
  },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    getData() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts/")
        .then((response) => {
          this.users = response.data;
        });
    },
  },
  mounted() {
    this.getData();
    console.log("in data component");
  },
};
</script>
