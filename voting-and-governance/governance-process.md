---
description: Una descripción general de alto nivel de la arquitectura de gobernanza.
---

# Arquitectura

## Visión general

DYDX otorga a los titulares el derecho de proponer y votar los cambios en el Protocolo. La gobernanza de DYDX se basa en los contratos de gobernanza de AAVE y admite la votación basada en las tenencias de tokens de DYDX.

Las propuestas deben pasar un umbral determinado y un porcentaje de votos positivos según el tipo de propuesta.

Estos tokens DYDX se pueden utilizar para hacer propuestas o votar sobre propuestas de gobernanza o delegarse a otras direcciones de Ethereum.

Hay 6 contratos inteligentes en el eje de la gobernanza de dYdX:

* **El contrato `de tokens DYDX`**: contiene instantáneas del poder de voto de cada dirección en diferentes bloques de tiempo.
* **El contrato `de estrategia de gobernanza`**: contiene la lógica de medición del poder relativo de los usuarios para proponer y votar.
* **El contrato `de módulo de seguridad`**: contiene las dinámicas para invertir tokens DYDX, tokenizar la posición y obtener recompensas. Los tokens invertidos en el módulo de seguridad conservan todos los derechos de gobernanza.
* **El contrato `de gobernanza`**: realiza un seguimiento de las propuestas y puede ejecutar propuestas a través del contrato inteligente de bloqueo de tiempo.
* **Los contratos `de bloqueo de tiempo`**: pueden poner en cola, cancelar o ejecutar transacciones votadas por la gobernanza. Las funciones de una propuesta son iniciadas por el contrato de bloqueo de tiempo. Las transacciones en cola se pueden ejecutar después de un retraso y antes de la expiración del período de gracia.
* **El contrato `de bloqueo cronométrico de prioridad`**: Lo mismo que el contrato de bloqueo de tiempo, pero permite que un controlador de prioridad ejecute transacciones dentro del **período** prioritario (7 días) antes del final del retraso del bloqueo de tiempo.

![Smart contract architecture](<.. /.gitbook/assets/image (49).png>)

La gobernanza en la cadena de dYdX permite:

* Votar por las propuestas a ser ejecutadas por cualquier contrato ejecutor autorizado
* Participaciones de token instantáneas al comienzo de una propuesta
* Delegar por separado las facultades de voto y propuesta
* Establecer umbrales de gobernanza incluyendo propuestas, quórums y poderes diferenciales de voto
* Cambiar la forma en que se cuentan los votos (cambiando la dirección del contrato inteligente de “Estrategia de gobernanza” en el contrato de gobernanza)

## Tipos de propuestas

Existen cuatro tipos de propuestas con diferentes parámetros que afectan la duración y la ejecución de una propuesta, es decir, las propuestas críticas que afectan el consenso de la gobernanza requieren más tiempo de votación y un mayor diferencial de votos, mientras que las propuestas que afectan solo los parámetros del protocolo requieren menos tiempo de votación y pueden ser rápidamente implementadas. Cada tipo de propuesta debe ser validada por un ejecutor.

#### **Ejecutor de bloqueo de corto tiempo**

El ejecutor de bloqueo de corto tiempo controla lo siguiente:

* Los contratos de incentivos como: el módulo de liquidez, el módulo de seguridad y el módulo de distribuidor de Merkle
* Los fondos de las recompensas y tesorerías de la comunidad
* Acuñar nuevos tokens
* todos los contratos de proxy excepto el módulo de seguridad
* roles de custodio en los contratos de proxy de stark

**Ejecutor de bloqueo de tiempo de prioridad de Starkware**

El ejecutor de bloqueo de tiempo de prioridad de Starkware es propietario del contrato de intercambio de perpetuals de StarkEx. Puede ejecutar propuestas que controlan la configuración de la bolsa de la Capa 2 de dYdX.

Dependiendo de la acción a tomar, es posible que el equipo de Starkware deba involucrarse para implementar correctamente el cambio en la operación. Por esta razón, a este ejecutor se le otorga un rol de “controlador de prioridad”, el cual otorga a Starkware un período de 7 días (**Período de Prioridad**) en el cual solo él tiene la capacidad de activar la ejecución de una propuesta.

Starkware no tiene control sobre _los_ cambios que se realizan en el protocolo. Solo los titulares de tokens DYDX a través de la gobernanza de dYdX, tienen la capacidad de aprobar o denegar los cambios en el protocolo de operaciones.

#### **Ejecutor de bloqueo de largo tiempo **

El ejecutor de bloqueo de largo tiempo puede ejecutar propuestas que generalmente cambian partes del Protocolo afectando el consenso de gobernanza.

#### **Ejecutor Merkle-pauser**

Ejecutor Merkle-pauser: el ejecutor Merkle-pauser puede ejecutar propuestas que congelan la raíz de Merkle, la cual se actualiza periódicamente con el saldo de recompensa acumulativo de cada usuario, lo que permite distribuir nuevas recompensas a los usuarios a lo largo del tiempo, en caso de que la raíz propuesta sea incorrecta o maliciosa. También puede vetar las solicitudes de operaciones forzadas de cualquiera de los contratos de proxy de stark.

Los parámetros de bloqueo de tiempo inicial son los siguientes:

![Initial timelock parameters](<.. /.gitbook/assets/Initial Timelock Parameters.png>)

