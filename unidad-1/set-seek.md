# Unidad 1

## 🔎 Fase: Set + Seek

> ##  ACTIVIDAD 1

### ¿Qué es el diseño generativo?
El diseño generativo es la fusión entre la tecnología y el diseño. La programación se usa como herramienta o en algunos casos maquinas programadas, como ***Licia He*** con sus ***Plotters***, y al hacer equipo con la mente de un diseñador salen creaciones increibles. El diseñador se encarga de diseñar y programar las reglas y objetivos de este programa generativo, pero luego la magia entra en juego cuando el código es quien se encarga de hacer el diseño final y no solo 1 diseño sino que hay muchos posibles outcomes/resultados para este solo código.

Como el ejemplo del MIT que vimos, donde hicieron un rebrand y sacaron con un diseño generativo 40k logos

<p align = center>
<img width="450" height="294" alt="image" src="https://github.com/user-attachments/assets/d39e0071-6c8f-4af2-b1bb-f631ae280569" />
</p>

<p align = center>
(Foto tomada de aqui https://www.fastcompany.com/1663378/mit-media-labs-brilliant-new-logo-has-40000-permutations-video)
</p>

### Qué es el arte generativo?

El arte generativo es la fusión entre la tecnología y el arte. La programación se usa como herramienta o en algunos casos maquinas programadas, como ***Licia He*** con sus ***Plotters***, y al ser usadas por un artista salen creaciones únicas. Cada artista decide cual es el proceso para crear una pieza, en este caso, los artistas que crean arte generativo programan su arte.

### <p align = center> I Have To Talk To A Plotter by Licia He </p>
<p align = center>
<img width="452" height="221" alt="image" src="https://github.com/user-attachments/assets/987910db-7dc3-4563-bb71-40c1993870e3" /> </p>

<p align = center> (Screenshot tomado de https://youtu.be/jmzVt61-mEE?feature=shared&t=152) </p>

### ¿Cuál es la diferencia entre el diseño/arte generativo vs el diseño/arte tradicional?
La diferencia se centra en que el diseño/arte generativo son **creaciones y procesos interdisciplinarios**, es decir, requieren habilidades y herramientas en más de un solo campo, mientras que el diseño/arte tradicional NO fusiona cosas como la programación, los algoritmos, la IA con las habilidades del diseñador o artista.

### ¿Qué posibilidades crees que esto puede ofrecer a tu perfil profesional? (al finalizar el curso te haré de nuevo esta pregunta)
Las posibilidades que me brinda el arte/diseño generativo a mi perfil profesional son muchas. Como futura profesional en **INGENIERIA** en **DISEÑO** de entretenimiento digital, enfasis en esas dos palabras, quiero apuntar a ser una diseñadora interdisciplinaria. El diseño/arte generativo es un claro ejemplo de las habilidades y creaciones que puedo ofrecer como parte de mi perfil profesional.

Como dice Patrik Hübner, "lo que nos hace falta no es la tecnología. Necesitamos una nueva forma de pensar" y esa es la posibilidad que esto me ofrece.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> ##  ACTIVIDAD 2

### Antes de lo que hemos discutido, ¿Qué pensabas que hacía un Ingeniero en diseño de entretenimiento digital con énfasis en experiencias interactivas?
Antes pensaba que un ingeniero en IDED con enfasis en experiencias interactivas solo hacía aplicaciones o solo hacia experiencias dirigidas a fabricas o empresas. Cuando estaba en introducción a IDED me mostraron un ejemplo de un juego de hacer galletas para la fábrica NOEL, y ese era el referente más cercano que tenía a lo que haciamos en esta línea.

### ¿Qué potencial le ves al diseño e implementación de experiencias inmersivas colectivas?
Le veo mucho pontencial, de que es más complicado y que hay que tener más factores en cuenta? si, pero lo hace más interesante. Una experiencia inmersiva colectiva permite tener más aleatoriedad, ya que son más inputs a tener en cuenta. Como en la referencia de ***Jorge Drexler - Habitación 316 (n1)*** el hecho de que varias personas en la habiatación puedan participar en la experiencia lo hace mucho más enriquecedor. 

De hecho también le veo potencial en sentido de innovador y retador, porque lograr que una experiencia sea inmersiva para todo un grupo de personas no es cualquier bobada. Incluso se me ocurre que la manera en la que interactuan las personas con la experiencia no tiene que ser la misma. Por ejemplo que pasa si en la de ***Arturs Skutelis — Vienkārši Vārdi*** el kinect no está en el rapero sino que está en alguien del publico que baile hiphop y otra persona al llevar el ritmo del rap con los pies se le pone un sensor que detecte el movimiento y que con el beat cambie el color de la visual.

### Nosotros estamos definiendo en TIEMPO REAL una nueva forma de expresión, una nueva forma de interactuar de manera colectiva. Estamos diseñando nuevas maneras de contar historias e interactuar con ellas. ¿Cómo te ves profesionalmente en este escenario?

Me visualizo como toda una creativa e innovadora. Me emociona y me puedo ver a futuro retandome y divirtiendome con estos escenarios y en este campo. Tener que buscar maneras creativas para que en tiempo real la audiencia viva una experiencia inmersiva es 0 monotono y como futura profesional me logro visualizar en eso. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> ##  ACTIVIDAD 3

### Link al ejemplo analizado: http://www.generative-gestaltung.de/2/sketches/?01_P/P_2_1_2_01

### Link a mi versión modificada: [https://editor.p5js.org/Lula402/full/fpiFwE6N_  ]


### Análisis de como funciona:

***Hipotesis:*** A simple vista y explorando, creo que este ejemplo funciona con la posición del mouse. Entonces lo que noto es que si el Mouse:

<p align=center> 
<img src="https://github.com/user-attachments/assets/780adbfd-b82c-426b-9790-fcf6cbf3d2cf" width="400" height="400">
</p>

***Analizando el código:*** 

1. noto que hay varibales para el Tile count que es el grid en el que están organizados los circulos y que hay una random seed que probabemente se va a usar para aleatorizar la posición de los circulos al desordenarse.
   
```js
var tileCount = 20;
var actRandomSeed = 0;

var circleAlpha = 130;
var circleColor;

function setup() {
  createCanvas(600, 600);
  noFill();
  circleColor = color(0, 0, 0, circleAlpha);
}
```

2. Cada iteración del draw se recalcula el origen del sis de coordenadas, para que al recorrer el canvas con el ciclo el origen coincida con el origen de cada circulo al ser pintado. Entonces agarro el ancho del canvas, lo divido por el tilecount que es 20 y eso me da el ancho de cada Tile, pero necesito saber su centro entonces lo divido por 2 y ahora si puedo centrar el circulo al pintarlo.
   
   El canvas se limpia en cada iteración. La random seed usa una actRandomSeed que es random pero ni tan random, porque mientras se mantenga la misma seed, es este caso 0, las opciones de aleatoriedad van a ser las mismas.

   Se asigna el color del trazo del circulo y también su grosor, ahí se usa el input de la posición en Y del mouse, porque a medida que este valor cambia, tambien cambiará el grosor.

   Hay dos ciclos ***for*** para recorrer el canvas y pintar en cada draw, entonces las variables ***posx*** y ***posy*** son el centro de cada uno de esos circulos. Acá entra el input de la posición del mouse en X, porque se usa un random entre ***- MouseX*** hasta ***MouseX*** para aleatorizar el movimiento de los circulos, si el mouse no se mueve en X no se mueven los circulos. Luego con posx, posy, shiftx, shifty se dibuja el circulo.

```js
function draw() {
  translate(width / tileCount / 2, height / tileCount / 2);

  background(255);

  randomSeed(actRandomSeed);

  stroke(circleColor);
  strokeWeight(mouseY / 60);

  for (var gridY = 0; gridY < tileCount; gridY++) {
    for (var gridX = 0; gridX < tileCount; gridX++) {

      var posX = width / tileCount * gridX;
      var posY = height / tileCount * gridY;

      var shiftX = random(-mouseX, mouseX) / 20;
      var shiftY = random(-mouseX, mouseX) / 20;

      ellipse(posX + shiftX, posY + shiftY, mouseY / 15, mouseY / 15);
    }
  }
}
```

3.  Cuando se presiona el click izquierdo del mouse la actRandomSeed se randomiza tomando un valor aleatorio de 0 a 100k. Mientras no se de click la random seed se mantenia en 0 e iba a seguir aleatorio con lo mismo, pero si quiero que se randomice diferente entonces le doy click y asi tengo como un nuevo set de randomizaciones.
   
```js
function mousePressed() {
  actRandomSeed = random(100000);
}
```

4.  Si presiono la tecla S se toma un Screenshot del canvass y se guarda como png.
```js
function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
}
```

### Parámetro que escogí: 
circleColor, para modificarlo con el input de MouseY.

En el sketch original, el color de los circulos se mantenía. La modificación que realicé fue añadir color a los circulos, pero siendo cambiado en tiempo real gracias al input de la posición del mouse en Y. Ahora el movimiento del mouse en Y no solo va a cambiar el grosor de la stroke de los circulos, sino que el color va a ser más azul entre más arriba este el mouse y más verde entre más abajo esté el mouse.

Como circleColor recibía un R,G,B entonces tuve que transformar los valores de la posición del mouse a un valor entre (0 , 255), para ello usé ***map***. 

```js
let G = map(mouseY, 0, height, 0, 255)
```

El valor a mapear era mouseY, el valor min era 0 y el max era el height del canvas. Eso se iba a traducir a un rango que si es min era 0 y si era max es 255, (tambien se podian valores intermedios). Con el azul hice lo mismo pero viceversa y el rojo lo dejé en 0 para que se viera más el cambio entre verde y azul. 

Si el mouse estaba lo más abajo posible se veia verde (G= 255, B=0) y a medida que el mouse subiera se veia azul (G=0, B=255)

### ¿Como creo que podria servirme para el proyecto del curso?
Este experimento podría servirme porque muestra cómo los inputs (como el mouse) pueden controlar parámetros visuales, como en este caso el color. Esto es esencial en interactividad y diseño generativo. Para el proyecto del curso voy a necesitar interacciones en tiempo real y el mouse es una herramienta que permite eso sin complicarse mucho.
