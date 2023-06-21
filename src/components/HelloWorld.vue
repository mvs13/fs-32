<template>
  <h1>Our Chat</h1>
  <input type="text" name="" id="" v-model="message">
  <button class="btn" @click="sendMessage()" >Send</button>
</template>

<script>
const { io } = require("socket.io-client");
const socket = io('http://localhost:3001');

socket.on("handshake", (arg) => {
  console.log(arg); 
});

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      message: null
    }
  },
  methods:{
    sendMessage() {
      socket.emit('message', this.message)
      console.log(this.message);
      this.message = null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
