---
description: >-
  Una descripción general paso a paso del proceso de gobernanza Creación de DRC, de creación de encuestas de Snapshot, creación de DIP, votación en una encuesta de Snapshot, votación en una DIP, puesta en cola de una DIP y ejecución de una DIP.
---

# Guía de gobernanza

La Fundación dYdX creó esta guía para ayudar a la comunidad de dYdX a comprender el proceso de gobernanza de dYdX. La guía proporciona un resumen general paso a paso de:

* [Discusiones en los foros (fuera de la cadena)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Creación de DRC (fuera de la cadena)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Creación de encuestas de capturas (fuera de la cadena)](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [Votar en una encuesta de capturas](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [Creación de DIP (fuera de la cadena)](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [Creación de DIP (en cadena)](governance-guide.md#step-1-on-chain-dip-drafting)
* [Votar por un DIP (en cadena)](governance-guide.md#how-to-vote-on-a-dip)
* [Poner en cola un DIP (en cadena)](governance-guide.md#how-to-queue-a-proposal)
* [Ejecutar un DIP (en cadena)](governance-guide.md#how-to-execute-a-proposal)

Los dos ejemplos presentados en la guía son _DIP 2 (propuesta fuera de la cadena) - Umbral de recompensas de proveedores de liquidez y_ _DIP 3 (propuesta en cadena) - Restauración de módulos de seguridad_.

## DIP 2 (propuesta fuera de la cadena) - Umbral de recompensas de proveedores de liquidez

_**Resumen:**_

En la etapa 6, la comunidad de dYdX votó en [Snapshot](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43) para reducir el umbral de volumen de recompensas de LP para los creadores de mercado del 1 % al 0,25 %. La reducción del umbral de recompensas de LP del 5% al 1% en la etapa 2 siguió el mismo proceso que la reducción en la etapa 6 (1% a 0.25%). El resumen paso a paso para reducir el umbral de volumen de recompensas de LP del 5 % al 1% está incluido a continuación.

La mayoría de la comunidad (399 votantes y 86 % de DYDX) votaron en [Snapshot](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN) para reducir el umbral de volumen para obtener recompensas de proveedores de liquidez del 5 % al 1 %. Un [DIP fuera de la cadena](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md) para reducir el umbral de volumen de recompensas de proveedores de liquidez para los creadores de mercado del 5 % al 1 %. Jacob Goh (jteam0x) en DeFiance Capital. Los creadores de mercado que cumplieron el umbral del 1 % en la etapa 2 fueron elegibles para ganar recompensas de proveedores de liquidez en la etapa 3. La propuesta no requería ningún cambio de contrato inteligente en cadena.

_**Antecedentes:**_

Como parte del [programa de recompensas](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards) de proveedores de liquidez, 1,150,685 DYDX se distribuyen  por etapa (28 días) a proveedores de liquidez que comercializan para el protocolo. Las recompensas se distribuyen según una fórmula que recompensa una combinación de tiempo de actividad, profundidad bilateral, diferenciales de oferta y demanda y la cantidad de mercados admitidos. Para ser elegible para este programa de recompensas, los proveedores de liquidez deben proporcionar un porcentaje mínimo del volumen total de creadores durante la etapa anterior.

La comunidad de dYdX tiene "control inmediato e irrevocable sobre" el umbral de recompensas de proveedor de liquidez. La lista completa de parámetros que los controles de la comunidad están enlazados [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

La comunidad fue motivada a reducir el umbral de recompensas de proveedor de liquidez para incentivar a los nuevos creadores de mercado y a los creadores de mercado pequeños y medianos a aumentar la liquidez en la plataforma dYdX. Además, aumentar el número de creadores de mercado en la plataforma ayuda al protocolo dYdX a ser más descentralizado.

A continuación, proporcionamos una descripción general paso a paso de cómo funciona la gobernanza de dYdX en la práctica. Más información sobre el proceso de gobernanza de dYdX está vinculado [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

### **PASO 1 - Discusiones en los foros y creación de DRC (fuera de la cadena) y comentarios de DRC**

_**Descripción:**_

El proceso de gobernanza de dYdX está impulsado por [foros de gobernanza](https://dydx.forum/). Los miembros de la comunidad publican y comentan sobre los hilos de discusión para llegar a un consenso aproximado fuera de la cadena. Más información sobre las discusiones en foros y la creación de DRC está vinculada [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle). \
\
Nota: El subDAO de operaciones ha lanzado [**https://dydx.forum/**](https://dydx.forum/) como el nuevo foro con la [votación de la comunidad para hacer la transición de Commonwealth a Discourse](https://snapshot.org/#/dydxgov.eth/proposal/0xa5e77732dd24edd26bd41b089969b3662c29eb41c3bacd35cb2931ca55882a8f). Algunas referencias en esta guía a discusiones anteriores de la DRC seguirán apuntando a Commonwealth, pero cualquier nueva discusión debe suceder en el foro de [**Discurso**](https://dydx.forum/) recientemente lanzado. \


_**Aplicación para DIP 2:**_

Su Zhu (zhusu) de Three Arrows Capital creó una [discusión en los foros fuera de la cadena](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/) para reducir el umbral de recompensas de proveedores de liquidez. Varios miembros de la comunidad, como Evgeny de Wintermute, Ben de Kronos, Josh de Sixtant y muchos más, participaron en la discusión y ofrecieron comentarios valiosos.

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives.png)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives-2.png)

#### _Cómo publicar y comentar en Discourse:_

* Regístrate en Discourse con tu cuenta de correo electrónico y únete a la comunidad de dYdX [aquí](https://dydx.forum/).

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 10.59.27 AM.png" alt=""><figcaption></figcaption></figure>

* Selecciona un hilo, desplázate por los comentarios y dale a me gusta o responde a los comentarios.
* Crea un nuevo hilo de discusión o publica un DRC al hacer clic en "**Nuevo tema**" y seleccionar la categoría de temas.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.03.33 AM.png" alt=""><figcaption></figcaption></figure>

* Si estás creando un DRC, por favor sigue la plantilla vinculada [aquí](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md). Como se describe en la creación de _DRC_ en el [ciclo de vida de la propuesta](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle), los DRC, como mínimo, deben incluir lo siguiente:
  * Un título corto y conciso del DRC.
  * Una descripción corta y concisa de la propuesta.
  * El motivo de la justificación para el DRC (por ejemplo, ¿por qué?).
  * El título del post del foro debe incluir DRC: \[insertar el título corto del DRC] (por ejemplo: Nueva solicitud de mercado).
  * Una encuesta comunitaria que los miembros de la comunidad pueden utilizar para votar sobre mejoras fuera de la cadena.

### **PASO 2 - Encuesta de capturas de DRC (fuera de la cadena)**

_**Descripción:**_

Después de que la comunidad llegue a un consenso aproximado, un miembro de la comunidad con 10K de poder de proponer puede crear un voto fuera de la cadena para el DRC en [Snapshot](https://snapshot.org/#/). [El poder](https://docs.dydx.community/dydx-governance/voting-and-governance/voting) de proponer da acceso a la creación y el mantenimiento de una propuesta. Snapshot es una interfaz de votación simple que permite a los usuarios señalar sentimientos fuera de la cadena. Los votos en Snapshot se calculan por el número de DYDX en poder o delegados a la dirección utilizada para votar. El miembro de la comunidad que crea la encuesta en Snapshot debe proporcionar detalles sobre el DRC, un sistema de votación, la fecha de inicio de la votación, la fecha de finalización de la votación y el número de bloque de Snapshot. El período de votación debe ser de 5 días y la votación debe comenzar después de un retraso de la votación de 1 día ( _basado en tiempos de bloque de 13,2 segundos)_. La demora en la votación brinda tiempo para que los miembros de la comunidad de dYdX aprendan más sobre DRC, compren DYDX o deleguen el poder de voto de sus DYDX. Los miembros de la comunidad que posean DYDX o que han sido delegados con poder de votación antes de que el número de bloque de Snapshot sean elegibles para votar. Más información sobre la encuesta de Snapshot está enlazada [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

_**Aplicación para DIP 2:**_

Los miembros de la comunidad proporcionaron comentarios sobre el post de Su Zhu. Los siguientes umbrales de recompensas fueron sugeridos por la comunidad:

* [0,5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Su Zhu de Three Arrows Capital,
* [1 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) - Sam de BitTrading,
* [2,5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Ben de Kronos / WOO Network, y
* [5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - Evgeny de Wintermute.

A continuación, Su Zhu creó una encuesta de Snapshot con las siguientes opciones:

* Umbral inferior de MM al 1 %
* Umbral inferior de MM al 2,5 %
* Mantén el umbral de MM al 5 %

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-create-snapshot.png)

#### _Cómo votar en una encuesta de Snapshot:_

* Regístrate en Snapshot con tu billetera de Ethereum y sigue las propuestas de dYdX [aquí](https://snapshot.org/#/dydxgov.eth).

![https://snapshot.org/#/dydxgov.eth](../.gitbook/assets/2-register-snapshot.png)

* Para votar en encuestas activas en Snapshot, debe tener DYDX o contar con el poder de voto delegado en su dirección antes del número de bloque de Snapshot cuando la encuesta de Snapshot se encuentre activa.
* Para votar, haz clic en la propuesta y selecciona “Sí” o “No” seguido de “Votar”.

#### _Cómo crear una encuesta en Snapshot:_

* Para crear una encuesta de Snapshot, deberás **tener un mínimo de 10 000 DYDX o tener el poder de proponer delegado a la dirección que estás utilizando** para crear la propuesta.
* La propuesta de Snapshot puede consistir en una o varias acciones, hasta un máximo de 10 acciones por propuesta. Las acciones son cambios especificados en una propuesta.
* Si cumples con el requisito mínimo de poder de propuesta de 10 000, selecciona "**Nueva propuesta**" y completa los campos abiertos según los requisitos de contenido a continuación.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.08.42 AM.png" alt=""><figcaption><p>Página de instantáneas de dYdX - Botón de "Crear nueva propuesta"</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.09.33 AM.png" alt=""><figcaption><p>Incluye detalles de la instantánea aquí y asegúrate de incluir un enlace a la DRC.</p></figcaption></figure>

Requisitos de contenido de la encuesta de DRC:

* detalles del DRC con un enlace al debate del foro,
* un sistema de votación,
* la fecha de inicio de la votación y la fecha de finalización de la votación se establecen en 4 días de duración total (_basado en tiempos de bloque de 13,2 segundos)_, y
* la encuesta de Snapshot se publica 1 día (\~6570 bloques) antes de que comience la votación.

Requisito para las encuestas de Snapshot vinculantes:

Para la mayoría de las decisiones, una encuesta instantánea actúa como una señal, mientras que se requiere un voto en cadena para obtener un resultado vinculante que cambie los contratos inteligentes. Para las decisiones que no requieren una llamada de contrato inteligente en cadena, en particular los cambios en las fórmulas de recompensas de proveedor de negociación y liquidez, los votos instantáneos se consideran el voto vinculante y final. Además de los requisitos de contenido anteriores, las encuestas de Snapshot que vinculan votos para variables controladas fuera de la cadena deben incluir:

* Opciones de votación binarias. Aclaración, una dirección es votar por o en contra de una propuesta.

![](../.gitbook/assets/2-snapshot-binary-voting.png)

* Después de la votación, la información relacionada se almacenará en IPFS y se generará un informe que estará disponible automáticamente para descargar.

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-snapshot-ipfs.png)

### **PASO 3 - Creación de DIP (Propuesta fuera de la cadena)**

_**Descripción**:_

Se debe crear un DIP cuando (1) una encuesta de Snapshot da como resultado la actualización de un parámetro fuera de la cadena (como modificaciones a las fórmulas de recompensas de operaciones o recompensas de LP) y (2) cuando un miembro de la comunidad desea enviar una propuesta para modificar Contratos inteligentes dentro de la cadena. Para los votos que no requieren actualizaciones de contratos inteligentes en la cadena, el resultado de la encuesta Snapshot debe formalizarse en un DIP fuera de la cadena y enviarse a través de una solicitud de extracción a la rama DIP pendiente del Github de la Fundación dYdX. El DIP debe reflejar el resultado ganador de la Snapshot. El DIP debe especificar la información incluida en la plantilla vinculada [aquí](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md).

_**Aplicación para DIP 2:**_

En este caso, el [DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md) fue creado por @Jteamdc.

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](../.gitbook/assets/2-dip-example.png)

Cuando el borrador de propuesta para DIP 2 se completó, @Jteamdc creó una solicitud de [retirada](https://github.com/dydxfoundation/dip/pull/8) de la rama trabajo contra la rama de DIP pendientes de la fundación dYdX. Después de que la Fundación dYdX revisara la propuesta y la aprobara, los cambios de los DIP pendientes se fusionaron a la rama maestra.

![https://github.com/dydxfoundation/dip/pulls](../.gitbook/assets/2-dip-pending-merge.png)

Dado que reducir el umbral de recompensas de proveedor de liquidez no requiere ningún cambio de contrato inteligente en la cadena, el proceso ahora está completo y los cambios serán efectivos durante la próxima etapa.

#### _Cómo crear un DIP:_

* El DIP debe estar basado en el resultado ganador de la votación DIP fuera de la cadena en Snapshot y puede constar de una o varias acciones, hasta un máximo de 10 acciones por propuesta. Las acciones son cambios especificados en una propuesta. Se puede encontrar más información en [Creación de DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution).
* Regístrate para una obtener una cuenta de Github: [https://github.com/signup](https://github.com/signup).
* Dirígete a la página del repositorio de dYdX vinculada [aquí](https://github.com/dydxfoundation/dip) y bifurca el repositorio en tu cuenta de Github.

![https://github.com/dydxfoundation/dip](../.gitbook/assets/2-dip-create-1.png)

* En el repositorio de bifurcación de DIP, ve al directorio que contiene el contenido de los DIP: [https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips).

![](../.gitbook/assets/2-dip-create-2.png)

* Selecciona la carpeta de dips: [https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content).

![](../.gitbook/assets/2-dip-create-3.png)

La carpeta de dips incluye un directorio de propuestas anteriores que siguen la plantilla de DIP vinculada [aquí.](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)

![https://github.com/dydxfoundation/dip/tree/master/content/dips](../.gitbook/assets/2-dip-create-4.png)

* Antes de comenzar a redactar una propuesta, asegúrate de que la rama que bifurcaste esté actualizada con la última versión de la rama principal. Si estás utilizando una versión antigua del repositorio de DIP, confirma que tu versión de bifurcación está actualizada con los últimos cambios. Para obtener ayuda para cambiar la base de tu versión bifurcada, puedes seguir los pasos aquí: [https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master).
* Edita la [plantilla de DIP](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) con la información de tu propuesta. Si no has bifurcado el repositorio DIP, al seleccionar el icono de edición bifurcarás automáticamente el repositorio maestro ya que no eres administrador.

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](../.gitbook/assets/2-dip-create-5.png)

* Sigue la [plantilla](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) y añade tu DIP a tu bifurcación del repositorio en el directorio `de contenido/dips/`. Sigue las convenciones de nomenclatura de estados DIP que se incluyen a continuación.

![](../.gitbook/assets/2-dip-create-6.png)

Estados de DIP:

* WIP - un DIP que aún se está desarrollando.
* Propuesto - un DIP que está listo para ser propuesto en la cadena.
* Aprobado - un DIP que ha sido aceptado para su implementación por la comunidad de dYdX.
* Implementado - un DIP que ha sido enviado a la red principal.
* Rechazado - un DIP que ha sido rechazado.
* Después de verificar que todo el contenido sea correcto, crea una solicitud de extracción desde tu rama de trabajo contra la rama DIP pendiente de la Fundación dYdX. Por favor **no** envíes esta solicitud de tirón contra la rama principal de la Fundación dYdX porque el trabajo de IPFS fallará si cualquier parte externa quiere fusionarse con la rama principal. Utilice la solicitud de extracción vinculada [aquí](https://github.com/dydxfoundation/dip/pull/8) como ejemplo.

![](../.gitbook/assets/2-dip-status-1.png)

* Después de la revisión, la Fundación dYdX fusionará los cambios de la rama de DIPs pendientes a la rama Maestro.

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/2-dip-status-2.png)

* Antes de **la fusión,** un trabajo se ejecutará automáticamente para cargar el DIP a IPFS. Puedes verificar la carga de DIP a IPFS aquí: [https://github.com/dydxfoundation/dip/pull/9/checks](https://github.com/dydxfoundation/dip/pull/9/checks).
* El DIP se agrega bajo [**`dip`**](https://github.com/dydxfoundation/dip)`/`[`contenido`](https://github.com/dydxfoundation/dip/tree/master/content)/**`dips`**`/```.

![](../.gitbook/assets/2-dip-status-3.png)

Dado que la propuesta no requiere ningún cambio de contrato inteligente en la cadena, el proceso está completo y los cambios se harán efectivos durante la próxima etapa

## DIP 3 (Propuesta de cadena) - Restauración de módulos de seguridad

_**Resumen:**_

El 1 de noviembre, Dan Robinson de Paradigm creó un [DIP](https://dydx.community/dashboard/proposal/3) en la cadena para restaurar la funcionalidad del grupo de participación del módulo de seguridad. La mayoría de la comunidad (251 votantes y casi 142M DYDX) votaron a favor de restaurar la funcionalidad del módulo de seguridad. Después de un período de votación de 10 días, un miembro de la comunidad tardó casi 3 días en llamar a la cola y pasar la propuesta a la demora de 7 días. El 20 de noviembre, el módulo de seguridad fue restaurado y restablecido a un estado limpio.

_**Antecedentes:**_

El módulo de seguridad dYdX es un contrato de participación diseñado para iniciar un grupo descentralizado de fondos que se pueden utilizar para respaldar el protocolo dYdX. Los usuarios participan DYDX en el grupo de seguridad y reciben stkDYDX (1:1). stkDYDX es una posición tokenizada transferida como ERC-20 que tiene los mismos derechos de voto y propuesta que DYDX. En el caso de un evento de déficit, se requiere un voto de gobernanza para reducir drásticamente el DYDX apostado y mitigar las pérdidas. Del suministro de tokens de DYDX, el 2,5 % (25 000 000 DYDX) del suministro de tokens se distribuirá a los usuarios que inviertan en DYDX en el grupo de participación de seguridad. Más información sobre la reserva de seguridad se puede encontrar [aquí](https://dydx.foundation/blog/en/safety-staking).

Como parte de las [recompensas del fondo de participación de seguridad](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool), se distribuirán 383 562 DYDX por etapa (28 días) a los interesados. Las recompensas se distribuyen proporcionalmente cada segundo a los interesados.

La comunidad de dYdX tiene "control inmediato e irrevocable sobre" los parámetros del contrato inteligente de módulo de seguridad. La lista completa de parámetros que los controles de la comunidad están enlazados [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

El 8 de septiembre a las 15:00 UTC, la restricción de transferencia de tokens de DYDX fue levantada y se abrió efectivamente la participación al módulo de seguridad de dYdX. Más de 50 direcciones diferentes apostaron aproximadamente 157K DYDX en el transcurso de casi 1 hora. Un virus provocó un error en el proceso de implementación y no se emitió ningún stkDYDX a las direcciones que apostaron en el módulo de seguridad. Como resultado, los fondos de cada participante quedaron varados en el contrato y el equipo de dYdX desactivó la participación en la interfaz de usuario de gobernanza de dYdX.

[DIP 1](https://dydx.community/dashboard/proposal/0) propuso restaurar la funcionalidad del Módulo de seguridad y permitir que las direcciones afectadas recuperen sus fondos y reciban un 10% adicional de sus tokens apostados como compensación. Si bien el sentimiento de la comunidad estaba fuertemente a favor de [DIP 1 - Restauración del módulo de seguridad y recuperación de participantes](https://dydx.community/dashboard/proposal/0), la propuesta fracasó porque no cumplía con el quórum mínimo requerido de 100 millones de DYDX para un voto de bloqueo de largo plazo para que se apruebe. Como resultado, Jacob Goh (jteam0x) de DeFiance Capital creó [DIP 4 - Módulo de seguridad de reembolsos y compensación de participantes](https://dydx.community/dashboard/proposal/2) para reembolsar y compensar a las direcciones afectadas por sus recompensas perdidas y por los inconvenientes causados. [DIP 4](https://dydx.community/dashboard/proposal/2) involucró implementar el contrato de recuperación para los tokens apostados de los usuarios y compensar a las direcciones afectadas con un 10% adicional de Tesorería de Recompensas. El DIP se rige por parámetros de gobernanza menos estrictos de un bloqueo de corto tiempo.

El ciclo de vida de la propuesta de un DIP generalmente es consistente hasta la creación del DIP. La diferencia principal entre DIP 3 (en la cadena) y DIP 2 (fuera de la cadena) era que DIP 3 requería votación en cadena e implementación de contratos inteligentes. Dado que el proceso para las discusiones en el foro, la creación de DRC y la creación de borradores de DIP son los mismos, comenzamos nuestra discusión paso a paso con los requisitos de contenido para redactar DIP en la cadena. Para más información por favor siga los enlaces a continuación:

* Proceso de gobernanza de dYdX - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
* Informe de incidentes de módulo de seguridad - [https://dydx.foundation/blog/en/outage-1](https://dydx.foundation/blog/en/outage-1).
* Discusión fuera de la cadena  **-** [https://commonwealth.im/dydx/propuesta/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause).
* DRC fuera de la cadena **-** [https://commonwealth.im/dydx/propuesta/discussion/1770-drc-incident-report-of-the-safety-module-outage-propropuesta-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* Encuesta de Snapshot de DRC fuera de la cadena **-** [https://snapshot.org/#/dydxgov.eth/propuesta/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* DIP propuesto en Github **-** [https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **PASO 1 - Creación de DIP en la cadena**

_**Descripción:**_

La creación de un DIP en la cadena que afecte el consenso de gobernanza sobre el protocolo dYdX debe describir los pasos específicos para implementar cambios en los contratos inteligentes. Después de que la comunidad logre un consenso aproximado de Snapshot o un DIP fallido con anterioridad, un miembro de la comunidad con suficiente poder de propuesta puede enviar el nuevo DIP en la cadena. Más información sobre el umbral de poder de propuesta, el ejecutor de bloqueo de tiempo y otros parámetros de gobernanza están vinculados [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)

_**Aplicación para DIP 3:**_

En este caso, el [DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md) fue creado por Dan Robinson de Paradigm. Dado que la propuesta incluía cambios en los contratos inteligentes en la cadena, la propuesta incluía un enlace a las implementaciones específicas de contratos inteligentes.

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/2-dip3-example-1.png)

Navegar desde el contrato de implementación de SafetyModuleV2.sol hasta la carpeta de seguridad muestra el README que contiene los detalles específicos de cómo se implementará la propuesta.

![](../.gitbook/assets/2-dip3-example-1a.png)

Los pasos para implementar la propuesta incluida en el README están enlazados aquí: [https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety).

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-2.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-3.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-4.png)

#### _Cómo redactar un DIP en la cadena (WIP):_

* Crea una nueva billetera para crear el DIP. El proceso de implementación requerirá que ingreses tu frase inicial como una variable de entorno, por lo que te recomendamos que uses una billetera única para la creación de DIP en la cadena.
* Delega el poder de proponer a la billetera única para la creación de DIP. Puedes delegar el poder de proponer [aquí.](https://dydx.community/dashboard) Los diferentes umbrales de poder de propuesta están incluidos a continuación y están vinculados [aquí](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).
  * Bloqueo de corto tiempo: 0,5% de la oferta total (5M en potencia propuesta).
  * Ejecutor de Starkware: 0,5 % del suministro total (5M en potencia de propuesta)
  * Ejecutor de largo tiempo: 2,0 % del suministro total (20M en el poder de propuesta)
  * Ejecutor de bloqueo de tiempo Merkle-Pauser: 0,5 % del suministro total (5M en el poder de propuesta)
* Crea una clave de Alchemy. Con la clave de Alchemy, no es necesario ejecutar un nodo de Ethereum para interactuar con Ethereum e implementar el contrato inteligente. La guía para crear una clave de Alchemy está vinculada [aquí](https://docs.alchemy.com/alchemy/introduction/getting-started).

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-1.png)

Selecciona Ethereum y “Empezar”.

![](../.gitbook/assets/2-draft-dip-example-2.png)

Completa la información requerida, selecciona la Red de Goerli y selecciona “crear aplicación”.

<figure><img src="../.gitbook/assets/2-draft-dip-example-3.png" alt=""><figcaption></figcaption></figure>

Después de crear tu cuenta, sigue las instrucciones de configuración vinculadas [aquí](https://docs.alchemy.com/alchemy/introduction/getting-started).

En "4. Comenzar a construir,” selecciona “Intentar implementar tu primer contrato inteligente” y sigue la guía.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-4.png)

* Abre la línea de comandos de Windows, la aplicación de terminal predeterminada o descarga iTerm: [https://iterm2.com/](https://iterm2.com/).
* Descarga e instala Node.js y npm si aun no lo tienes: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Hardhat es una herramienta de desarrollo para compilar y probar el software de Ethereum. Instala Hardhat si no lo has hecho aún: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Redacta tu(s) implementación(es) de propuesta(s) de contrato inteligente.
* El hash de IPFS se genera automáticamente y se puede obtener [aquí](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips). El hash de IPFS estará en el directorio de la Fundación dYdX bajo el nombre de archivo `DIP-[New DIP #]-ipfs-hashes.json`.

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](../.gitbook/assets/2-draft-dip-example-5.png)

* Después de seleccionar el nuevo archivo (`DIP-[New DIP #]-ipfs-hashes.jso`), asegúrate de que usas el Hash codificado.

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](../.gitbook/assets/2-draft-dip-example-6.png)

### **PASO 2 - Envía un DIP en la cadena**

_**Descripción:**_

Después de que un miembro de la comunidad haya confirmado que la(s) implementación(es) del contrato inteligente propuesta(s) es(n) correcta(s) y el DIP esté finalizado, el DIP se puede enviar en la cadena. Cuando se crea un DIP en la cadena, la propuesta ingresa a un estado "Pendiente" para la Demora de votación que dura aproximadamente 1 día (aproximadamente 6570 bloques). Las Snapshots de los usuarios se registran después de la Demora de votación para dar cuenta de las participaciones de DYDX y el poder de voto delegado. Luego, la propuesta ingresa a un estado "Activo" y la duración de la votación varía de 2 a 10 días según el tipo de propuesta. Para que una propuesta sea implementada, la votación debe pasar el quórum mínimo y el diferencial mínimo de votos, el cual cambia según el tipo de propuesta. Si el DIP satisface el quórum mínimo, la diferencia mínima de votos y la mayoría de los miembros de la comunidad votan a favor del DIP, cualquier dirección puede llamar a la cola para pasar la propuesta a la cola de bloqueo de tiempo. Los contratos de bloqueo de tiempo pueden poner en cola, cancelar o ejecutar transacciones votadas por la comunidad de dYdX. La duración de la cola de bloqueo de tiempo varía en función del tipo de propuesta.

_**Aplicación para DIP 3:**_

El equipo de Paradigm finalizó el código de solidez de `SafetyModuleV2.sol.`

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/2-draft-dip-example-7.png)

El equipo de Paradigm simuló las actualizaciones en un entorno de red principal local y bifurcación. Luego se ejecutó el conjunto de pruebas para garantizar la restauración de la funcionalidad completa, luego de la ejecución de la propuesta de gobernanza en la red principal.

El equipo de Paradigm implementó las actualizaciones de contratos inteligentes ejecutando los siguientes scripts.

**Implementación de recuperación de módulo de seguridad**

`exportar ALCHEMY_KEY=<... >`

`exportar MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-recovery`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**Propuesta de gobernanza: módulo de seguridad Fix**

`exportar ALCHEMY_KEY=<... >`

`exportar MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\
`--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\
`--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\
`--safety-module-new-impl-address 0x...`

**Propuesta de gobernanza: Compensación de módulo de seguridad**

`exportar ALCHEMY_KEY=<... >`

`exportar MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\ `--proposal-ipfs-hash-hex 0x...`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\
`--safety-module-recovery-address 0x...`

El DIP fue publicado simultáneamente en [https://dydx.community/dashboard](https://dydx.community/dashboard).

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-8.png)

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-9.png)

El contrato de Gobernanza de dYdX es 0x7e9b1672616ff6d6629ef2879419aae79a9018d2: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).

La implementación de DIP se puede confirmar en Etherscan: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

El DIP fue creado el 1 de noviembre de 2021, en el bloque 13532376. Para 6570 bloques en el futuro, el estado del DIP es “Pendiente”.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-10.png)

Los titulares de DYDX pudieron votar el DIP cuando pasó a un estado “activo” en el bloque 13538946.

La primera votación se emitió el 2 de noviembre de 2021, a las 5:51:22 PM UTC (bloque 13538959), a 6583 bloques desde la creación del DIP en la cadena.

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/2-draft-dip-example-11.png)

Después del período de votación de 10 días relacionado con un bloqueo de tiempo prolongado, cualquier miembro de la comunidad puede llamar a la cola y pasar la propuesta a la demora de bloqueo de tiempo de 7 días. Para DIP 3, un miembro de la comunidad tardó casi 3 días en llamar a la cola.

![https://etherscan.io/tx/0x3402372aa549d2270a6b5d4f84884ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/2-draft-dip-example-12.png)

Después de la demora de bloqueo de tiempo de 7 días, el DIP se ejecutó en la cadena.

![https://etherscan.io/tx/0xfd3332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/2-draft-dip-example-13.png)

En el momento en el que el DIP se ejecutó en la cadena el estado de DIP en [https://dydx.community/dashboard/propuesta/3](https://dydx.community/dashboard/proposal/3) se actualizó a “Ejecutado.”

![](../.gitbook/assets/2-draft-dip-example-14.png)

Ten en cuenta que (1) las propuestas deben ejecutarse dentro del Período de Gracia de Ejecución de 7 días que comienza inmediatamente después de la demora del bloqueo de tiempo y (2) la dirección que propone debe mantener la cantidad mínima de poder de propuesta requerida por el contrato de bloqueo de tiempo respectivo hasta que se ejecute el DIP ( ya sea 5M o 20M en el poder de propuesta).

#### _Cómo enviar un DIP en la cadena:_

* Asegúrate de tener suficiente poder de propuesta para crear el DIP. Se puede encontrar más información el Creación de un [DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle)
  * Ejecutor de bloqueo de corto tiempo: 0.5% del suministro total (5M en el poder de propuesta).
  * Ejecutor de Starkware: 0.5% del suministro total (5M en potencia de propuesta).
  * Ejecutor de largo tiempo: 2,0 % del suministro total (20M en el poder de propuesta)
  * Ejecutor de bloqueo de tiempo Merkle-Pauser: 0.5% del suministro total (5M en el poder de propuesta).
* Asegúrate de que haya ETH en la billetera para pagar la tasa de gas.
* Crea una aplicación en Alchemy para la red principal de Ethereum.

![https://dashboard.alchemyapi.io/](../.gitbook/assets/2-draft-dip-example-15.png)

* Después de crear la aplicación, haz clic en "Ver clave" para obtener tu clave de Alchemy (7LOaQtguSm2kSEcFXQH88B): [https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul).

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](../.gitbook/assets/2-draft-dip-example-16.png)

* Descarga e instala Node.js y npm: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Instala Hardhat: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Ejecuta el script que has redactado.
* Verifica el contrato de gobernanza para comprobar que la propuesta ha sido creada en la cadena: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).
* Con la dirección que presentó la propuesta, debes mantener la cantidad mínima de poder de propuesta requerida por el contrato de bloqueo de tiempo respectivo hasta que la propuesta sea ejecutada.

#### _Cómo votar un DIP:_

* Asegúrate de que haya ETH en la billetera para pagar la tasa de gas.
* Puedes votar un DIP activo seleccionando el DIP desde: [https://dydx.community/dashboard](https://dydx.community/dashboard).

![](../.gitbook/assets/2-draft-dip-example-17.png)

La duración de la votación depende del tipo de propuesta. Se puede encontrar más información en [Creación de DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

* Ejecutor de bloqueo de corto tiempo: 4 días.
* Ejecutor de Starkware: 4 días.
* Ejecutor de largo tiempo: 10 días.
* Ejecutor de Pauser de Merkle: 2 días.

#### _Cómo poner una propuesta en cola_

Se puede poner en cola una propuesta exitosa para iniciar el retraso de bloqueo de tiempo.

* Asegúrate de estar utilizando una billetera compatible que contenga Eth.
* Ve a la pestaña "Contrato" en Etherscan y haz clic en "Escribir contrato." El contrato de gobernanza está vinculado [aquí](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-queue-1.png)

* Selecciona la cola y envía el “proposalId.”

![](../.gitbook/assets/2-draft-dip-example-queue-2.png)

El “proposalId” se puede encontrar en Etherscan en el momento de la creación del DIP: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

* Selecciona “haz clic para ver más.”

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-3.png)

* Selecciona "Decodificar datos de entrada".

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-4.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-5.png)

#### _Cómo ejecutar una propuesta:_

Después de la demora de bloqueo de tiempo, se puede ejecutar una propuesta exitosa.

* Ve a la pestaña "Contrato" en Etherscan y haz clic en "Escribir contrato." El contrato de gobernanza está vinculado [aquí](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-1.png)

* Selecciona “ejecutar” envía el “proposalId.”

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-2.png)

* Sigue los pasos anteriores (bajo _Cómo colar una propuesta)_ para encontrar el “proposalId.”
* Ingrese ”0” en “payableAmount (ether).”
