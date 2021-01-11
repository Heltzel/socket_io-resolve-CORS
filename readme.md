# Resolve the CORS problem for Socket.io

## Server side

 The default port for React is 3000

 <small>server/index.js</small>

```javascript
const app = require('express')()
const http = require('http').createServer(app)
const io = require('socket.io')(http, {
  cors: {
    origin: 'http://localhost:3000',
    methods: ['GET', 'POST'],
    allowedHeaders: ['my-custom-header'],
    credentials: true,
  },
})

http.listen(4000, () => {
  console.log('listening on *:4000')
})
```

## Client 

Port 4000 is set in the server

 <small>client/src/App.js</small>

```javascript
import io from 'socket.io-client'
const socket = io.connect('http://localhost:4000')
```
