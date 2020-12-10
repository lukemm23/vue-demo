<template>
<h1>{{title}}</h1>
<p>Welcome...</p>
<!-- :header and :text is passing down data by props -->
<!-- :header="header" :text="text"  (deleted) -->
<!-- @close is a custom event listening to emitted event from modal component to close modal -->
<teleport to=".modals" v-if="showModal">
  <Modal theme="sale" @close="toggleModal">
    <!-- demo of a named slot: v-slot:links signifies the name of the slot -->
    <template v-slot:links>
      <a href="#">Sign up now</a>
      <a href="#">More info</a>
    </template>

    <!-- this is passed down to modal as slot, must use <slot></slot> tag to render -->
    <h1>Ninja Giveaway!</h1>
    <p>Grab your ninja swag for half price! </p>
  </Modal>
</teleport>

<button @click="toggleModal">open modal</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components:{Modal},
  data(){
    return{
      title:'My first VUE app!',
      // these are passed down on modal component
      header:'Sign up for the giveaway!',
      text:'Grab your ninja swag for half price!',
      showModal:false
    }
  },
  methods:{
    toggleModal(){
      this.showModal = !this.showModal
    },

    handleClick(){
      console.log(this.$refs.name)
      //adds class 'active' to referenced element
      this.$refs.name.classList.add('active')
      // focuses on the referenced element
      this.$refs.name.focus()
    }
  }
}
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
h1{
  border-bottom: 1px solid #aaa;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
