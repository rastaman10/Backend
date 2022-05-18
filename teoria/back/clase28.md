![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")


# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)
### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Clase 28

### WebSockets
- [WebSockets en Wikiwand](https://www.wikiwand.com/es/WebSocket)
- [Introducción a los WebSockets: incorporación de sockets a la Web en HTML5Rocks!](https://www.html5rocks.com/es/tutorials/websockets/basics/)
- [Start Using HTML5 WebSockets Today](https://code.tutsplus.com/tutorials/start-using-html5-websockets-today--net-13270)
- [Módulo WebSockets para server en node.js](https://github.com/websockets/ws)
- [WebSocket | MDN](https://developer.mozilla.org/es/docs/Web/API/WebSocket)

![WS_Sockets](../../assets/back/clase28/ea23e52c-0327-4892-902e-5558750ec543.png)

- Protocolo de comunicación que se negocia sobre HTTP
- Full-duplex
- Única conexión permanente (Siempre conectado)
- Stream de mensajes
- Contenido en tiempo real
- Orientado a "eventos" (mensajes)
- Baja latencia


**Entendiendo los eventos**

![Sockets](../../assets/back/clase28/b1e9c41f-a93f-4c66-85ad-957ae970d8ec.png)


**Negociación del protocolo WebSocket**

> Para establecer una conexión WebSocket, el cliente manda una petición de negociación WebSocket, y el servidor manda una respuesta de negociación WebSocket
> [WebSockets en Wikiwand](https://www.wikiwand.com/es/WebSocket)



### WS: Nativo

- [Soporte](http://caniuse.com/#search=websocket)
- [Documentación en MDN](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
- [Ejemplo online de WebSocket nativo](https://javascript.info/websocket)
- [Demo WebSocket para mostrar en tiempo realtransacciones de Bitcoins.](https://codepen.io/ulisesgascon/pen/JWRMbG)
- [API WebSocket Blockchain](https://www.blockchain.com/api/api_websocket)

**Abrir la conexión**
```javascript
var myWebSocket = new WebSocket("ws://www.websockets.org");
```

**Gestión de Eventos**

- Siempre dispondremos del parametro event.
```javascript
myWebSocket.onopen = function() { console.log("Connection open ..."); };
myWebSocket.onmessage = function(evt) { console.log( "Received Message: ", evt.data); };
myWebSocket.onclose = function() { console.log("Connection closed."); };      
```

**Envio de mensajes**
```javascript
myWebSocket.send("Hello WebSockets!");
```

**Cerrar la conexión**
```javascript
myWebSocket.close();
```

### WS: socket.io

![Sockets](../../assets/back/clase28/e3c7432f-687a-4f4c-9534-3fb2a1a6917a.png)

Caracrerísticas:
- Fácil
- Soporte a navegadores obsoletos (Fallback)
- Popular
- Extraordinariamente simple

Eventos reservados:
- socket.on("connect", cb)
- socket.on("disconnect", cb)
- socket.on("error", cb) *Solo cliente*
- socket.on("message", cb)

**Abrir la conexión**
```javascript
  var socket = io("url");
```

**Gestión de Eventos**
```javascript
  socket.on('channel', function(data) { 
    console.log( "Received Message: ", data); 
  });
```

**Envio de mensajoes**
```javascript
socket.emit('channel', data);
```

**Cerrar la conexión**
```javascript
socket.disconnect() 
socket.close(); // Si quieres reabrir. -> socket.connect();
```

### Nativo vs. Librerías

- [Differences between socket.io and websockets en Stackoverflow](http://stackoverflow.com/a/38558531)
- [WebSocket and Socket.IO by DWD](https://davidwalsh.name/websocket)
- [An Introduction to WebSockets by Matt West](http://blog.teamtreehouse.com/an-introduction-to-websockets)

### Ejemplos
- [Ejemplo chat socket.io](https://socket.io/get-started/chat/)
- [Más ejemplos socket.io](https://socket.io/#examples)
- [Full socket.io client and server example](https://gist.github.com/luciopaiva/e6f60bd6e156714f0c5505c2be8e06d8)

### Demos WebSocket con socket.io
- [Ejemplo chat socket.io](https://socket.io/get-started/chat/)
- [Streaming video con WebSocket](https://github.com/10-Minutos-Programando/streamingVideo.git)
- [building-a-currency-ticker-with-nodejs-and-socket-io](https://medium.com/weekly-webtips/building-a-currency-ticker-with-nodejs-and-socket-io-3718280f1803)

![WS](../../assets/back/clase28/wsmeme.jpeg)


