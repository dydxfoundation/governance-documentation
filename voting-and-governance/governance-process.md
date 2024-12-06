---
description: Una descripción general de alto nivel de la arquitectura de gobernanza.
hidden: true
---

# 🏗️ Arquitectura

## Visión general

$ethDYDX, $stkDYDX y $wethDYDX ("Tokens de gobernanza") otorgan a los titulares el derecho de proponer y votar sobre los cambios en dYdX v3. La gobernanza de dYdX se basa en los contratos de gobernanza de AAVE y admite la votación en función de las tenencias de los Tokens de gobernanza.

Las propuestas deben pasar un umbral determinado y un porcentaje de votos positivos según el tipo de propuesta.

Los poderes de votación y propuesta del Token de Gobernanza permiten al titular del Token de Gobernanza hacer propuestas y votar en las propuestas de gobernanza. Ten en cuenta que el titular del Token de Gobernanza puede delegar dichos poderes a otras direcciones de Ethereum.

Hay 8 contratos inteligentes en el eje de la gobernanza de dYdX:

* **Los contratos `de Token $ethDYDX, $stkDYDX y $wethDYDX`**: tienen instantáneas del poder de voto de cada dirección en diferentes bloques en el tiempo.
* **El contrato de `Estrategia de Gobernanza V2`**: Contiene la lógica de medición del poder relativo de los usuarios para proponer y votar. La comunidad dYdX [votó](https://dydx.community/dashboard/proposal/15) por actualizar el contrato `de Estrategia de gobernanza` a `la Estrategia de` gobernanza V2 para dotar a $wethDYDX de la misma funcionalidad de gobernanza que ethDYDX para votar y proponer en la gobernanza de dYdX v3.
* **El contrato `de módulo de seguridad`**: contiene las lógicas para invertir tokens $ethDYDX, tokenizar la posición y obtener recompensas. Los tokens invertidos en el módulo de seguridad conservan todos los derechos de gobernanza.
* **El contrato de `Gobernanza`**: realiza un seguimiento de las propuestas y puede ejecutar propuestas a través del contrato inteligente de Bloqueo de Tiempo.
* **Los contratos `de bloqueo de tiempo`**: pueden poner en cola, cancelar o ejecutar transacciones votadas por la gobernanza. Las funciones de una propuesta son iniciadas por el contrato de bloqueo de tiempo. Las transacciones en cola se pueden ejecutar después de un retraso y antes de la expiración del período de gracia.
* **El contrato de `Bloqueo de Tiempo de Prioridad`**: Lo mismo que el contrato de bloqueo de tiempo, pero permite que un controlador de prioridad ejecute transacciones dentro del **Período Prioritario** (7 días) antes del final del retraso del bloqueo de tiempo.

![Arquitectura de contratos inteligente](../.gitbook/assets/1-smart-contract-architectue.png)

La gobernanza en la cadena de dYdX permite:

* Votar por las propuestas a ser ejecutadas por cualquier contrato ejecutor autorizado
* Participaciones de token instantáneas al comienzo de una propuesta
* Delegar por separado las facultades de voto y propuesta
* Establecer umbrales de gobernanza incluyendo propuestas, quórums y poderes diferenciales de voto
* Cambiar la forma en que se cuentan los votos (cambiando la dirección del contrato inteligente de “Estrategia de Gobernanza” en el contrato de Gobernanza)

## Tipos de Propuestas

Existen cuatro tipos de propuestas con diferentes parámetros que afectan la duración y la ejecución de una propuesta, es decir, las propuestas críticas que afectan el consenso de la gobernanza requieren más tiempo de votación y un mayor diferencial de votos, mientras que las propuestas que afectan solo los parámetros del protocolo requieren menos tiempo de votación y pueden ser implementadas rápidamente. Cada tipo de propuesta debe ser validada por un ejecutor.

#### **Ejecutor de bloqueo de corto tiempo**

El ejecutor de bloqueo de corto tiempo controla lo siguiente:

* Los contratos de incentivos como: el módulo de liquidez, el módulo de seguridad y el módulo de distribuidor de Merkle
* Los fondos de las recompensas y tesorerías de la comunidad
* Acuñar nuevos tokens
* todos los contratos de proxy excepto el módulo de seguridad
* roles de custodio en los contratos de proxy de stark

**Ejecutor de bloqueo de tiempo de prioridad de Starkware**

El ejecutor de bloqueo de tiempo de prioridad de Starkware administra el contrato de StarkEx Perpetual Exchange y ejecuta propuestas que configuran dYdX v3. Starkware tiene un rol de "controlador de prioridad", lo que les permite un período de prioridad de 7 días para activar la ejecución de la propuesta. Sin embargo, los cambios de protocolo los deciden únicamente los titulares de Tokens de Gobernanza a través de la gobernanza de dYdX v3.

#### **Ejecutor de bloqueo de largo tiempo**

El ejecutor de bloqueo de tiempo largo puede ejecutar propuestas que generalmente cambian partes de dYdX v3 que afectan el consenso de gobernanza.

#### **Ejecutor de Merkle-pauser**

El ejecutor de Merkle-pauser puede ejecutar propuestas que congelan la raíz de Merkle, la cual se actualiza periódicamente con el balance de recompensa acumulativo de cada usuario, lo que permite distribuir nuevas recompensas a los usuarios a lo largo del tiempo, en caso de que la raíz propuesta sea incorrecta o maliciosa. También puede vetar las solicitudes de operaciones forzadas de cualquiera de los contratos de proxy de stark.

Los parámetros de bloqueo de tiempo inicial son los siguientes:

![Parámetros de bloqueo de tiempo inicial](../.gitbook/assets/1-initial-timelock-parameters.png)
