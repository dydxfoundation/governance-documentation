---
description: Visión general de los fondos de participación de liquidez.
---

# Fondo de participación de liquidez

2,5% \(`25,000,000 DYDX`\) se distribuirá a los usuarios que inviertan USDC a un fondo de participación de liquidez.

### Objetivos

* Efectos de la red de liquidez de dYdX

## Visión general

La liquidez, especialmente cuando se utiliza correctamente, es un componente central de cualquier operación exitosa. Para promover los efectos de la red de liquidez e incentivar a los creadores de mercado profesionales, DYDX se distribuirá a los usuarios que inviertan USDC en el fondo de participación de liquidez. Los creadores de mercado conocidos y aprobados utilizarán los USDC invertidos para crear mercados en el Protocolo, aumentando la liquidez disponible en todos los mercados. Los creadores de mercado conocidos y aprobados utilizarán los USDC invertidos para crear mercados en el Protocolo, aumentando la liquidez disponible en todos los mercados. Sin embargo, una parte de los USDC invertidos podría perderse si un creador de mercado perdiera fondos \(a través de operaciones no rentables\) y no pudiera reponerlos al fondo de participación de liquidez. Los inversores recibirán DYDX, distribuidos continuamente de acuerdo con la porción de cada participante de los USDC totales en el fondo. Un inversor debe solicitar retirar USDC al menos `14 días` \(**Ventana de Bloqueo**\) antes de la etapa para poder retirar sus USDC después del final de esa etapa. Si los inversores no solicitan retirar, sus USDC invertidos se transferirán a la siguiente etapa.

## Prestatarios aprobados

El contrato de fondos de participación de liquidez opera como un sistema de préstamo bilateral sin garantía.

El monto que se puede retirar depende del porcentaje de asignación del prestatario y del total de fondos disponibles invertidos en el fondo. Tanto el porcentaje de asignación como el total de fondos disponibles pueden cambiar, en tiempos predefinidos especificados por el `LS1EpochSchedule`. Los fondos prestados solo se pueden utilizar en la bolsa de la Capa 2 de dYdX. Esto se aplica a través del contrato de `TrustedBorrowerL2Proxy` que interactúa con el contrato de operaciones L2 \(`StarkPerpetual`\).

Los proveedores de liquidez aprobados inicialmente incluyen `Wintermute`, `Sixtant`, `Kronos`, `Amber` y `MGNR`, que han estado realizando activamente el mercado en el Protocolo desde el lanzamiento.

| Prestatarios previamente aprobados | Porcentaje de asignación inicial | Detalles sobre proveedores de liquidez |
| :--- | :--- | :--- |
| Wintermute | `X%` de TBD | [https://dydx.exchange/blog/ama-recap-wintermute](https://dydx.exchange/blog/ama-recap-wintermute) |
| Sixtant | Y% de TBD | [https://dydx.exchange/blog/ama-recap-sixtant](https://dydx.exchange/blog/ama-recap-sixtant) |
| Kronos \(Wootrade\) | Z% de TBD | [https://dydx.exchange/blog/ama-recap-wootrade](https://dydx.exchange/blog/ama-recap-wootrade) |
| Amber | Z% de TBD |  |
| MGNR | Z% de TBD |  |

Cuando los usuarios solicitan retirar fondos, el saldo asignado de un prestatario para la próxima etapa puede caer por debajo de la cantidad prestada actualmente. En esta situación, el prestatario es responsable de pagar la diferencia entre sus saldos prestados y asignados antes del final de la etapa. Si el saldo prestado de un prestatario es mayor que su asignación al comienzo de la siguiente etapa, se espera y se confía en que devolverá la diferencia antes del comienzo de esa etapa.

A medida que los prestatarios piden prestado y reembolsan los fondos, su saldo neto prestado es registrado. También se realiza un seguimiento del saldo neto total del préstamo entre todos los prestatarios. El saldo restante en poder del contrato se conoce como el saldo no prestado.

La siguiente equidad es válida en todo momento cuando el contrato en su conjunto es tomado en consideración:

total activo + total inactivo = total prestado + total no prestado

### Gobernanza

La gobernanza de dYdX es responsable de:

* Hacer la debida diligencia en los prestatarios existentes
* Añadir nuevos prestatarios al fondo de participación
* Cambio de asignaciones de fondos prestados a prestatarios aprobados
   * Las funciones \`setBorrowerAllocations\` y \`setBorrowingRestriction\` se usan para cambiar las asignaciones de ciertos prestatarios. Se pueden utilizar para agregar y eliminar prestatarios. Los aumentos entran en vigor en la próxima etapa, pero las reducciones restringirán el endeudamiento de inmediato. Estas funciones no se pueden solicitar durante la ventana de bloqueo.
* La duración de la etapa y la ventana de bloqueo se establecen al crear el contrato, pero pueden ser modificadas por la gobernanza de dYdX

### Contabilidad de saldo invertido

Un saldo invertido puede estar en uno de dos estados:

* Activo: Disponible para pedir prestado, gana recompensas de participación y no puede ser retirado por el inversor.
* Inactivo: no disponible para pedir prestado, no gana recompensas y puede ser retirado por el inversor.

Un participante puede tener una combinación de saldos activos e inactivos. Los fondos se contabilizan etapa por etapa como se muestra en el siguiente ejemplo:

Las siguientes operaciones afectan a los saldos invertidos de la siguiente manera:

* Depósito: aumentar el saldo activo.
* Solicitar retiro: pasar algunos fondos de activos a inactivos al final de la etapa actual.
* Retirar: disminuir el saldo inactivo.
* Transferencia: entregar fondos activos a otro inversor.

Para codificar el hecho de que un saldo puede programarse para cambiar al final de una etapa determinada, almacenamos cada saldo como una estructura de tres campos: currentEpoch, currentEpochBalance y nextEpochBalance. Los saldos de usuarios inactivos también hacen uso del sector shortfallCounter.

## Preguntas frecuentes

### ¿Cómo puedo ganar recompensas de participación?

Los inversores pueden depositar USDC en cualquier momento en el fondo de participación de liquidez y comenzar a ganar recompensas de inmediato. Las recompensas de DYDX se obtienen de forma continua de acuerdo con la participación de cada inversor en el fondo total. Las recompensas se pueden reclamar y retirar en cualquier momento.

### ¿Cómo deposito e invierto USDC en el fondo de liquidez?

Para depositar e invertir fondos, los usuarios utilizan la [función](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) \`stake\`. Los usuarios también pueden depositar e invertir en nombre de otra dirección utilizando la [función](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) \`stakeFor\`

Para invertir USDC del fondo de liquidez, sigue los siguientes pasos:

* Haz clic en “invertir”
* Debes habilitar la opción de USDC la primera vez que deposites. Tendrás que hacer esto una sola vez.
* Ingresa la cantidad de USDC que deseas invertir en el fondo
* Haz clic en “Fondos de participación” - tendrás que pagar las tasas de gas para invertir y desinvertir fondos

![](https://lh4.googleusercontent.com/caSDz783Gi-asRNYP8Gm8L5qv_yAuJZwEmUAfl8I1MfHecIF2In10IQCqZBCIpxeXl90eT28GGLbZyts8-x9U5w4Y6LBC4kyehMEalsZu_-aI11S6V7nwPrwtcc75m2M8847jFvv)

Los fondos invertidos están activos y empiezan a ganar recompensas de inmediato.

### Contabilidad de recompensas

Los fondos activos ganan recompensas por el período de tiempo que permanecen activos. Esto significa que, después de solicitar el retiro de algunos fondos, esos fondos seguirán ganando recompensas hasta el final de la etapa. Por ejemplo:

En el escenario anterior, el usuario obtendría recompensas por el período t\_0 y t\_2, que varían con el saldo total invertido en ese período. Si el usuario solo solicita un retiro de una parte de su saldo, el saldo restante seguirá ganando recompensas más allá de t\_2.

### ¿Qué es la ventana de bloqueo?

Una ventana de bloqueo es un período de tiempo durante el cual los usuarios no pueden solicitar retiros de fondos invertidos. La función \`requestWithdrawal\` no se puede utilizar durante una ventana de bloqueo, que se configura inicialmente como los últimos 14 días de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta 7 días antes del final de una etapa determinada.

### ¿Cómo retiro fondos del fondo de participación? ¿Cuánto tiempo tarda?

Se aplica un cronograma de etapas para los retiros a fin de brindar previsibilidad y una cadencia regular para la disponibilidad de fondos en el fondo. Un inversor debe solicitar el retiro de fondos al menos 14 días antes del final de una etapa para poder retirar sus fondos después del final de esa etapa. Si los inversores no solicitan retirar, sus USDC invertidos se transferirán a la siguiente etapa.

Para retirar fondos, los usuarios utilizan la [función](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L73-L83) \`requestWithdrawal\` solicitando el retiro de fondos para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán ser retirados durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la próxima etapa, los usuarios utilizan la función \`[withdrawStake](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L91)\` para transferir fondos inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. La función \`withdrawMaxStake\` es menos eficiente de gas que consultar el máximo a través de eth\_call y utilizar \`withdrawStake\(\)\`.

### ¿Cuáles son los riesgos de invertir en el fondo de participación de liquidez? ¿Qué sucede si un prestatario no paga su deuda?

Los préstamos sin garantía vienen con un estándar de confianza mucho más alto que el prestatario debe cumplir. Los proveedores de liquidez no pueden retirar los USDC invertidos del Protocolo, lo que les obliga a usarlo solo en el Protocolo. Sin embargo, los USDC invertidos podrían perderse si un proveedor de liquidez perdiera la bolsa de fondos y no pudiera reponer sus asignaciones prestadas a través de fuentes de financiación externas.

En este caso, los fondos inactivos pueden estar sujetos a pérdidas socializadas prorrateadas en caso de un déficit en el que un prestatario se atrase en el pago de los fondos que han sido solicitados para retirar. En caso del incumplimiento de pago de un préstamo sin garantía, un prestatario moroso enfrentará un daño significativo a su reputación.

Solvencia de contrato:

En cualquier momento, el contrato estará en uno de los siguientes estados según la relación entre los saldos invertidos y los prestados:

| ![](https://lh3.googleusercontent.com/nTJuAC4WSmhOiAGkM6r-YWzy6z2MIHQnydr8U0n-TReAh_gfqD6ZyalxQpYv9RNBsJzrlw78QB_wp9utqBc-PQZipwzWpxDifD1_zEtyVBhYXRl_f8V-iDMwLBO70LQsftDlXrsr) | ![](https://lh3.googleusercontent.com/x_Yev8ZJrYYm8FTDSdoj0jDXEBY_b9xOC69lpQudQdoALQ_tuQFEbFc5hAU6TbpGNCB6J2BsjMwHb59GrCqR52747j45jSC_BmyzyiY72gTRk4oamv35gO8PPZalA43COZF1pgtP) |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/wX37DQoW9oR4OhJzb4hc5ZxPE1X05OPfyETbUv7WTY0b__WH2PydjJoBuQIREHgeWL18GDn7E1ORgGmcre0R6iYPmwSsdFNzBZ7DBPs0wkajjoDBjxDYDPHcet_-dPPAyS1GWL0v) |  |

Se dice que el contrato es insolvente si:

* el saldo total prestado es mayor que el saldo total activo;
* equivalentemente: el saldo total inactivo es mayor que el saldo total no prestado
* equivalentemente: el saldo total retirable es mayor que el saldo de USDC estipulado en el contrato

De lo contrario, se dice que el contrato es solvente.

Debido a que el préstamo se limita a la proporción de fondos activos asignada al prestatario, y debido a que el saldo inactivo solo puede aumentar entre etapas \(excepto en el caso de transferencias de USDC "descubiertas" al contrato\), el contrato generalmente solo puede pasar de un estado solvente a un estado de insolvencia durante las transiciones entre etapas.

Un prestatario individual siempre recibirá un aviso con al menos una semana de antelación a que su propio saldo asignado caiga por debajo del saldo prestado pendiente. Tal transición solo puede ocurrir entre etapas.

Mientras que el contrato es insolvente, es posible que los usuarios no puedan retirar todos los fondos que se les adeudan. Además, la situación plantea riesgos adicionales si existe alguna incertidumbre sobre si se abordará el déficit y con qué rapidez:

1. Los usuarios pueden verse desincentivados a invertir fondos adicionales, ya que hacerlo puede ponerlos en una posición en la que puedan no recuperar sus fondos.
2. Los usuarios que han invertido actualmente pueden recibir incentivos para "correr hacia la salida" y retirarse lo antes posible, para maximizar sus posibilidades de recuperar sus fondos.

Las pérdidas se rastrean a través de índices que representan la fracción de fondos inactivos que se convirtieron en deuda durante un evento de déficit determinado. Cada saldo inactivo de un inversor almacena un contador de déficit en caché, que representa la cantidad de déficit que sucedió anteriormente en relación con la última actualización del saldo. Cualquier pérdida incurrida por un saldo inactivo se traduce en un crédito igual al saldo de deuda de ese inversor. Consulta LS1DebtAccounting para obtener más información sobre cómo se calcula el índice.

Si el contrato es insolvente, la función markDebt\(\) puede ser utilizada \(por cualquier persona\), dirigida a un prestatario que haya superado su asignación. La cantidad por la cual su saldo prestado excede su saldo de asignación se denomina saldo de deuda. El monto del saldo de la deuda se saca de su saldo prestado y se coloca en un saldo especial que se usa específicamente para contabilizar la deuda pendiente de pago.

Se realiza un ajuste igual a la contabilidad de los fondos invertidos. Una cantidad igual al monto de la deuda se elimina de los saldos inactivos y se agrega a un saldo especial que contabiliza la deuda insuficiente adeudada a los participantes. El saldo inactivo de cada participante se reducirá y recibirán una cantidad equivalente en forma de deuda. De esta forma, la pérdida por insolvencia se socializa \(prorratea\) entre todos los interesados que mantienen saldos inactivos.

Este proceso se describe a continuación:

![](https://lh5.googleusercontent.com/2b2e67wVF3DL32NU0ykTVV0PJWaJ_bdmRQRKgx-5c3_qr_nWNYsuE77JviLtbBxXzASEfIp2Fw4hvzRPeM1a7TAIxq0NYUfo3dZLUhChilDpa5Ygq-YugSvNXKmyf2ul3GQM22SZ)

Si el prestatario endeudado paga la deuda \(o si otra parte, como la gobernanza, la paga en su nombre\), entonces las partes interesadas a las que se les debía la deuda pueden recuperar los fondos por orden de llegada.

### ¿Qué representa una deuda?

La deuda

### ¿Hay algún recurso para los inversores si un prestatario no cumple con los requisitos?

Cuando se utiliza un markDebt\(\) en un prestatario, ese prestatario pierde el derecho a tomar prestados más fondos del contrato. Este derecho puede ser restablecido por la gobernanza.

Potencialmente añadir contenido en el acuerdo de creadores de mercado con la Fundación

