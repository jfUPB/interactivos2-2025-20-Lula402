# Unidad 1

## 🛠 Fase: Apply

### Link ejemplo escogido: https://editor.p5js.org/generative-design/full/HJ2Wx9qq61N

### Link Sketch modificado: 

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
   

### <p align=center> Explore </p>

### <p align=center> Tinker </p>

