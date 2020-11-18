<template>
  <div id="app">
    <img alt="Ai" src="./assets/ai-1.gif">
    <transition name="fade">
      <form
      id="formOne"
      @submit="save"
      action="https://vuejs.org/"
      method="post"
      v-if="!nameSaved">
        <input v-model="myName" placeholder="Your name" required>
        <button>Feed it</button>
      </form>
    </transition>
    
    <Message :userName="myName" v-if="nameSaved" />
  </div>
</template>

<script>
import Message from "./components/Message.vue";

export default {
  name: 'App',
  data: () => {
    return {
      myName: null,
      nameSaved: false
    }
  },
  components: {
    Message
  },
  methods: {
    save(e) {
      e.preventDefault();
      if(this.myName !== null) {
        this.nameSaved = true;
      }
    }
  }
  
}
</script>

<style>
html {
  background: #000;
  color: #fff;
  font-weight: 400;

}
#app {
  font-family: "Inter", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
input {
    background: #ffffff0d;
    padding: 18px 20px;
    outline: 0;
    border: 0;
    border-bottom: 4px solid #fff;
    color: white;
    font-family: inherit;
    font-weight: 600;
    font-size: 30px;
}
form {
  display: flex;

}
button {
      background: #220086;
    border: 0;
    font-size: 22px;
    height: 1;
    padding: 10px 40px;
    color: white;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
