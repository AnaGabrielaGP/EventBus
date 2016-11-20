# EventBus
Biblioteca EventBus

##**Tarea:** Investigar la biblioteca EventBus y como esta nos ayuda a comunicarnos dentro de nuestra aplicación
___

EventBus es es una herramienta que nos permite lanzar y capturar eventos entre diferentes clases. Está basada en el patrón bus de eventos y su implementación consiste en que uno o varios objetos se suscriben a un canal a través del cual escuchan, y otro, en el momento en el que suceda algo que desea notificar, lanza un evento a través de este canal y todos aquellos que estaban escuchando reaccionarán haciendo aquello que tenían programado al suscribirse a éste. EventBus no solo nos facilita la tarea de notificar a los suscriptores acerca del evento si no que nos permite enviar información asociada a ese evento a través del canal y decidir en qué hilo se ejecutará la respuesta.

Un bus de eventos es una herramienta muy útil y potente, pero el abuso de esta forma de trabajar y las malas prácticas al hacer uso de esta herramienta puede ser contraproducente en ciertas ocasiones:

* _Flexibilidad:_ Con EventBus se puede generar toda una forma de trabajar basada en estos eventos. Sin embargo, esto puede ser contraproducente, ya que te permite abstraer de las herramientas de paso de mensajes y de notificaciones que brinda Android y el lenguaje en general.
* _Simplicidad:_ Es una ventaja clara que nos brinda en este caso como herramienta, ya que en solo tres pasos podemos hacer uso de esta herramienta. En cualquier parte se llama al método post de la instancia de EventBus y se propaga un evento. En cualquier parte de la app nos suscribimos en el momento que deseemos y, generando un método con una simple anotación, reaccionamos a dicho evento especificando en qué hilo se da la respuesta.
* _Agilidad:_ Ahorramos muchas líneas de código, clases y lógica de interacción que se traduce en un menor tiempo de desarrollo. Pero haciendo hincapié en lo anterior, lo que parece ahorrarnos trabajo de desarrollo, si no se hace correctamente y se abusa de ello, se puede convertir en tiempo de depuración.

Se muestran los errores más frecuentes al usar EventBus:

* Un bus de eventos no es un canal de comunicación, sino una forma de notificar eventos entre los suscriptores y los generadores.
* Un error muy común es el de estar suscrito a muchos eventos y controlar qué evento es el que se está recibiendo en función de la información que se nos envía. Los datos asociados al evento contienen información complementaria a este, y no para distinguirlo de otro.
* El lanzamiento incontrolado de eventos es algo muy común, hay que elegir bien cuáles se lanzan y dónde, y no llenar nuestra aplicación de suscripciones.
* Hay que tener cuidado, no tanto de en qué hilo se lanzan los eventos, sino en el de la respuesta.
