<template>
<div ref="hofApp" id="hofApp">
<Navbar />
<Track />
</div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Dog from './components/Dog.vue'
import Track from './components/Track.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  data() {
    return {
    showModal: true
    }
  },
  components: {
    Navbar, Dog, Track, Footer
  },
  methods: {
  toggleModal() {
  this.showModal = !this.showModal
  },
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
  margin-top: 0px;
}







</style>
