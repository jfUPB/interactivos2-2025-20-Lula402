# Unidad 2

## 🔎 Fase: Set + Seek

> ACTIVIDAD 1

**Caso escogido:** John Whitney - Experiments in motion graphics 1968 - Generative graphics https://youtu.be/jIv-EcX9tUs?feature=shared

### <p align=center> INPUT </p>

### ¿Cuáles son los Inputs que crees que utiliza el sistema?

- Panel de luz, que es el que estaban controlando como con un lapicerito al inicio. En este panel cambiaban los valores de los parametros como un input.
- Las señales enviadas por el programa del computador, que son las que controlan la camara cuando la conectan.
- Otro input de cierta manera pueden ser los filtros de color que él luego le pone a la cámara para enriqucer las visuales.
- Cuando usan la cámara el computador no es controlado por el light panel, sino que es controlado por unos papeles que les llamó "punch cards", que son tarjetas perforadas con un código binario:

<p align=center>
<img width="300" height="174" alt="image" src="https://github.com/user-attachments/assets/30f19363-f7f3-4553-a770-02510df4e5f4" />
 </p>

### <p align=center> PROCESS </p>

### ¿Cómo imaginas que es el Process? Describe las reglas o la lógica que podría estar detrás.

- aprox 20 parámetros que son las letras y numeros que mostraron al inicio, todas esas variaciones se dieron cuenta que era un generador de diferentes figuras. Los parametros son mappins y rotations.
- Los valores numeros se escojen como input y se le pueden asignar a estos parametros.
- El programa previamente configurado en el computador envia señales que operan la cámara.

### <p align=center> OUTPUT </p>

### ¿Cuál es el Output final que se genera?

- Figuras en movimiento, de diferentes colores. Después de unos segundos de moverse, pasan al reposo y se vuelven a mover nuevamente.

<p align=center>
<img width="145" height="111" alt="image" src="https://github.com/user-attachments/assets/e4fc3481-58cb-495e-94ea-67277a37492e" />
</p>

- El artista deja planteado varias ideas de ponerle música al fondo. Todo esto que el hizo, lo hizo pensando en que iba a ser acompañado de música y para generar sentimientos: "it does not do that very well, but I think it will".

------------------------------------------------------------------------------------------------------------------------------

> ACTIVIDAD 2

| Prometeo  | Fase I: OPRESIÓN| Fase II: CONFLICTO  | Fase III: REVELACIÓN |
| ------------- | ------------- | ------------- | ------------- |
| **Input**  | El primer input es una onda de sonido, de la que se van a extraer características como la intensidad y el tono de la voz de Nerón. El otro input es el kinect, que trackea el movimiento del cuerpo de Nerón mientras está en el escenario. El propio Kineckt tiene sus inputs: cámara RGB, sensor de profundidad (infrarrojo) y micrófono direccional.  | Como dispositivo de input ahora tenemos el micrófono, para captar la onda de sonido de lo que rapea Nerón, además de probablemente también captar el track de Nerón para poder captar los bits. Serían entonces la señal de audio en vivo y el track. ................................................................................................ Como otro input, tenemos de nuevo el Kinect, este servirá para poderle hacer el body tracking a Nerón y saber cuando haga esos gestos bruscos. El kinect se va a encargar de ser ese input de cambios en el movimiento. | Celular, que será un cliente remoto, donde hay una interfaz y el input puntual, son esas palabras que envía al domo el público al dar click en la pantalla.  |
| **process** | Hay un sistema de partículas, entre los parámetros que tiene, están la densidad y la velocidad, esos parámetros van a ser manipulados por el input de la onda de sonido. ................................................................................................  La proyección de luz que representa el aura de Nerón inicia por lo que el kinect trackea, el kinect probablemente envíe las señales o la información que capte al sistema. El programa se encarga de basarse en eso y proyectar el aura al rededor, teniendo en cuenta el mapeado de su posición en el escenario.  | Para poder procesar los beats y los golpes de las sílabas se puede usar ***la transformada de Fourier*** (que ya lo conversamos por encimita en clase). Con ***Fourier*** se puede descomponer la señal de audio de Nerón en las diferentes ondas de sonido y asi poder obtener los picos. Al obtener esos picos en ese momento es cuando se mostrarian los ataques visuales rojos y blancos. ................................................................................................ Para las ondas de choque sonicas que van a salir de Nerón, el procesamiento sería calcular la velocidad con la que realizó el movimiento de los brazos. Entonces cuando el brazo cambie de un punto A -> B se mide con que velocidad fue y si sobrepasó el tope que se configure entonces cuenta como un golpe. ................................................................................................ Para que los fragmentos geométricos sean repelidos, debe haber un chekeo constante entre la posición de cada fragmento y la posición del aura de luz, en el momento en el que coincidan los parametros de movimiento del fragmento deben cambiarse hacia el sentido contrario para poder crear ese efecto de que fue "repelido". | El input es enviado como un paquete de datos al server el server le manda ese paquete al cliente local, que me imagino que es un pc desde donde se va a controlar la experiencia. Con Socket.io se manejan ambos clientes y el server. ................................................................................................ En el momento en el que la llama cambia, cuando cada palabra entre y coincida con la posición del aura de Nerón, lo que se podría hacer es que la palabra desaparezca al entrar en contacto, pero también subirle la saturación a la llama para hacer enfasis, esto se puede hacer con un if. ................................................................................................ Las palabras "miedo" y "soledad" se pueden gestionar con ifs, en el que se haga una comparación de que "si esa fue la palabra que entró en contacto con la llama, entonces florece o haz un árbol de luz". Me imagino que ese florecer y árbol de luz van a hacer funciones aparte y simplemente se llaman si se cumple el condicional.  |
| **output** | El domo está oscuro y los colores que se ven son desaturados. Desde la parte superior del domo caen las particulas en forma de gotas azules, no van a ser identicas entre si, van a verse diferentes dependiendo del input. Se podrá ver al rededor de Nerón un marco de luz dinámico que se va a mover con él y lo va a bordear.  | Los fragmentos geométricos rojos y blancos se ven moverse por todo el domo y rebotan cuando tocan el aura de Nerón o cuando este envia una onda sónica. El otro output es una onda, probablemente representada con arcos que sale desde la mano que Nerón movió bruscamente. | Se van a visualizar las palabras escogidas por el público, pasando por todo el domo. Se va a ver la llama de Nerón cada vez más potente y siempre moviendose con él. Se van a ver las palabras desaparecer al tocar la llama. Se va a ver un árbol blanco de luz crecer en el domo y también el florecer de alguna flor. |

### ¿Qué elemento del diseño te parece más innovador y por qué? 
### ¿Cómo crees que la experiencia del público cambiaría si uno de los inputs (por ejemplo, las palabras del público) fuera eliminado?




