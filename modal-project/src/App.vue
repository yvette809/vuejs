<template>
  <h1>{{ title }}</h1>
  <p>welcome...</p>
  <div v-if="showModal">
    <ModalItem :header="header" :text="text" theme="sale" @close='toggleModal' />
  </div>
  <button @click="toggleModal">Open Modal</button>
</template>

<script>
import ModalItem from "./components/ModalItem.vue";
export default {
  name: "App",
  components: { ModalItem },
  data() {
    return {
      title: "my first view app",
      header: "sign up for a give away",
      text: "grab your ninja swabs for half price",
      showModal: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
