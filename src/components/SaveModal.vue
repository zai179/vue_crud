<template>
  <div class="modal-overlay" @click="$emit('close-modal')">
    <div class="modal" @click.stop>
      <form @submit="submit" method="post">
        <label for="">User Name:</label>
        <input
          type="text"
          name="user-name"
          id=""
          v-model="form.name"
          class="form-control"
        />
        <button type="submit">Submit</button>
      </form>
    </div>
    <div class="close" @click="$emit('close-modal')">X</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      form: {},
    };
  },
  methods: {
    submit(e) {
      e.preventDefault();
      axios
        .post("https://jsonplaceholder.typicode.com/posts", this.form, {
          headers: {
            "Content-type": "application/json; charset=UTF-8",
          },
        })
        .then((response) => {
          this.form = "";
          console.log(response);
        });
    },
  },
};
</script>
<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  background-color: #000000da;
}

.modal {
  text-align: center;
  background-color: white;
  height: 100px;
  width: 500px;
  margin-top: 10%;
  padding: 60px 0;
  border-radius: 20px;
}
.close {
  margin: 10% 0 0 16px;
  cursor: pointer;
}
</style>
