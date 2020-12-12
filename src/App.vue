<template>
  <h1>{{ title }}</h1>
  <br />
  <input type="text" ref="name" />
  <br />
  <button @click="handleClick">click me</button>
  <teleport to=".modals" v-if="showModal">
    <Modal theme="" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Sign up for this</h1>
      <p>This is text.</p>
    </Modal>
  </teleport>
  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up for newsletter</h1>
      <p>This is text 2.</p>
    </Modal>
  </div>
  <button @click="toggleModal">Open Modal</button>
  <button @click="toggleModalTwo">Open Modal 2</button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My first Vue app by CLI",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      this.$refs.name.classList.add("active");
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
button {
  background: #bbb;
  padding: 10px;
  border: none;
  border-radius: 4px;
  margin: 10px;
  font-size: 16px;
  color: #333;
}
</style>
