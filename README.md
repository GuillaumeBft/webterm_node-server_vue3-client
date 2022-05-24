# Web terminal node-server + vue3-client

A web terminal with 2 components :
- A simple node server (**use node-pty** and **socket.io**)
- A vue3 client (use **xterm** and **socket.io-client**)

## Version
Node : v14.17.6
npm : 8.10.0

## To run
### Server
```
cd node-pty-server
npm install
node index.js
```
### Client
```
cd vue-xtermjs-client
npm install
npm run serve
```
Then, open web browser on http://localhost:8080
