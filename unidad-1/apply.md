# Unidad 1

## 🛠 Fase: Apply

### Link ejemplo escogido: https://editor.p5js.org/generative-design/full/HJ2Wx9qq61N

### Link Sketch reconstruido: https://editor.p5js.org/Lula402/full/f0DQBp8he

### <p align=center> Deconstrucción/reconstrucción </p>

### <p align=center> Select </p>
 Link ejemplo escogido: https://editor.p5js.org/generative-design/full/HJ2Wx9qq61N

### <p align=center> Describe </p>

<p align=center>
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/36c67245-b213-49e7-81e3-c6e01eafc1b5" />
 </p>

- ***Formas:*** son curvas. No hay letras.
- ***Funcionamiento:*** Las curvas se dibujan por medio de una lineas que parecen funcionar como si fuera un compás. Son 3 lineas unidas por dos puntos, las cuales se van moviendo y cruzandose entre si mientras van pintando las curvas con el color correspondiente.
- ***Interactividad:***
  
  Arrow arriba: crecen las lineas, entonces ocupa más espacio del canvas.
  
  Arrow abajo: decrecen las lineas entonces la figura se pinta más pequeña y con más curvas.
  
  Arrow derecha: aumenta la cantidad de puntos que dibujan.
  
  Arrow izquierda: disminuye la cantidad de puntos que dibujan.
  
  1: esconde las lineas y los puntos que dibujan.
  
  2: esconde la figura que se está dibujando.
  
  +: dibuja más rápido, pero tambien hace que se vea menos redonda la figura, sino que se ve más puntuda asi:
  
  <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/17c17be7-4592-4fab-bdba-e207cb0eefda" />

  
  -: dibuja más lento.
  
  delete: se limpia el canvas.
- ***Colores:*** verde limón, verde menta, azul, morado y rosado.
- ***grids:*** al parecer hay una simetría respecto al centro, porque se dibuja lo mismo en los tres lados, aunque no se dibuje a la misma vez.
- ***rhythm:*** las curvas verdes se dibujan a la misma velocidad y la curva morada, rosada y azul se dibujan a la misma velocidad entre sí, pero más rápido que las verdes.
- ***Repetitions:*** primero se dibuja la mitad de la primera punta, luego las lineas pasan a dibujar la segunda punta por completo y por ultimo la tercera y la mitad faltante de la primera punta.


### <p align=center> Analyze </p>

Los componentes que identifico a primera vista al interactuar con el ejemplo son:

- Speed, para determinar la velocidad a la que se pintan.
- Lectura de algunas teclas como input
- Stroke, para dibujar las curvas.
- Una función draw que a diferencia de otros ejercicios que he hecho no limpia el background del canvas en cada frame.
- Sistema de coordenadas: deben haber posisicones para poder centrar las lineas que dibujan.
- Deben haber ángulos, junto con la speed porque las lineas que dibujan rotan y se transladan..
- Funciones para la acción de cada tecla.
- Función set up, para poder determinar las cosas bases del programa, como el canvas, color del canvas, colores o variables que no van a cambiar y se van a inicializar en cada frame.
  
### <p align=center> Convert </p>

1.

```js
function setup() {
  createCanvas(600, 600);
  background(255);
  
}

function draw() {
 
}

function keyPressed (){
  
  if (key == DELETE ){
    
  }
  
  if (key == '+'){
      
      }
  
  if (key == '-'){
      
      }
  
  if (key == UP_ARROW){
      
      }
  
  if (key == DOWN_ARROW){
      
      }
  
  if (key == LEFT_ARROW){
      
      }
  
   if (key == RIGHT_ARROW){
      
      }
   
   if (key == '1'){
     
   }
  
   if (key == '2'){
     
   }
  
   if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
}
```
2. A partir de acá me sentí muy perdida porque la verdad no sabía como funcionaba nada, entonces me tuve que apoyar del código original. Voy a entender que hace, para poder que en el futuro pueda hacer este paso de ***convert*** sin atascarme tan rápido:

En esta parte se declaran todas las variables globales que se van a necesitar. Por el momento no se que hacen: shape, joints, pendulumPath. 

Respecto a las siguientes si tengo mi suposición de que almacenan: 
- lineLength: la  longitud de las lineas que dibujan, porque esa se puede modificar con las arrows up and down.
- speedRelation: la relación de velocidad entre las strokes de colores, porque es diferente.
- center: Lo que mencioné arriba de que debe haber un sistema coordenado para centrar los trazos.
- angle: el ángulo en el que van las líneas que dibujan, me imagino que este valor se va actualizando porque esas lineas van girando.
- maxAngle: el ándulo max es 360° porque ahi la linea termina de dar la vuelta y la variable angle debería iniciar again en 0.
- speed: la velocidad a la que se pinta la figura.
- showPendulum: guarda true si si se está mostrando el dibujo, esto puede cambiar con la tecla 1.
- showPendulumPath: guarda true si si se están mostrando las lineas, esto cambia con la tecla 2.

```js
let shape;
let joints = 5;
let lineLength = 100;
let speedRelation = 2;
let center;
let pendulumPath;
let angle = 0;
let maxAngle = 360;
let speed;
let showPendulum = true;
let showPendulumPath = true;
```

3. un setup si lo reconozco desde antes, acá se prepara un canvas blanco de 600px x 600px. Se determina que las figuras que se vayan a pintar van a ser sin fill y que el trazo va a tener un grosor de 1px. Luego tambien se establece que el center va a ser en la mitad del canvas y se crea un vector con eso. Se llama a la función startDrawing que me imagino que es para dejar todo listo para la 1era iteración.

```js
function setup() {
  createCanvas(600, 600);
  background(255);
  noFill();
  strokeWeight(1);
  center = createVector(width / 2, height / 2);
  startDrawing();
}
```

4. Se define un array pendulumPath que ya se había declarado arriba. Luego ese pendulum path se recorre con un for y el tope son la cantidad de Joints, osea 5. En cada iteración del for se hace un push, osea que se añade un array [] dentro del pendulumPath. Va a quedar un array, y dentro de cada uno de los 5 espacios de ese array, van a guardarse otros 5 arrays correspondientemente.

<p align=center>  

<img src="https://github.com/user-attachments/assets/5d430c33-f06d-481a-ba04-52fb94f2a3d0" width="400" height="300">

</p>

El angle se hace 0 para volverlo a inicializar.

En Speed se calcula la velocidad a la que se pinta todo el dibujo. La velocidad va a depender de que tantos joints hayan y de cual sea la speedRelation. Si los Joints aumentan entonce 1.75 se va a elevar a una cantidad más grande, y por ende va a quedar un denominador más grande. Lo mismo para con la speedRelation. La velocidad se reduce a medida que aumentan los joints o la speedRelation.

```js
function startDrawing() {
  pendulumPath = [];
  // new empty array for each joint
  for (let i = 0; i < joints; i++) {
    pendulumPath.push([]);
  }

  angle = 0;
  speed = 8 / pow(1.75, joints - 1) / pow(2, speedRelation - 1);
}
```

5. Yo pensaba que el background no se limipaba, pero resulta que si en cada frame. El angulo va incrementando pues para poder que se mueva.

Cada frame se actualiza la posición de cada joint, si ya recorrió los 360° para de calcular porque ya no entra al if. Dentro del ciclo for se calcula la posición de cada joint, el angulo segun el joint e intercaladamente giran para sentidos contrarios. Se calcula la longitud a la que va a estar el siguiente joint. 

Se dibuja una elipse, que se ve como un puntico en la posición en x & y del joint, luego se pinta una linea conectando la posicion inicial (x,y) y la next (x,y).

Se almacena la posición del nextPos para poder saber cual va a ser el trayecto y luego pos se actualiza = nextPos para poder avanazar.

Ahora si lo que realmente pinta la figura. pendulumPath es un aray que se recorre con un for. Con begin y end shape se recorre todo el path y se unen los vertices con una linea usando vertex. Tambipen se usa map para convertir el # del joint al color que le correspondería. 

```js
function draw() {
  background(0, 0, 100);

  angle += speed;

  // each frame, create new positions for each joint
  if (angle <= maxAngle + speed) {
    // start at the center position
    let pos = center.copy();

    for (let i = 0; i < joints; i++) {
      let a = angle * pow(speedRelation, i);
      if (i % 2 == 1) a = -a;
      let nextPos = p5.Vector.fromAngle(radians(a));
      nextPos.setMag(((joints - i) / joints) * lineLength);
      nextPos.add(pos);

      if (showPendulum) {
        noStroke();
        fill(0, 10);
        ellipse(pos.x, pos.y, 4, 4);
        noFill();
        stroke(0, 10);
        line(pos.x, pos.y, nextPos.x, nextPos.y);
      }

      pendulumPath[i].push(nextPos);
      pos = nextPos;
    }
  }

  // draw the path for each joint
  if (showPendulumPath) {
    strokeWeight(1.6);
    for (let i = 0; i < pendulumPath.length; i++) {
      let path = pendulumPath[i];

      beginShape();
      let hue = map(i, 0, joints, 120, 360);
      stroke(hue, 80, 60, 50);
      for (let j = 0; j < path.length; j++) {
        vertex(path[j].x, path[j].y);
      }
      endShape();
    }
  }
}
```

6. Es la función de keyPressed, pero es bastante intuitiva entonces si la entendí.

### <p align=center> Explore </p>
> ### Explore #1
Cambié el color del background, porque me di cuenta que tenia un bug y es que en el codigo original es (0,0,100) entonces se debería ver azul, pero en realidad se ve blanco, luego modifiqué esos parametros y de la nada ya si se veia azul, de todas maneras lo dejé en (100,100,0). Aumenté speedRelation, maxAngle = 180°, joints = 10 y lineLength = 50. Corregí la función de keypressed porque resulta que a algunos no se les ponia ***key*** sino ***keyCode***, ahora si funciona.

<img width="363" height="292" alt="image" src="https://github.com/user-attachments/assets/9311560a-4f54-4abb-b0a8-214ae2fbe4f1" />

> ### Explore #2

### <p align=center> CÓDIGO FUENTE DE MI VERSIÓN </p>

```js
let shape;
let joints = 5;
let lineLength = 100;
let speedRelation = 2;
let center;
let pendulumPath;
let angle = 0;
let maxAngle = 360;
let speed;
let showPendulum = true;
let showPendulumPath = true;

function setup() {
  createCanvas(1000, 1000);
  background(255);
  noFill();
  strokeWeight(2);
  colorMode(HSB, 360, 100, 100, 100);
  center = createVector(width / 2, height / 2);
  startDrawing();
}

function startDrawing() {
  pendulumPath = [];
  // new empty array for each joint
  for (let i = 0; i < joints; i++) {
    pendulumPath.push([]);
  }

  angle = 0;
  speed = 8 / pow(1.75, joints - 1) / pow(2, speedRelation - 1);
}

function draw() {
  background(0, 0, 0);

  angle += speed;

  // each frame, create new positions for each joint
  if (angle <= maxAngle + speed) {
    // start at the center position
    let pos = center.copy();

    for (let i = 0; i < joints; i++) {
      let a = angle * pow(speedRelation, i);
      if (i % 2 == 1) a = -5;
      let nextPos = p5.Vector.fromAngle(radians(a));
      nextPos.setMag(((joints - i) / joints) * lineLength);
      nextPos.add(pos);

      if (showPendulum) {
        noStroke();
        fill(50, 255);
        ellipse(pos.x, pos.y, 4, 4);
        noFill();
        stroke(255, 50);
        line(pos.x, pos.y, nextPos.x, nextPos.y);
      }

      pendulumPath[i].push(nextPos);
      pos = nextPos;
    }
  }

  // draw the path for each joint
  if (showPendulumPath) {
    strokeWeight(6);
    for (let i = 0; i < pendulumPath.length; i++) {
      let path = pendulumPath[i];

      beginShape();
      // let hue = map(i, 0, joints, 120, 360);
      let hue = frameCount % 360;
      stroke(hue, 100, 100, 50);
      for (let j = 0; j < path.length; j++) {
        vertex(path[j].x, path[j].y);
      }
      endShape();
    }
  }
}

function keyPressed() {
  if (keyCode == DELETE) {
    startDrawing();
  }

  if (key == "+") {
    speedRelation += 0.5;
    if (speedRelation > 5) speedRelation = 5;
    startDrawing();
  }

  if (key == "-") {
    speedRelation -= 0.5;
    if (speedRelation < 2) speedRelation = 2;
    startDrawing();
  }

  if (keyCode == UP_ARROW) {
    lineLength += 2;
    startDrawing();
  }

  if (keyCode == DOWN_ARROW) {
    lineLength -= 2;
    startDrawing();
  }

  if (keyCode == LEFT_ARROW) {
    joints--;
    if (joints < 1) joints = 1;
    startDrawing();
  }

  if (keyCode == RIGHT_ARROW) {
    joints++;
    if (joints > 10) joints = 10;
    startDrawing();
  }

  if (key == "1") {
    showPendulum = !showPendulum;
  }

  if (key == "2") {
    showPendulumPath = !showPendulumPath;
  }

  if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");
}
```
<p align=center>
 
<img width="239" height="215" alt="image" src="https://github.com/user-attachments/assets/2f30cbf0-758f-4ff4-b4f5-43edafa70432" />

<img width="270" height="306" alt="image" src="https://github.com/user-attachments/assets/fe644173-c8d2-4005-92d5-48a74410f463" />

<img width="217" height="229" alt="image" src="https://github.com/user-attachments/assets/5a926a5e-e3af-4d06-ac87-44112513ecc4" />

</p>

### Video: https://youtube.com/shorts/1gInJmx_yfM?feature=share

### <p align=center> Tinker </p>
> ### Tinker #1

<p align=center>
<img width="266" height="214" alt="image" src="https://github.com/user-attachments/assets/719d3510-4155-483c-b884-db894ae9d01a" />
</p>

> ### Tinker #2
<p align=center>
<img width="262" height="223" alt="image" src="https://github.com/user-attachments/assets/860ca385-b871-4e57-8a7a-d66f2a0259e1" />
</p>

> ### Tinker #3
<p align=center>
<img width="263" height="215" alt="image" src="https://github.com/user-attachments/assets/9c9d32e2-e762-42ef-abb6-19da011e8fd5" />
</p>

> ### Tinker #4
<p align=center>
<img width="226" height="230" alt="image" src="https://github.com/user-attachments/assets/a348e075-8cde-4a95-8211-94a7629ea893" />
</p>

### Código modificado del tinker:

```js
let shape;
let joints = 5;
let lineLength = 100;
let speedRelation = 2;
let center;
let pendulumPath;
let angle = 0;
let maxAngle = 700;
let speed;
let showPendulum = true;
let showPendulumPath = true;

function setup() {
  createCanvas(1000, 1000);
  background(frameCount % 360);
  noFill();
  strokeWeight(2);
  colorMode(HSB, 360, 100, 100, 100);
  center = createVector(width / 2, height / 2);
  startDrawing();
}

function startDrawing() {
  pendulumPath = [];
  // new empty array for each joint
  for (let i = 0; i < joints; i++) {
    pendulumPath.push([]);
  }

  angle = 0;
  speed = 8 / pow(1.75, joints - 1) / pow(2, speedRelation - 1);
}

function draw() {
  background(frameCount % 360, 80, 80);

  angle += speed;

  // each frame, create new positions for each joint
  if (angle <= maxAngle + speed) {
    // start at the center position
    let pos = center.copy();

    for (let i = 0; i < joints; i++) {
      let a = angle * pow(speedRelation, i);
      if (i % 2 == 1) a = -5;
      let nextPos = p5.Vector.fromAngle(radians(a));
      nextPos.setMag(((joints - i) / joints) * lineLength);
      nextPos.add(pos);

      if (showPendulum) {
        noStroke();
        fill(50, 255);
        ellipse(pos.x, pos.y, 4, 4);
        noFill();
        stroke(255, 50);
        line(pos.x, pos.y, nextPos.x, nextPos.y);
      }

      pendulumPath[i].push(nextPos);
      pos = nextPos;
    }
  }

  // draw the path for each joint
  if (showPendulumPath) {
    strokeWeight(0.5);
    for (let i = 0; i < pendulumPath.length; i++) {
      let path = pendulumPath[i];

      beginShape();
      // let hue = map(i, 0, joints, 120, 360);
      let hue = (100,100,0);
      stroke(hue, 100, 0, 50);
      fill(hue, 0, 100, 50);
      for (let j = 0; j < path.length; j++) {
        vertex(path[j].x, path[j].y);
      }
      endShape();
    }
  }
}

function keyPressed() {
  if (keyCode == DELETE) {
    startDrawing();
  }

  if (key == "+") {
    speedRelation += 0.5;
    if (speedRelation > 5) speedRelation = 5;
    startDrawing();
  }

  if (key == "-") {
    speedRelation -= 0.5;
    if (speedRelation < 2) speedRelation = 2;
    startDrawing();
  }

  if (keyCode == UP_ARROW) {
    lineLength += 2;
    startDrawing();
  }

  if (keyCode == DOWN_ARROW) {
    lineLength -= 2;
    startDrawing();
  }

  if (keyCode == LEFT_ARROW) {
    joints--;
    if (joints < 1) joints = 1;
    startDrawing();
  }

  if (keyCode == RIGHT_ARROW) {
    joints++;
    if (joints > 10) joints = 10;
    startDrawing();
  }

  if (key == "1") {
    showPendulum = !showPendulum;
  }

  if (key == "2") {
    showPendulumPath = !showPendulumPath;
  }

  if (key == "s" || key == "S") saveCanvas(gd.timestamp(), "png");
}
```
