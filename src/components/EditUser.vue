<template>
  <div>
    <editmodal
      v-bind:users="userid"
      v-show="showModal"
      @close-modal="showModal = false"
    />
    <div class="save-btn">
      <button @click="showModal = true">Edit</button>
    </div>
  </div>
</template>

<script>
import editmodal from "../components/EditModal.vue";
export default {
  props: ["userid"],
  components: {
    editmodal,
  },
  data() {
    return {
      showModal: false,
    };
  },
  methods: {
    // UserUpdate() {
    //   this.$emit("Updateuser", this.id);
    // },
  },
};
</script>
