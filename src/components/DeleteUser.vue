<template>
  <button @click="deleteUser">Delete</button>
</template>

<script>
export default {
  props: ["userid"],
  methods: {
    deleteUser() {
      fetch("https://jsonplaceholder.typicode.com/posts/" + this.userid, {
        method: "DELETE",
      });
    },
  },
  mounted() {},
};
</script>
