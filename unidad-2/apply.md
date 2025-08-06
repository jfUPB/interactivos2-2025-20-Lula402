# Unidad 2

## 🛠 Fase: Apply


**Título del Proyecto:** Entre la vida y la muerte

**Canción seleccionada:** Caronte - Nerón Arkano
https://youtu.be/nh7VWbBrlOA?feature=shared&t=1508

**Concepto Raíz:**

Caronte no es solo un viaje a la muerte o al olvido. Es una travesía entre la vida y la muerte, la memoria y el olvido, el pasado y la dignidad presente. El espacio será una travesía sensorial donde los participantes, por medio de la canción de Nerón, cruzan simbólicamente el río con Caronte, enfrentando memorias, heridas y recuerdos. Nerón no solo rapea en Vivo en el domo, sino que convoca. El público no solo observa, cruzan con él el río y lo acompañan.

> ---------------------------------------------------------------------------------------------------------------------------

### Fase 1: emprendiendo el viaje

**Emoción Buscada:** Desarraigo, vacío y búsqueda existencial.

La ilusión visual del túnel va a estar siempre centrada detrás de Nerón, mientras que el resto del domo va a estar con niebla. A medida que Nerón canta objetos y palabras van a ir siendo tragados por este túnel. Que palabras y objetos? una lápida, la palabra "fe", "mamá", dolor, soledad, unsa sonrisa.

<img width="460" height="240" alt="image" src="https://github.com/user-attachments/assets/b41dddc8-8f80-4300-95d8-2306d3389f84" />

<img width="236" height="236" alt="image" src="https://github.com/user-attachments/assets/51c28752-90af-4833-9a5b-e3826f9ab67c" />

**Input** 

- Voz de Nerón = niebla visual.

  La onda sonora de la voz de Nerón en vivo es procesada para extraer la frecuencia con la que está cantando ese día. La       freciencia determinará la densidad y tono de la niebla de color azulado, 

  Voz más grave → niebla más densa y oscura (casi azul petróleo).

  Voz más aguda → niebla más ligera y translúcida (azul cielo oscurito).

- La onda sonora de la voz de Nerón en vivo también es procesada para extraer los versos. Los versos entrarán como input y se almacenanrán, porque estó será lo que desencadene que se muestren objetos o palabras.


- Movimientos lentos de Nerón por el escenario = deformación del túnel al rededor de él.
Un kinect va a estar ubicado trackeando a Nerón en el escenario. El kinect va a permitir obtener como input la posición constante (en vivo) de Nerón.


**Process:**

- La frecuencia de la voz se remapea (con una función map()) a valores de color y transparencia. Esta niebla se actualiza cada frame en tiempo real, dando la sensación de que la atmósfera respira con la voz de Nerón.

  Azul petróleo con alpha alto para tonos bajos.
  
  Azul claro con alpha bajo para tonos altos.
  

- Los versos serán procesados como strings, luego se va a hacer una comparación, probablemente con un ***if***, para saber si el verso corresponde con cierta palabra. Luego de que se verifique si ese es "tal" verso, este va a escoger aleatoriamente de unas opciones de palabras u objetos. Para explicarme mejor, tomaré el verso "acompañado de la soledad", después de comprobar de cual verso se trata, se va a escoger aleatoriamente con un random una posición de un array de strings que contiene palabras como: soledad, abandono, aislamiento, destierro, desamparo. Esa palabra va a ser la que se proyectará.

  Para cumplir el efecto de que el tunel se traga las palabras, a medida que la palabra se acerque más al centro del túnel, su alpha disminuirá. Esto se puede hacer en p5.js con un map, para mapear y "convertir" la posición de la palabra a su valor en alpha.

- La posición de Nerón que envíe el Kinect, va a ser usada como ancla para el origen (0,0) del túnel. El origen de Nerón siempre va a ser perseguido por el origen del túnel, de ese modo siempre se verá centrado y en movimiento detrás de él.


**Output:**
- niebla entre azul muy oscuro y azul cielo, con diferentes transparencias.
- deformación del túnel al rededor de Nerón. Este túnel siempre va a proyectar el efecto de absorver las cosas.
- Palabras que se mueven por el domo y son tragadas lentamente por el túnel.


> ---------------------------------------------------------------------------------------------------------------------------

### Fase 2: [Nombre de la fase]
**Emoción Buscada:** …

**Input:** …

**Process:** …

**Output:** …
> ---------------------------------------------------------------------------------------------------------------------------
### Fase 3: [Nombre de la fase]
**Emoción Buscada:** …

**Input:** …

**Process:** …

**Output:** …
> ---------------------------------------------------------------------------------------------------------------------------
### Fase 3: [Nombre de la fase]
**Emoción Buscada:** …

**Input:** …

**Process:** …

**Output:** …


cruzando el rio, neron es una de esas almas que se queda atrapada, por eso su aureola blancusca. Cada que 





**Nodos:** [Describe dónde y cómo ocurren los nodos en tu diseño]

**Multi-linealidad y emergencia:** [Explica cómo tu sistema genera una experiencia única cada vez]

**Staging la apertura:** [Detalla cómo escenificas la experiencia en lugar de contarla]

**Agencia Distribuida:** [Analiza cómo se distribuye la agencia entre artista, público y sistema en tu propuesta]

### <p align= center> CARONTE </p>

En la mitología griega, Caronte (Χάρων en griego) es el barquero que transporta las almas de los muertos a través del río Aqueronte, que separa el mundo de los vivos del Hades, el reino de los muertos. Era una figura sombría y desagradable, representada a menudo como un anciano, a veces con barba, que exigía un pago (un óbbolo) por sus servicios. Las almas que no podían pagar, o que no habían sido debidamente enterradas, vagaban por la orilla del río durante cien años. 

### <p align= center> EPITAFIO (No sabía que significaba) </p>

Inscripción que se pone, o se supone puesta, sobre un sepulcro o en la lápida o lámina colocada junto al enterramiento.

### <p align= center> LETRA </p>

Dejé la fe en un compraventa y quise

tomar atajos hacia el final del planeta, hoy La sonrisa es lo que más me acompleja pues ya viajo a la nada con el

epitafio de mi vieja. Quise contar al infinito pero, acompañado de la soledad

si descanso me limito pero si sigo adelante me limita mi realidad. El dolor es exquisito, la

tristeza suele darme placer yo ya no sé qué necesito, pero de ese algo tengo sed

voy a la nada con nadie sin todo, voy por todo con nada sin nadie, voy a la nada

con nadie sin todo, voy por todo Sin un peso y fuera de la faz

para morir hay que vivir aún más Solamente quiero hacerme el fuerte

porque llorar la muerte si la vida duele más, sin un peso y fuera de la faz para

morir hay que vivir aún más Solamente quiero hacerme el fuerte porque llorar la

muerte si la vida duele más. No hay salida al Laberinto, no hay escape de este

Laberinto si la musa me cobija con su grito y es la progenitora de las frases

que yo cito, adicto, a mirar la luna, a llena derramarme con mis venas, a no esperar

noches buenas despreciando las faenas pa' no soñar con sirenas con las manos vacías pero con el alma llena y nena no

tengo un auto de lujo tengo un cuarto vacío acompañado de reblujo un Lienzo en

blanco que mantengo allí colgado no tengo fortuna y eso me hace afortunado, voy a la nada con nadie sin todo voy por

todo con nada sin nadie voy a la nada con nadie sin todo voy por

todo. Sin un peso y fuera de la faz para morir hay que vivir aún más Solamente

quiero hacerme el fuerte porque que llorar la muerte si la vida duele más, sin un peso y fuera de la Paz para morir

hay que vivir aún más Solamente quiero hacerme el fuerte porque llorar la muerte si la vida duele más voy a la nada

con nadie sin todo voy por todo con nada sin nadie voy a la nada con nadie sin

todo voy por todo voy por todo voy a la nada con nadie sin todo voy por todo con

nada sin nadie voy a la nada con nadie sin todo voy por todo yo voy por todo. Sin 

un peso y fuera de la faz pa' morir hay que vivir aún más, Solamente quiero

hacerme el fuerte porque llorar la muerte si la vida duele más sin un peso

y fuera de La Paz pa' morir hay que vivir aún más Solamente quiero hacerme el

fuerte porque llorar la fuerte si la vida duele más si la vida duele más

si la vida duele más Solamente quiero hacerme el fuerte si la vida duele más

si la vida duele más si la vida duele más

voy por todo yo voy por todo




