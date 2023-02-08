---
description: Una visión general del Fondo de participación de seguridad
---

# Módulo de seguridad

`El 0,5 %` del suministro de tokens (`5 049 079 $DYDX)` se distribuyó a los usuarios que invierten DYDX en un Fondo de seguridad para respaldar el sistema. Inicialmente, `el 2,50 %` del suministro de tokens (`25 000 000 DYDX`) fue asignado para ser distribuido entre usuarios que invirtieran $DYDX en el Módulo de seguridad. El Módulo de seguridad dejará de estar activo a partir del 28 de noviembre de 2022. En [DIP 17](https://dydx.community/dashboard/proposal/9), la comunidad dYdX [votó](https://dydx.community/dashboard/proposal/7) para desconectar eficazmente el Módulo de seguridad al establecer las recompensas del Módulo de seguridad por segundo a 0.\


Anteriormente, se distribuyó $DYDX a los usuarios que invirtieron $DYDX en el Módulo de seguridad. El Módulo de seguridad era un fondo descentralizado que debía utilizarse en caso de insolvencia u otros problemas con el protocolo dYdX.

Los $DYDX invertidos en el Módulo de seguridad conservan sus derechos de propuesta y voto, así como sus capacidades de delegación.

## Resumen general

Actualmente, los $DYDX invertidos en el Módulo de seguridad no está ganando recompensas.

Los 383 562 $DYDX distribuidos previamente entre los inversores de $DYDX se acumularán en la Tesorería de Recompensas y podrán ser utilizados por la comunidad de dYdX con un [voto de gobernanza](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Desinversión y retiros de DYDX

Los inversores deben solicitar el retiro de fondos al menos `3 días` **(Periodo de bloqueo)** antes del final de la etapa para poder retirar $DYDX una vez finalizada esa etapa. Si los inversores no solicitan un retiro de fondos, sus $DYDX invertidos se transfieren a la siguiente etapa.

No se pueden solicitar retiros durante el **Periodo de bloqueo**.

En [DIP 17](https://dydx.community/dashboard/proposal/9), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para reducir la duración del Periodo de bloqueo de `14 días` a `3 días`.



## Preguntas frecuentes

### ¿Qué es el Periodo de bloqueo?

Un Periodo de bloqueo es un lapso de tiempo durante el cual los usuarios no pueden solicitar retiros de $DYDX invertidos. La función de `requestWithdrawal` (solicitud de retiro) no se puede utilizar durante un Periodo de bloqueo, que está configurado como los últimos `3 días` de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta `tres días `antes del final de una etapa determinada.

### ¿Cómo retiro fondos del Fondo de participación? ¿Cuánto tiempo tarda?

Se aplica un cronograma de etapas para los retiros a fin de brindar previsibilidad y una cadencia regular para la disponibilidad de fondos en el fondo. Un inversor debe solicitar desinvertir al menos `3 días` antes del final de una etapa para poder retirar sus fondos después del final de esa etapa. Si los inversores no solicitan un retiro de fondos, sus $DYDX invertidos se transfieren a la siguiente etapa.

Para retirar fondos, los usuarios utilizan la función \`requestWithdrawal\` solicitando el retiro de fondos para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán ser retirados durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la próxima etapa, los usuarios utilizan la función \`withdrawStake\` para transferir fondos inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. Ten en cuenta que la función \`withdrawMaxStake\` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar \`withdrawStake\(\)\`.

Para retirar $DYDX del Módulo de seguridad, sigue estos pasos:

* Visita  [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Haz clic en “**Solicitar**” e ingresa la cantidad de DYDX que deseas solicitar retirar del fondo.
* Haz clic en “**Solicitar retiro**”. Tendrás que pagar tasas de gas para retirar fondos.
* Los inversores que solicitan retirar DYDX al menos `3 días` antes de que la etapa actual termine pueden retirar DYDX al comienzo de la siguiente etapa.

