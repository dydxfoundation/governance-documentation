---
description: Una visión general del fondo de participación de liquidez
---

# Módulo de liquidez

`El 2,50 %` del suministro inicial de tokens (`25.000.000 DYDX`2) fue asignado para ser distribuido a los usuarios que apostaban USDC en el fondo de participación de liquidez. El fondo de participación de liquidez no está activo desde el 29 de septiembre de 2022. En el [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para cerrar efectivamente el fondo de participación de liquidez y el fondo de préstamo al establecer las recompensas de los fondos de participación de liquidez por segundo a 0.

\\Anteriormente, DYDX se distribuyó entre los usuarios que participaron USDC en el fondo de participación de liquidez. Los proveedores de liquidez aprobados por la comunidad utilizaron los USDC participados para crear mercados en el protocolo de la capa 2 de dYdX, lo que perpetuó la liquidez disponible en todos los mercados. Los proveedores de liquidez se restringieron a usar fondos prestados fuera del protocolo de la capa 2 de dYdX.

## Visión general **de la participación**

Actualmente, los USDC apostados en el fondo de participación de liquidez no están generando recompensas.

Los 383.562 DYDX previamente distribuidos a los participantes de USDC se acumularán en el Tesoro de Recompensas y pueden ser utilizados por la comunidad dYdX con un [voto de gobernanza](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Desinversión y retiros de USDC

Un inversor debe solicitar retirar USDC al menos `14 días`  (**Ventana de bloqueo**) antes del final de una [**etapa**](../start-here/epochs.md)  para poder retirar los USDC del inversor después del final de esa etapa. Si los inversores no solicitan retirar, sus USDC invertidos se transferirán a la siguiente etapa.

No se pueden solicitar retiros durante la **ventana de bloqueo**.

En el [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para reducir la duración de la ventana de bloqueo de `14 días` a `3 días`.

## ¿Qué es stkUSDC?

Los titulares de USDC que depositen e inviertan sus USDC en el fondo de participación de liquidez recibirán una posición tokenizada (**stkUSDC**). stkUSDC se acuña cuando un usuario invierte en USDC y se quema cuando un usuario utiliza el `withdrawStake` En la misma transacción en la que los USDC salen de la billetera de un inversor, stkUSDC ingresa a la billetera del inversor o viceversa cuando se desinvierte.

Un saldo de stkUSDC puede estar activo o inactivo. Los stkUSDC activos se pueden transferir como ERC-20, pero no se pueden retirar. Los stkUSDC inactivos se pueden retirar, pero no se pueden transferir. Por ejemplo, un usuario puede tener 100 stkUSDC activos y 100 inactivos en su billetera, y el saldo del usuario mostrará 200 stkUSDC, pero la transferencia se revertirá si el usuario intenta transferir más de 100 stkUSDC.

Un saldo invertido para el cual el participante haya solicitado un retiro antes del final de la etapa se consideraría inactivo y, por lo tanto, no transferible.

## Preguntas frecuentes

### ¿Qué es la ventana de bloqueo?

Una ventana de bloqueo es un período de tiempo durante el cual los usuarios no pueden solicitar retiros de USDC invertidos. La función de `solicitud de retiro` ("requestWithdrawal") no se puede utilizar durante una ventana de bloqueo, que está configurada como los últimos `3 días` de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta `3 días `antes del final de una etapa determinada.

### ¿Cómo retiro USDC del fondo de participación? ¿Cuánto tiempo tarda?

Un participante debe solicitar remover la participación de USDC al menos `3 días` antes del final de una etapa para poder retirar los USDC del participante después del final de esa etapa. Si los inversores no solicitan retirar, sus USDC invertidos se transferirán a la siguiente etapa.

Para retirar USDC, los usuarios utilizan la función `de solicitud de` retiro para solicitar el retiro de USDC para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán retirar durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la próxima etapa, los usuarios solicitan la función de `withdrawStake` para transferir USDC inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. La función `withdrawMaxStake` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar `el withdrawMaxStake()`

Para desinvertir USDC del fondo de liquidez, sigue los siguientes pasos:

* Visita [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Haz clic en “**Solicitar**”, para abrir el siguiente modo:

![Solicitud de retiro](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Ingresa la cantidad de USDC que deseas solicitar retirar del fondo y haz clic en "**Solicitar retiro**". Tendrás que pagar las tasas de gas para desinvertir USDC.
* Los inversores que solicitan retirar la participación de USDC al menos `3 días` (**ventana de bloqueo**) antes de que la etapa final actual pueden retirar sus USDC al inicio de la siguiente etapa.

### ¿Qué parámetros pueden cambiar la gobernanza?

La gobernanza de dYdX es responsable de:

* Recompensas por segundo por participar USDC en el fondo de participación de liquidez
* Añadir nuevos prestatarios al, o eliminar prestatarios existentes del, fondo de liquidez de participación
* Cambiar las asignaciones de los USDC prestados a los prestatarios aprobados
  * Las `setBorrowerAllocations` de prestatarios y de asignación de fondos de `setBorrowerAllocations` requieren cambiar las asignaciones de ciertos prestatarios. Se pueden utilizar para agregar y eliminar prestatarios. Los aumentos entran en vigor en la próxima etapa, pero las reducciones restringirán el endeudamiento de inmediato. Estas funciones no se pueden solicitar durante la ventana de bloqueo.
* La duración de la etapa y la ventana de bloqueo se establecen al crear el contrato, pero pueden modificarse
