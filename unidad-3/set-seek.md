# Unidad 3

## 🔎 Fase: Set + Seek

> ACTIVIDAD 1

### <p align=center> Diagrama de bloques </p>

<p align=center>
  
<img width="1795" height="396" alt="Diagrama de Bloques Server - clientes" src="https://github.com/user-attachments/assets/583245f8-b985-489d-b421-8f81daf86459" />

</p>

### <p align=center> Paso a paso  </p>

### Paso 1: Captura en el móvil (mobile.js con p5.js)

En este paso se recibe la info del tactil del movil, se trata la info, se serializa en json y se emite al server.


+ Loop principal

  + draw() corre constantemente (~60 FPS), refrescando la pantalla.

+ Detección táctil

  + touchMoved() se ejecuta cada vez que el usuario mueve el dedo.

+ Procesamiento del evento táctil

  + Calcula el desplazamiento respecto a la última posición registrada (lastTouchX, lastTouchY).

  + Si el movimiento supera un umbral (threshold) o es el primer toque:

    + Construye un objeto con la información del toque:
      
```js
{ type: 'touch', x: mouseX, y: mouseY }
```

    + Lo serializa a JSON: JSON.stringify(touchData).

    + Lo envía al servidor vía WebSocket:
    
```js
socket.emit('message', JSON.stringify(touchData));
```

    + Actualiza lastTouchX y lastTouchY.



### 2. Túnel de VS Code + Servidor Microsoft

En este paso el server recibe la info y la reemite al resto de clientes exceptuando al emisor original.

+ El cliente móvil y el cliente de escritorio no se conectan directo al servidor local.
Los datos viajan primero por un túnel creado en VS Code, pasan por el servidor de Microsoft y desde ahí llegan a tu servidor local.
Este túnel actúa como puente seguro que redirige el tráfico desde Internet hasta el  server.


### 3. Recepción en el servidor (server.js con Express + Socket.IO)

```js
socket.on('message', (message) => {
    console.log(`Received message => ${message}`);
    socket.broadcast.emit('message', message);
});
```

+ En server.js, dentro de io.on('connection', ...), está registrado.

  + socket.on('message'): captura el evento procedente de ese móvil.

  + Log: imprime el JSON recibido.

  + socket.broadcast.emit: re-emite el mismo evento 'message' a todos los demás sockets conectados al mismo namespace excepto el emisor. 



### 4. Recepción en el escritorio (desktop.js con p5.js)
En este paso recibe la info, la extrae, después actualiza los datos. 

```js
socket.on('message', (data) => {
    console.log(`Received message: ${data}`);
    try {
        let parsedData = JSON.parse(data);
        if (parsedData && parsedData.type === 'touch') {
            circleX = parsedData.x;
            circleY = parsedData.y;
        }
    } catch (e) { ... }
});
```

+ En desktop.js, el cliente ya tiene sus listeners
  
  + Recepción: el escritorio recibe la misma cadena JSON reenviada por el servidor.

  + Parsing: intenta JSON.parse.

  + Validación ligera: verifica type === 'touch'.

  + Actualización de estado: asigna circleX/circleY.

### 5. Renderizado en el escritorio.

En este paso vuelve a renderizar el círculo acorde a los datos actualizados.

```js
background(220);
fill(255, 0, 0);
ellipse(circleX, circleY, 50, 50);
```

+ El loop draw() de p5.js corre ~60 FPS

  + Como circleX/circleY ya se actualizaron, el círculo se dibuja en la nueva posición en el siguiente frame.
