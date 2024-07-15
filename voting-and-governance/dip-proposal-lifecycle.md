---
description: Visión general del ciclo de vida de la propuesta de mejora de dYdX (DIP).
---

#

## **Etapas de la propuesta**

El Proceso de gobernanza de dYdX se alimenta de los foros de gobernanza en [**https://dydx.forum/**](https://dydx.forum/) y se ratifica a través de la Propuesta de mejora de dYdX ("DIP").



El siguiente diagrama de flujo muestra las etapas iniciales propuestas para aprobar una propuesta:

![Etapas de un DIP](../.gitbook/assets/1-proposal-stage-flow-chart.png)

## 0. Discusión en los foros

Cualquier persona puede inscribirse e iniciar un hilo sobre cualquier tema en los foros de gobernanza de dYdX alojados en [**https://dydx.forum/**](https://dydx.forum/). Los miembros de la comunidad deben registrarse usando una dirección de correo electrónico o una billetera de Ethereum.

## 1. Creación de DRC (fuera de la cadena)

La creación de la **solicitud de comentarios de dYdX** (DRC) fuera de la cadena es el primer paso en el proceso de mejora de la gobernanza. Cualquier persona puede participar en el [Foro de gobernanza](https://dydx.forum/), crear DRC fuera de la cadena y discutir las mejoras.

Para crear un DRC, utiliza [esta plantilla](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) (disponible en nuestro Github). El DRC debe abarcar toda la información del potencial DIP final.

Como mínimo, los DRC deben incluir:

* Títulos cortos y concisos del DRC
* Una descripción corta y concisa de la propuesta
* La justificación del DRC, es decir, ¿por qué?
* El título del post en el foro debe incluir DRC: con el título corto del DRC. Por ejemplo, DRC: nueva solicitud de mercado
* Una encuesta de la comunidad que los miembros de la comunidad puedan usar para votar sobre mejoras fuera de la cadena

## 2. Discusión y comentarios de DRC

Una vez publicadas en el foro de gobernanza, todas las preguntas y comentarios deben ser tratados y considerados, para mejorar aún más el DRC.

## 3. Encuestas de Snapshot de DRC

Las encuestas de Snapshot sirven para dos objetivos: la señalización del sentimiento para futuros DIP y votos vinculantes en la cadena para variables controladas fuera de la cadena.

Animamos a la comunidad de dYdX a crear encuestas de Snapshot los lunes para aumentar la visibilidad durante la semana de trabajo regular.

Snapshot es una interfaz de votación simple que permite a los usuarios señalar sentimientos fuera de la cadena. Los votos en Snapshot son ponderados por la facultad de voto de la dirección utilizada para votar.

Para las encuestas de Snapshot relacionadas con la señalización del sentimiento, el proponente tendrá que proporcionar:

* detalles del DRC,
* un sistema de votación,
* un período de votación - fecha de inicio de la votación y fecha de finalización de la votación establecidas para un período de 4 días, y
* un retraso de votación - un número de bloque de Snapshot que es de 6570 bloques (aproximadamente 1 día basado en un tiempo de bloque de 13,2 segundos) en el futuro. El número de bloque de Snapshot bloquea el estado de los miembros de la comunidad que pueden votar. Los titulares de tokens que poseen tokens antes del número de bloque de Snapshot son elegibles para votar.

Para las decisiones que no requieren una llamada de contrato inteligente en cadena, en particular los cambios en las fórmulas de recompensas de proveedor de negociación y liquidez, los votos instantáneos se consideran el voto vinculante y final. El proponente deberá incluir los requisitos anteriores y proporcionar:

* Opciones de votación binarias - para claridad, una dirección vota a favor o en contra de una propuesta.

Los cambios propuestos serán implementados por dYdX Trading Inc. si los resultados de la encuesta de Snapshot satisfacen:

* El quórum mínimo contribuye a la descentralización de la toma de decisiones y protege contra la toma de decisiones unilaterales y
* el diferencial de voto mínimo - al menos el 67% de los votos deben estar a favor de la propuesta. El diferencial de voto mínimo ayuda a filtrar propuestas que son altamente contenciosas y requieren más discusiones.

dYdX Trading Inc. tendrá hasta 1 Epoch (28 días), un período de gracia de ejecución, para implementar cambios basados en una encuesta de Snapshot exitosa.

Nota que las propuestas y los votos son solo mensajes firmados, almacenados en IPFS y disponibles en el portal de la mancomunidad.

## 4. Creación de DIP (en la cadena)

Cuando se llega a un consenso aproximado, un DIP en la cadena puede ser presentado por un miembro de la comunidad que tenga suficiente poder de propuesta para el tipo de propuesta. Un DIP en la cadena se inicia mediante una llamada de contrato inteligente. La propuesta debe basarse en el resultado ganador de la votación de DIP fuera de la cadena en Snapshot y puede estar compuesto por una o varias acciones, hasta un máximo de 10 acciones por propuesta.

La creación de un DIP está sujeta a un número mínimo de tokens poseídos/delegados requeridos para una cuenta. Debe especificarse un ejecutor de bloqueo de tiempo cuando se crea una propuesta. Los parámetros iniciales son los siguientes (y pueden ser modificados por la gobernanza):

| Parámetro | Descripción | Ejecutor de bloqueo de corto tiempo | Ejecutor Merkle-pauser | Ejecutor de bloqueo de largo tiempo  | Ejecutor de Starkware |
| ------------------ | ------------------------------------------------ | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Umbral de la propuesta | Tokens mínimos poseídos/delegados para crear una propuesta | 0,5% del suministro total | 0,5% del suministro total | 2% del suministro total | 0,5% del suministro total |

## 5. Votación de DIP (en la cadena)

Después de que se crea un DIP de la cadena, la propuesta pasa a un estado `pendiente` por un período definido por el **retraso de la votación**otación, que actualmente está configurado a `6.570` bloques o aproximadamente 1 día (asumiendo 13,2 segundos por bloque). En otras palabras, las instantáneas de los usuarios se registran 1 día después de que se crea el DIP, en cuyo momento la propuesta pasa al estado `activo`.

Después del retraso de la votación, se activa el período de la votación. La duración del período de la votación depende del tipo de propuesta.

El siguiente gráfico muestra un diagrama de flujo de estado de DIP:

<figure><img src="../.gitbook/assets/Proposal Lifecycle (1).png" alt=""><figcaption></figcaption></figure>

Después de que un DIP se crea en la cadena, está sujeto a un **retraso de la votación**, el **período de la votación**, el **quorum mínimo** y un **diferencial de voto** mínimo. Los parámetros iniciales son los siguientes:

| Parámetro | Descripción | Ejecutor de bloqueo de corto tiempo | Ejecutor Merkle-pauser | Ejecutor de bloqueo de largo tiempo  | Ejecutor de Starkware |
| ----------------- | ----------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Retraso de votación | El número de bloques de Ethereum para esperar antes de la votación sobre una propuesta puede comenzar después de que se envíe una propuesta. | 6,570 bloques | 6,570 bloques | 6,570 bloques | 6,570 bloques |
| Período de votación \* | Duración del tiempo para el cual las propuestas están disponibles para ser votadas | 4 días | 2 días | 10 días | 4 días |
| Quorum mínimo | Número mínimo de votos a favor para que una propuesta de DIP sea aprobada | 2% del suministro total | 1% del suministro total | 10% del suministro total | 2% del suministro total |
| Diferencial de votos | Brecha entre a favor y en contra necesaria para que se apruebe una propuesta de DIP | 0,5% del suministro total | 0,5% del suministro total | 10% del suministro total | 0,5% del suministro total |

_\*Tiempo basado en tiempos de bloque de 13,2 segundos._

Solo el retraso de la votación puede ser modificado por la gobernanza y solo se puede cambiar a valores entre (inclusive) el retraso mínimo y máximo. El período de la votación, el quorum mínimo y el diferencial de la votación no se pueden cambiar.

## 6. Espera en la cola y ejecución de la propuesta

Después de que un DIP haya sido aprobado, cualquier dirección puede llamar al método de la cola para pasar la propuesta a la cola de bloqueo de tiempo. Un DIP solo se puede poner en la cola si ha sido aprobado.

| Parámetro | Descripción | Ejecutor de bloqueo de corto tiempo | Ejecutor Merkle-pauser | Ejecutor de bloqueo de largo tiempo  | Ejecutor de Starkware |
| ------------------------ | ------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Retraso por bloqueo de tiempo\* | Después de que una propuesta sea aprobada y puesta en la cola, el retraso antes de la propuesta es ejecutado | 2 días | 0 días | 7 días | 2-9 días |
| Período de gracia de ejecución \* | Tiempo después del cual una propuesta se vuelve ejecutable, durante el cual debe ser ejecutada. | 7 días | 7 días | 7 días | 7 días |
| Retraso de bloqueo de tiempo mínimo \* | Demora mínima antes de que se ejecute una propuesta (después de estar en la cola) | 1 día | 0 días | 5 días | 4 días |
| Retraso de bloqueo de tiempo máximo\* | Demora máxima antes de que se ejecute una propuesta (después de estar en la cola) | 7 días | 1 día | 21 días | 21 días |

_\*Tiempo basado en tiempos de bloque de 13,2 segundos._

Cuando termine el período de la votación y una propuesta ha tenido éxito, cualquiera puede llamar a la cola para comenzar la demora del bloqueo de tiempo.

Para el ejecutor de bloqueo de tiempo de prioridad de Starkware, tiene un período de prioridad de 7 días de la demora de bloqueo de tiempo de 9 días. Eso significa que después de 9 días cualquier persona puede ejecutar una propuesta, pero dentro de los días 2-9 (el período de prioridad) Starkware tiene la opción de ejecutar la propuesta.

En términos prácticos es:

* Días 0–2: Nadie puede ejecutarla
* Días 2–9: Solo Starkware puede ejecutarla
* Días 9: Cualquier persona puede ejecutarla

## 7. Cancelación de la propuesta (opcional)

En cualquier momento del ciclo de vida del DIP, el proponente puede cancelar el DIP. Cualquier persona puede cancelar una propuesta antes de que sea ejecutada si el proponente no tiene suficiente poder de propuesta en el bloque actual.

## Preguntas frecuentes

### ¿Cuál es el objetivo de la demora en la votación?

La **Demora en la votación** es el número de bloques de Ethereum que hay esperar antes de votar sobre una propuesta, que puede comenzar después de que se envíe una propuesta.



Por ahora, la **demora en la votación** está configurada en `6.570 bloques`, que es aproximadamente 1 día. Este valor se le agrega al número del bloque actual cuando se crea una propuesta.

En el futuro, la gobernanza de dYdX puede votar para aumentar o disminuir **la demora en la votación**. Si bien hay beneficios obvios para una **Demora en la votación.** Puede introducir algunos resultados adversos potenciales, como la explotación oportunista en casos extremos.

### ¿Cuál es el objetivo del umbral de la propuesta?

Si no es totalmente imposible, esa cantidad sería prohibitivamente costosa y probablemente costaría más cuando se contabilizara la fluctuación de precios que la ganancia neta del ataque.

Si algún grupo lograra de alguna manera una toma de mala fe, la demora en el bloqueo de tiempo les daría a los agentes afectados tiempo para retirar sus activos del protocolo. Eso también sería una oportunidad de bifurcar el protocolo, una ruta que probablemente tomarían los actores de buena fe que queden.

###
