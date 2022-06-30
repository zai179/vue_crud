<template>
  <div class="modal-overlay" @click="$emit('close-modal')">
    <div class="modal" @click.stop>
      <form @submit="updateUser" method="post">
        <label for="">User Name:</label>
        <input
          type="text"
          name="user-name"
          id=""
          v-model="form.title"
          class="form-control"
        />
        <button type="submit">Submit</button>
      </form>
    </div>
    <div class="close" @click="$emit('close-modal')">X</div>
  </div>
</template>

<script>
export default {
  props: ["users"],
  data() {
    return {
      form: this.users,
    };
  },
  methods: {
    updateUser() {
      this.$emit("updateuser", this.users.id);
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
