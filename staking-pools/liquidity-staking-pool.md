---
description: Una visión general del Fondo de participación de liquidez
---

# Módulo de liquidez

`El 0,6 %` del suministro de tokens (`5 753 430 $DYDX)` se distribuyó a los usuarios que apostaban USDC en el Fondo de participación de liquidez. Inicialmente, el `2,50 %` del suministro inicial de tokens (`25 000 000 DYDX`) fue asignado para ser distribuido a los usuarios que apostaban $USDC en el Fondo de Participación de LEl 2,50 % del suministro inicial de tokens (25 000 000 DYDX2) fue asignado para ser distribuido a los usuarios que apostaban USDC en el Fondo de participación de liquidez. El Fondo de participación de liquidez no está activo desde el 29 de septiembre de 2022. En el [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para cerrar efectivamente el Fondo de participación de liquidez y el Fondo de préstamos al establecer las recompensas de los fondos de participación de liquidez por segundo a 0.\
\
Anteriormente, se distribuyó $DYDX entre los usuarios que participaron con $USDC en el Fondo de participación de liquidez. Los proveedores de liquidez aprobados por la comunidad utilizaron los $USDC participantes para crear mercados en el Protocolo de la Capa 2 de dYdX, lo que perpetuó la liquidez disponible en todos los mercados. Los proveedores de liquidez se restringieron a usar fondos prestados fuera del Protocolo de la Capa 2 de dYdX.

## Visión general **de la participación**

Actualmente, los $USDC apostados en el Fondo de participación de liquidez no están generando recompensas.

Los 383 562 distribuidos previamente a los participantes de $USDC se acumularán en la Tesorería de recompensas y pueden ser utilizados por el dYdX con un [voto de gobernanza](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Desinversión y retiros de USDC

Un inversor debe solicitar retirar $USDC al menos `3 días` (**Periodo de bloqueo**) antes del final de una [**etapa**](../start-here/epochs.md)  para poder retirar los $USDC del inversor después del final de esa etapa. Si los inversores no solicitan retirar, sus $USDC invertidos se transferirán a la siguiente etapa.

No se pueden solicitar retiros durante el **Periodo de bloqueo**.

En el [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para reducir la duración del Periodo de bloqueo de `14 días` a `3 días`.

## ¿Qué es $stkUSDC?

Los titulares de $USDC que depositen e inviertan sus $USDC en el Fondo de participación de liquidez recibirán una posición tokenizada ($**stkUSDC**). $stkUSDC se acuña cuando un usuario invierte en $USDC y se quema cuando un usuario utiliza el `withdrawStake`. En la misma transacción en la que los $USDC salen de la billetera de un inversor, $stkUSDC ingresa a la billetera del inversor o viceversa cuando se desinvierte.

Un saldo en $stkUSDC puede estar activo o inactivo. Los $stkUSDC activos se pueden transferir como ERC-20, pero no se pueden retirar. Los $stkUSDC inactivos se pueden retirar, pero no se pueden transferir. Por ejemplo, un usuario puede tener 100 $stkUSDC activos y 100 inactivos en su billetera, y el saldo del usuario mostrará 200 $stkUSDC, pero la transferencia se revertirá si el usuario intenta transferir más de 100 $stkUSDC.

Un saldo invertido para el cual el participante haya solicitado un retiro antes del final de la etapa se consideraría inactivo y, por lo tanto, no transferible.

## Preguntas frecuentes

### ¿Qué es el Periodo de bloqueo?

Un periodo de bloqueo es un lapso de tiempo durante el cual los usuarios no pueden solicitar retiros de $USDC invertidos. La función de solicitud de retiro ("`requestWithdrawal`") no se puede utilizar durante un periodo de bloqueo, que está configurado como los últimos `3 días` de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta `tres días `antes del final de una etapa determinada.

### ¿Cómo retiro $USDC del fondo de participación? ¿Cuánto tiempo tarda?

Un inversor debe solicitar desinvertir $USDC al menos `3 días` antes del final de una etapa para poder retirar sus $USDC una vez finalizada la etapa. Si los inversores no solicitan retirar, sus $USDC invertidos se transferirán a la siguiente etapa.

Para retirar $USDC, los usuarios utilizan la función `requestWithdrawal` (solicitud de retiro) para solicitar el retiro de $USDC para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán ser retirados durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la siguiente etapa, los usuarios llaman a la función `withdrawStake` para retirar $USDC inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. La función `withdrawMaxStake` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar `el withdrawMaxStake()`.

Para desinvertir $USDC del Fondo de Liquidez, sigue los siguientes pasos:

* Visita [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Haz clic en “**Solicitar**”, para abrir el siguiente modo:

![Solicitud de retiro](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Ingresa la cantidad de USDC que deseas solicitar retirar del fondo y haz clic en "**Solicitar retiro**". Tendrás que pagar las tasas de gas para desinvertir USDC.
* Los inversores que solicitan retirar la participación de USDC al menos `3 días` (**Periodo de bloqueo**) antes de que la etapa final actual pueden retirar sus USDC al inicio de la siguiente etapa.

### ¿Qué parámetros pueden cambiar la gobernanza?

La gobernanza de dYdX es responsable de:

* Recompensas por segundo por participar USDC en el Fondo de participación de liquidez
* Añadir nuevos prestatarios al, o eliminar prestatarios existentes del, Fondo de liquidez de participación
* Cambiar las asignaciones de los USDC prestados a los prestatarios aprobados
  * Las `setBorrowerAllocations` de prestatarios y de asignación de fondos de `setBorrowerAllocations` requieren cambiar las asignaciones de ciertos prestatarios. Se pueden utilizar para agregar y eliminar prestatarios. Los aumentos entran en vigor en la próxima etapa, pero las reducciones restringirán el endeudamiento de inmediato. Estas funciones no se pueden solicitar durante el periodo de bloqueo.
* La duración de la etapa y el periodo de bloqueo se establecen al crear el contrato, pero pueden modificarse
