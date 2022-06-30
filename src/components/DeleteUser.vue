<template>
  <button @click="deleteUser">Delete</button>
</template>

<script>
export default {
  props: ["userid"],
  methods: {
    deleteUser() {
      this.$emit("deleteUser", this.userid.id);
    },
  },
};
</script>
