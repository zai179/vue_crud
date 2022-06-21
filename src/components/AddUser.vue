<template>
  <div>
    <savemodal v-show="showModal" @close-modal="showModal = false" />
    <div class="save-btn">
      <button @click="showModal = true">Add</button>
    </div>
  </div>
</template>

<script>
import savemodal from "../components/SaveModal.vue";
export default {
  components: {
    savemodal,
  },
  data() {
    return {
      showModal: false,
    };
  },
  methods: {},
};
</script>
