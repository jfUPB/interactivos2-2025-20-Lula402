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

### Fase 2: Espíritus varados
**Emoción Buscada:** 
Vacío, desesperanza.

Caronte reprensentado como un anciano en una barca y Nerón como una de esas almas blancas que no podían cruzar el río hacia la muerte. *"fuera de la faz"*, *"pa' morir hay que vivir aún más"*, *"porque llorar la muerte si la vida duele más"*, son todos versos del coro que serán representados por esa sensación de estar muerto en vida, que la vida duele, que todavía no es tiempo de la muerte porque queda más por vivir. Esta fase se va a repetir cada coro porque me parece importante esa costancia. 

**Input:**

- El kinect seguirá trackeando la posición y movimientos de Nerón por todo el escenario. Para ello se necesitará fijarse mucho en la silueta de Nerón y ese será el input enviado.

  También con esta posición se calculará la cercanía de la barca de Caronte.

- La onda sonora seguirá siendo un input, pero esta vez para extraer el beat de la canción en vivo.


**Process:** 

- Tomando la posición de Nerón en el escenario, el aura blancusca, se va  a proyectar teniendo como referencia la silueta de Nerón, es decir, nerón actuará como un box collider y esta capa blanca se va a aderir a él.

- La posición de la barca de Caronte siempre va a estar trackeada, a medida de que esta brecha entre la posición de la barca con la posicón de Nerón disminuya, la barca de Caronte se va a alejar en el río, para simular que no lo puede alcanzar. El domo no tiene profundidad, pero esto sería visualmente simulado poniendo la barca cada vez más arriba en el río.

  Zonas más altas del domo = perspectiva falsa de profundidad
  Zonas más bajas del domo = perspectiva falsa de cercanía
  
  La trayectoria es circular, como si Caronte diera vueltas alrededor del domo sin jamás llegar a cruzarlo.

- Después de determinar los BPMS del beat, ese numero se usará para remapear el ritmo al que las estrellas cambian su Alpha. Cada beat las estrellas tendrán el alpha al 255 y entre beats bajará a masomenos 80. Parece ser que p5.js tiene una librería llamda beat.js, para captar esos beats. El remapeo se hace con la función map, donde se mapean los beats y se convierten a un valor del alpha.
  

**Output:**

- El domo entero se transforma en un río oscuro y estrellado.
- El techo es cielo con estrellas que giran lento, y más abajo, las paredes simulan agua que refleja esas estrellas.
- Una figura encapuchada (Caronte) aparece remando lentamente en círculo alrededor del domo.
- Nerón en el escenario bordeado por un aura blancusca.

> ---------------------------------------------------------------------------------------------------------------------------
### Fase 3: lienzo en "blanco"

**Emoción Buscada:**
Melancolía, creatividad.

Nerón sigue rapeando letras melancólicas, pero hay una lucesita y es que dentro de todo ese dolor es que nace su creatividad. El domo es ese cielo oscuro en el que están todos, pero se comienza a llenar de color y palabras inpredecibles cuando el público interactúa y conecta. *"Tengo un cuarto vacío lleno de reblujo"*, *"Un lienzo en blanco que mantengo allí colgado"* son versos que vienen a la vida con esa representación de grafitis, como lo es hoy en día la comuna 13.

**Input:**
- En un lugar del domo , van a haber dos estaciones interactivas . Las taciones tendrán una pantalla y un lapicito digital. En esta pantalla el público va a poder escribir una palabra y eso se tomara como un input string.

**Process:**
- El input String de cada palabra va a ser procesado para que con una fuente de grafiti sea proyectado al cielo oscuro del domo. El tamaño va a ser escogido aleatoriamente, pero con un rango definido para poder que las palabras sean legibles o que no ocupen todo el domo. El color de cada palabra va a ser randomizado.

**Output:**
- Cielo muy oscuro.
- Grafitis de palabras, cada una con un color y tamaño diferentes escritos por todo el domo.
- El domo que inició como un "lienzo en blanco", se convirtió en un espacio de expresión como las paredes de la comuna 13.
   
> ---------------------------------------------------------------------------------------------------------------------------
### Fase 4: el viaje no termina aquí.

**Emoción Buscada:**
Resiliencia, fuerza.

El arte bombea esa sangre y esa resiliencia entre tanto dolor. Por eso el arte de los grafitis y el rap de Nerón dan vida a el domo. El domo se llena de vida y Nerón y público conectan más que nunca en esta canción, por decirlo asi, es el climax de Caronte. Caronte ya no está en el río, porque se dejó en claro que Nerón y el público no están listos para cruzar el río y morir. Solo está el río y el cielo, los grafitis coloreando todo el domo y todos los presentes son esas almas que no van a pasar aún.

**Input:**

- Aun continua la interactividad del público con las estaciones interactivas con la pantalla y el lapiz.

- Como input se conserva la onda de sonido de la canción en vivo. Se extrae de acá los BPMS como en la fase 2.}

- Con el Kinect se trackeará especialmente el movimiento del brazo de Nerón, del brazo con el que no esté sosteniendo el micrófono. Se tomará como input la posición A y la posición B.

**Process:**

- Los strings de las palabras escritas por el público se siguen procesando igual que en la fase anterior.

- Después de determinar los BPMS del beat, ese numero se usará para que los grafitis "palpiten" al ritmo de la canción. Se va a remapear el valor del beat a el tamaño de la palabra grafiteada.

  Cuando marque el beat, la palabra se mostrará más grande. Cuando esté entre beats, la palabra se mostrará más pequeña. De esa manera se creará el efecto de que los grafitis palpitan al ritmo de la canción.

- La velocidad con la que nerón mueva el brazo va a tener un umbral. Se le pedirá a Nerón que porfavor mueva el brazo hacia el cielo llevando el ritmo:

  Si la velocidad, que va a representar la fuerza, con la que Nerón mueve el brazo pasa el umbral preconfigurado, entonces todos los grafitis mostrados en pantalla van a cambiar de color aleatoriamente.

  De cierta manera el resultado sería el mismo si usamos como input el beat, ya que nerón con su brazo va a llevar el beat. Pero ese es el truco de lo generativo, va a ser slightly different si el input no es el mismo.

- La posición de cada grafiti debe mantenerse actualizada, ya que hay que asegurase de que nunca toquen el agua, los grafitis solo se van a escribir en el cielo. Debido a esto, la posición del río debe actual como un collider, para que nunca lo toquen.

**Output:** 

- Cielo oscuro y río moviendose abajo al rededor del domo.
  
- Grafitisde palabras palpitantes y coloridos en el cielo.
  

> ---------------------------------------------------------------------------------------------------------------------------


**<p align=center> Nodos </p>**

En mi propuesta de Caronte, cada uno de los nodos no determina el futuro, sino que lo posibilita.

**Nodo de inicio:** la primera nota que cante Nerón activa el sistema sin que este sepa cómo será su interpretación ese día. Si canta con melancolía, la niebla será más clara y si canta con rabia, se vuelve más densa y oscura. Su frecuencia abre diferentes caminos posibles.

**Nodo túnel:** cada paso de Nerón deforma el túnel, reacciona a su movimiento, y ese instante crea opciones visuales que solo existen en ese “ahora" y dependiendo de como se mueva Nerón por el escenario. Las palabras que se van a mostrar en el domo dependiendo de cada verso, son aleatorias, como puede que en una presentación se muestre "soledad" en otra se puede ver "desamparo".

**Nodo coro:** cuando el aura blanca de Nerón se acerca al barco este se aleja. La cercanía de su cuerpo y el movimiento en vivo lo determinan. Cada estrella palpita con los BPMs de ese día.

**Nodo final:** cuando el público escribe palabras en la estación de la Fase 3 y 4, no se sabe qué va a aparecer en el cielo. “Soledad”, “mamá”, “sancocho”, “Medallo”. Cada palabra modifica el cielo de formas únicas, y cada noche ese cielo será otro.
Además de el ritmo, la fuerza y velocidad con la que Nerón mueva la mano, determinará el cambio de color de los grafitis, que puede ser diferente cada noche.

**<p align=center> Multi-linealidad y emergencia </p>**

- Nerón nunca canta igual. La saturación de la niebla, el tono emocional, el tempo, todo cambia.

- El público escribe palabras diferentes y cada presentación tiene nuevas personas (generalmente). Cada conjunto de palabras abre un cielo grafiteado y visuales distintas.

- El sistema responde a inputs físicos (posición en el escenario, intensidad, movimiento) y sonoros (frecuencia, beat, verso).


**<p align=center> Staging la apertura </p>**

No digo “esto trata sobre el duelo” o "esto trata sobre el viaje desde la vida a la muerte". Lo muestro: Nerón intenta moverse, pero el túnel lo persigue. Canta y el entorno responde. Su cuerpo es atravesado por niebla y en el coro es uno de esos espíritus. El público lanza palabras al cielo desde su propio sentir y experiencia.

No representamos “el viaje”. El sistema está diseñado para simular estar atrapado en un viaje sin fin, sin destino. El domo nunca entrega cierre. Ni muerte, ni retorno. Solo presente y como Nerón y el público viven en él.

**<p align=center> Agencia Distribuida </p>**

**Agencia Distribuida:** el control no es de uno solo. Todos ponen su granito de arena y hacen que cada presentación tenga un outcome diferente.

**Agencia Intuitiva del Artista:** Nerón no hace nada milimetricamente pensado desde antes, es su arte y concexión con el público lo que determinan el concierto. Cada movimiento, su energía, su fuerza en las palabras, el ánimo con el que canta es lo que mueve el domo.

**Agencia Co-creadora del Público:** al enviar sus palabras, se convierten en co-autores del paisaje grafiteado visual.

**Agencia Interpretativa del Visualista:** guía las transiciones y se toma el tiempo de sentir la canción y diseñar un concierto generativo para que entre el público y el artista, generen en vivo una experiencia única.


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








