---
description: Visión general del Fondo de Participación de Seguridad
hidden: true
---

# 🔐 Módulo de seguridad

El módulo de seguridad dejará de estar activo a partir del 28 de noviembre de 2022. En [DIP 17](https://dydx.community/dashboard/proposal/9), la comunidad dYdX [votó](https://dydx.community/dashboard/proposal/7) para desconectar eficazmente el módulo de seguridad al establecer las recompensas por segundo del Módulo de seguridad a 0.

Todos los ethDYDX restantes de la asignación de recompensas del módulo de liquidez se migraron a la Tesorería de la comunidad de la cadena dYdX.

Hay más información sobre la Tesorería de la Comunidad de la Cadena dYdX disponible [aquí](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury).



## Desinversión y retiros de DYDX

Los inversores deben solicitar el retiro de fondos al menos `3 días` **(Periodo de bloqueo)** antes del final de la etapa para poder retirar $ethDYDX una vez finalizada esa etapa. Si los inversores no solicitan retiros, sus $ethDYDX invertidos se transferirán a la siguiente etapa.

No se pueden solicitar retiros durante la **ventana de bloqueo**.

En [DIP 17](https://dydx.community/dashboard/proposal/9), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/7) para reducir la duración del Periodo de bloqueo de `14 días` a `3 días`.

## Preguntas frecuentes

<details>

<summary>¿Qué es el Periodo de bloqueo?</summary>

Un Periodo de bloqueo es un lapso de tiempo durante el cual los usuarios no pueden solicitar retiros de $DYDX invertidos. La función `requestWithdrawal` no se puede utilizar durante un periodo de bloqueo, que está configurado como los últimos `3 días` de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta `tres días `antes del final de una etapa determinada.

</details>

<details>

<summary>¿Cómo retiro fondos del fondo de participación? ¿Cuánto tiempo tarda?</summary>

Se aplica un cronograma de etapas para los retiros a fin de brindar previsibilidad y una cadencia regular para la disponibilidad de fondos en el fondo. Un inversor debe solicitar desinvertir al menos `3 días` antes del final de una etapa para poder retirar sus fondos después del final de esa etapa. Si los inversores no solicitan retiros, sus $ethDYDX invertidos se transferirán a la siguiente etapa.

Para retirar fondos, los usuarios utilizan la función `` `requestWithdrawal` `` para solicitar un retiro de fondos para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán retirar durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la próxima etapa, los usuarios utilizan la función `` `withdrawStake` `` para transferir fondos inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función `` `withdrawMaxStake` `` para retirar todos los fondos inactivos. Ten en cuenta que la función `` `withdrawMaxStake` `` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar `` `withdrawStake()` ``.

Para retirar $ethDYDX del módulo de seguridad, sigue estos pasos:

* Visita  [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Haz clic en “**Solicitar**” e ingresa la cantidad de $ethDYDX que deseas solicitar retirar del fondo.
* Haz clic en “**Solicitar retiro**”. Tendrás que pagar tasas de gas para retirar fondos.
* Los inversores que solicitan retirar $ethDYDX al menos `3 días` antes de que la etapa actual termine pueden retirar $ethDYDX al comienzo de la siguiente etapa.

</details>

