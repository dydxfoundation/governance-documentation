---
description: Una visión general del fondo de participación de seguridad
---

# Módulo de seguridad

`El 2,50%` del suministro inicial de tokens (`25,000,000 DYDX`) se distribuirá a los usuarios que inviertan DYDX en un fondo de seguridad para respaldar el sistema.

**Objetivos**

* Bootstrap, un fondo descentralizado que se utilizará en caso de insolvencia u otros problemas con el protocolo.
* Incentivar a los tenedores de DYDX a gobernar correctamente: los titulares de DYDX se arriesgan a eventos dilusivos como último respaldo y actúan como gobernantes de riesgo en el sistema.

Los DYDX invertidos en el módulo de seguridad conservan sus derechos de propuesta y voto, así como sus capacidades de delegación.

Comienza a invertir en [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*

## Visión general

La seguridad y la protección del usuario han sido un enfoque clave desde el lanzamiento del Protocolo. Por ese motivo, se distribuirá DYDX a los usuarios que inviertan DYDX en el fondo de seguridad para crear una red de seguridad adicional para los usuarios del Protocolo. Los inversores recibirán DYDX continuamente de manera proporcional a su porción total de DYDX en el fondo.

El fondo de seguridad se activará en DYDX y serán transferibles el 8 de septiembre de 2021 a las 15:00 UTC.

## Retiros

Los inversores deben solicitar el retiro de fondos al menos `14 días` **(ventana de bloqueo)** antes del final de la etapa para poder retirar fondos después del final de esa etapa. Si los inversores no solicitan retirar, sus DYDX invertidos se transferirán a la siguiente etapa.

## Riesgos

Los DYDX invertidos pueden reducirse drásticamente como resultado de un evento de déficit. La reducción se produce a discreción de la gobernanza de DYDX y requiere un voto de la misma para que se ejecute.

Al igual que los participantes en cualquier protocolo DeFi, las partes interesadas en el Módulo de seguridad están expuestas al riesgo del contrato inteligente, si existe una vulnerabilidad en el código del contrato inteligente subyacente. Todos los contratos inteligentes de DYDX y gobernanza han sido auditados y probados rigurosamente.

## Eventos de déficit

La interpretación de la ocurrencia de un evento de déficit está sujeta a un voto de la gobernanza de dYdX, pero puede incluir:

* La solvencia de operaciones (por ejemplo, la operación queda subcolateralizada debido a liquidaciones no rentables)
* Ataques de contratos inteligentes
* Otros eventos que la gobernanza de dYdX considera haber resultado en un déficit

En un evento de déficit, los saldos de los titulares de tokens pueden ser reducidos y transferidos a otra dirección o contrato (establecido por la  gobernanza de dYdX caso por caso). La gobernanza de dYdX debe aprobar una breve propuesta de bloqueo de tiempo para reducir drásticamente los tokens invertidos. Después de un voto de gobernanza sobre la reducción de los tokens de DYDX invertidos, los DYDX reducidos pueden ser subastados en el mercado para ser vendidos contra los activos necesarios y así mitigar el déficit incurrido.

## Preguntas frecuentes

### ¿Cómo puedo ganar recompensas de participación?

Los inversores pueden depositar DYDX en el fondo de participación de seguridad en cualquier momento y comenzar a ganar recompensas de inmediato. Las recompensas de DYDX se obtienen de forma continua según la participación de cada inversor en el fondo total en el lapso de un segundo. Las recompensas se pueden reclamar y retirar en cualquier momento.

Los fondos activos ganan recompensas por el período de tiempo que permanecen activos. Esto significa que, después de solicitar el retiro de algunos fondos, esos fondos seguirán ganando recompensas hasta el final de la etapa. Esto se puede confirmar en el siguiente ejemplo del [fondo de participación de liquidez](https://docs.dydx.community/dydx-governance/staking-pools/liquidity-staking-pool):

![](../.gitbook/assets/1-earning-staking-rewards.png)

En el escenario anterior, el usuario ganaría recompensas por el **período 0** al **periodo 2**, que variaría con el saldo total invertido en ese período. Si el usuario solo solicita un retiro de una parte de su saldo, el saldo restante seguirá ganando recompensas más allá del **Periodo 2**.

### ¿Cómo deposito e invierto DYDX en el fondo de seguridad?

Para invertir DYDX en el fondo de seguridad, sigue estos pasos:

* Visita  [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Haz clic en “**Stake**”
* Debes habilitar DYDX la primera vez que deposites. Solo tendrás que hacer esto una vez e incurrir en tarifas de gas únicamente una vez.
* Ingresa la cantidad de DYDX que deseas invertir en el fondo.
* Haz clic en “**Fondos de participación**”. Tendrás que pagar tasas de gas para invertir y desinvertir fondos.

Los fondos invertidos están ahora activos y empiezan a ganar recompensas de inmediato.

Para depositar e invertir fondos directamente en el contrato inteligente, los usuarios utilizan la [función](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) \`stake\` Los usuarios también pueden depositar e invertir en nombre de otra dirección utilizando la [función](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) \`stakeFor\`.

### ¿Qué son los stkDYDX?

Para contribuir a seguridad del protocolo y recibir incentivos, los titulares de DYDX depositarán sus tokens en el módulo de seguridad. A cambio, recibirán una posición tokenizada (**stkDYDX**) que puede ser retirada o transferida como ERC-20. Los **stkDYDX** tienen los mismos derechos de propuesta y votación que los DYDX para la gobernanza de dYdX.

### ¿Qué es la ventana de bloqueo?

Una ventana de bloqueo es un período de tiempo durante el cual los usuarios no pueden solicitar retiros de fondos invertidos. Se aplica un cronograma de etapas para los retiros a fin de brindar previsibilidad y una cadencia regular para la disponibilidad de fondos en el fondo. Un inversor debe solicitar invertir fondos antes de la ventana de bloqueo para poder retirar sus fondos después del final de esa etapa. Si un inversor no solicita retirar, sus fondos invertidos serán transferidos a la siguiente etapa.

La ventana de bloqueo recomendada para el fondo de seguridad es de `14 días`.

### ¿Cómo funciona la contabilidad de saldos invertidos?

Un saldo invertido puede estar en uno de dos estados:

* **Activo**: disponible para pedir prestado, gana recompensas de participación y no puede ser retirado por el inversor.
* **Inactivo**: no disponible para pedir prestado, no gana recompensas y puede ser retirado por el inversor.

Un participante puede tener una combinación de saldos activos e inactivos. Los fondos se contabilizan etapa por etapa como se muestra en el siguiente ejemplo:

![](../.gitbook/assets/1-staked-balance-accounting.png)

Las siguientes operaciones afectan a los saldos invertidos de la siguiente manera:

* **Depósito**: aumentar el saldo activo.
* **Solicitar** **un retiro**: pasar algunos fondos de activos a inactivos al final de la etapa actual.
* **Retirar**: disminuir el saldo inactivo.
* **Transferencia**: entregar fondos activos a otro inversor.

Para codificar el hecho de que un saldo puede programarse para cambiar al final de una etapa determinada, almacenamos cada saldo como una estructura de tres campos: currentEpoch, currentEpochBalance y nextEpochBalance.

### ¿Cómo retiro fondos del fondo de participación? ¿Cuánto tiempo tarda?

Se aplica un cronograma de etapas para los retiros a fin de brindar previsibilidad y una cadencia regular para la disponibilidad de fondos en el fondo. Un inversor debe solicitar desinvertir al menos `14 días` antes del final de una etapa para poder retirar sus fondos después del final de esa etapa. Si los inversores no solicitan retirar, sus DYDX invertidos se transferirán a la siguiente etapa.

Para retirar fondos, los usuarios utilizan la función \`requestWithdrawal\` solicitando el retiro de fondos para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán ser retirados durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la próxima etapa, los usuarios utilizan la función \`withdrawStake\` para transferir fondos inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. Ten en cuenta que la función \`withdrawMaxStake\` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar \`withdrawStake\(\)\`.

Para retirar DYDX del fondo de liquidez, sigue estos pasos:

* Visita  [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Haz clic en “**Solicitud**” e ingresa la cantidad de DYDX que deseas solicitar retirar del fondo.
* Haz clic en “**Solicitar retiro**”. Tendrás que pagar tasas de gas para retirar fondos.
* Los inversores que solicitan retirar DYDX al menos 14 días antes de que la etapa actual finalice pueden retirar sus DYDX al comienzo de la siguiente etapa.

### ¿Cuáles son los riesgos de los inversores para el fondo de participación de seguridad? ¿Qué sucede en el caso de un evento de déficit?

La decisión de un inversor de bloquear DYDX en el fondo de seguridad lo expone al riesgo de un evento de déficit, lo que puede resultar en la reducción de los fondos de DYDX invertidos a discreción de la gobernanza de DYDX.

Todos los fondos del contrato, activos o inactivos, son reductibles. Dentro del contrato, la reducción se implementa a través de una actualización del tipo de cambio entre DYDX y stkDYDX. Esto significa que a medida que ocurran las reducciones, el tipo de cambio entre DYDX y stkDYDX divergirá de su valor inicial de 1:1. Ten en cuenta que la ganancia de recompensas de participación no se verá afectada por las reducciones.
