---
description: Una visión general del fondo de participación de liquidez
hidden: true
---

# 🔋 Módulo de Liquidez

El fondo de participación de liquidez no está activo desde el 29 de septiembre de 2022. En [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), la comunidad dYdX votó [para](https://dydx.community/dashboard/proposal/7) reducir efectivamente el Fondo de Participación de Liquidez y el Fondo de Préstamos al establecer las recompensas del Fondo de Participación de Liquidez por segundo a 0.

Todos los ethDYDX restantes de la asignación de recompensas del módulo de liquidez se migraron a la Tesorería de la comunidad de la cadena dYdX.

Hay más información sobre la Tesorería de la Comunidad de la Cadena dYdX disponible [aquí](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury).

## Visión general **de la participación**

Actualmente, los $USDC apostados en el Fondo de participación de liquidez no están generando recompensas.

## Desinversión y retiros de USDC

Un inversor debe solicitar el retiro de $USDC al menos `3 días` (**Periodo de bloqueo**) antes del final de una [**etapa**](../start-here/epochs.md) para poder retirar los $USDC del inversor después del final de esa etapa. Si los inversores no solicitan retirar, sus $USDC invertidos se transferirán a la siguiente etapa.

No se pueden solicitar retiros durante la **ventana de bloqueo**.

## Preguntas frecuentes

<details>

<summary>¿Qué es el Periodo de Bloqueo?</summary>

Un periodo de bloqueo es un lapso de tiempo durante el cual los usuarios no pueden solicitar retiros de $USDC invertidos. La función de solicitud de retiro ("`requestWithdrawal`") no se puede utilizar durante un periodo de bloqueo, que está configurado como los últimos `3 días` de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta `tres días `antes del final de una etapa determinada.

</details>

<details>

<summary>¿Cómo retiro $USDC del fondo de participación? ¿Cuánto tiempo tarda?</summary>

Un inversor debe solicitar desinvertir $USDC al menos `3 días` antes del final de una etapa para poder retirar sus $USDC una vez finalizada la etapa. Si los inversores no solicitan retirar, sus $USDC invertidos se transferirán a la siguiente etapa.

Para retirar $USDC, los usuarios utilizan la función `requestWithdrawal` (solicitud de retiro) para solicitar el retiro de $USDC para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no podrán ser retirados durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la siguiente etapa, los usuarios llaman a la función `withdrawStake` para retirar $USDC inactivos en una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. La función `withdrawMaxStake` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar `withdrawMaxStake()`.

Para desinvertir $USDC del Fondo de Liquidez, sigue los siguientes pasos:

* Visita [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Haz clic en "**Solicitar**"
* Ingresa la cantidad de $USDC que solicitas retirar del fondo y haz clic en "**Solicitar retiro**". Tendrás que pagar las tasas de gas para desinvertir $USDC.
* Los inversores que solicitan retirar la participación de $USDC al menos `3 días` (**Periodo de bloqueo**) antes de que la etapa final actual pueden retirar sus $USDC al inicio de la siguiente etapa.

</details>

###
