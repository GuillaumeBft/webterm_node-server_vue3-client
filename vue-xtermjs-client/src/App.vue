<template>
  <body>
    <div id="terminal-container"></div>
  </body>
</template>

<script>
//import { Terminal } from 'xterm'
import { TerminalUI } from "./TerminalUI";
import io from "socket.io-client";

export default {
  name: 'App',
  data() {
    return {
        serverAddress: "127.0.0.1:8080"
    }
  },
  methods: {
    connectToSocket(serverAddr) {
      return new Promise(res => {
        const socket = io(serverAddr);
        res(socket);
      });
    },
    startTerminal(container, socket) {
      const terminal = new TerminalUI(socket);
      terminal.attachTo(container);
      console.log("startTerminal")
      terminal.startListening();
    },
    start() {
      const container = document.getElementById("terminal-container");

      this.connectToSocket(this.serverAddress).then(socket => {
        this.startTerminal(container, socket);
      });
    }
  },
  mounted() {
    this.start();
  }
}
</script>

<style>

</style>
