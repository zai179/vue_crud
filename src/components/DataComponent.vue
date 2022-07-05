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
          <td>
            <deleteuser :userid="user" @deleteUser="deleteData($event)" />
            <edituser :userid="user" @Updateuser="updateData($event)" />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import adduser from "../components/AddUser.vue";
import deleteuser from "./DeleteUser.vue";
import edituser from "./EditUser.vue";
import axios from "axios";
export default {
  components: {
    adduser,
    deleteuser,
    edituser,
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

    deleteData(userid) {
      // alert(userid);
      axios
        .delete("https://jsonplaceholder.typicode.com/posts/" + userid)
        .then((response) => {
          let i = this.users.map((data) => data.id).indexOf(userid);
          this.users.splice(i, 1);
          console.log(response);
        });
    },
    updateData(id) {
      axios
        .post("https://jsonplaceholder.typicode.com/posts/" + id)
        .then((response) => {
          this.form = "";
          console.log(response);
        });
    },
  },
  mounted() {
    this.getData();
  },
};
</script>
