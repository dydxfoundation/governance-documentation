---
description: Una visión general del fondo de participación de liquidez
---

# Módulo de liquidez

El fondo de participación de liquidez no está activo desde el 29 de septiembre de 2022.

## Visión general **de la participación**

Actualmente, los $USDC apostados en el Fondo de participación de liquidez no están generando recompensas.



## Desinversión y retiros de USDC

Un inversor debe solicitar retirar $USDC al menos `3 días` (**Periodo de bloqueo**) antes del final de una [**etapa**](../start-here/epochs.md)  para poder retirar los $USDC del inversor después del final de esa etapa. Si los inversores no solicitan retirar, sus $USDC invertidos se transferirán a la siguiente etapa.

No se pueden solicitar retiros durante el **Periodo de bloqueo**.

En el [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para reducir la duración de la ventana de bloqueo de `14 días` a `3 días`.

## ¿Qué es stkUSDC?

En la misma transacción en la que los $USDC salen de la billetera de un inversor, $stkUSDC ingresa a la billetera del inversor o viceversa cuando se desinvierte.

Un saldo en $stkUSDC puede estar activo o inactivo. Los $stkUSDC activos se pueden transferir como ERC-20, pero no se pueden retirar. Los $stkUSDC inactivos se pueden retirar, pero no se pueden transferir.

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

*
*

### ¿Qué parámetros pueden cambiar la gobernanza?

La gobernanza de dYdX es responsable de:

*
* Añadir nuevos prestatarios al, o eliminar prestatarios existentes del, fondo de liquidez de participación
*
  * Las `setBorrowerAllocations` de prestatarios y de asignación de fondos de `setBorrowerAllocations` requieren cambiar las asignaciones de ciertos prestatarios. Se pueden utilizar para agregar y eliminar prestatarios. Los aumentos entran en vigor en la próxima etapa, pero las reducciones restringirán el endeudamiento de inmediato. Estas funciones no se pueden solicitar durante la ventana de bloqueo.
* La duración de la etapa y el periodo de bloqueo se establecen al crear el contrato, pero pueden modificarse
