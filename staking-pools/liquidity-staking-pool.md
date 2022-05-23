---
description: Una visión general del fondo de participación de liquidez
---

# Módulo de liquidez

El `2.50%` del suministro de token inicial (`25,000,000 DYDX`) se distribuirá a los usuarios que participen con USDC al fondo de participación de liquidez.

### Objetivos

* Incentivar la asignación de USDC con fines de creación de mercado en el protocolo dYdX de la capa 2.
* Asignar capital a proveedores de liquidez de alto rendimiento para aumentar el margen, la profundidad y el tiempo de actividad en dYdX.

Comenzar a participar en [**dydx.community/dashboard/pools/liquidez**](https://dydx.community/dashboard/pools/liquidity)**.**

## Visión general **de la participación**

La liquidez es un componente central de cualquier operación exitosa. Para promover los efectos de la red de liquidez e incentivar a los proveedores profesionales de liquidez, DYDX se distribuirá a los usuarios que inviertan USDC en el fondo de participación de liquidez. Los proveedores de liquidez aprobados por la comunidad utilizarán el USDC apostado para crear mercados en el Protocolo de la Capa 2 de dYdX, aumentando la liquidez disponible en los mercados. Los proveedores de liquidez están restringidos a usar fondos prestados fuera del Protocolo de la capa 2 de dYdX.

Los inversores ganarán recompensas de DYDX por invertir en USDC. Las recompensas de DYDX se distribuirán continuamente de acuerdo con la porción de USDC total de cada participante en el fondo.

Cada proveedor de liquidez e inversor está obligado a ser parte del Acuerdo de crédito rotativo (enlace [aquí](https://dydx.foundation/revolving-credit-agreement)). El acuerdo pone en lenguaje natural los términos del grupo de participación de liquidez para otorgar a cada participante un derecho exigible contra cualquier proveedor de liquidez que no reembolse el USDC prestado. El acuerdo es solo entre cada inversor y cada proveedor de liquidez. La Fundación dYdX no es parte en el acuerdo y no tiene derechos u obligaciones en él.

## Desinversión y retiros de USDC

Un inversor debe solicitar retirar USDC al menos `14 días` (**Ventana de bloqueo**) antes del final de una [**etapa**](../start-here/epochs.md)  para poder retirar los USDC del inversor después del final de esa etapa. Si los inversores no solicitan retirar, sus USDC invertidos se transferirán a la siguiente etapa.

No se pueden solicitar retiros durante la **ventana de bloqueo**.

## Riesgos de participación

Los prestatarios del grupo no están obligados a bloquear la garantía. Todos los prestatarios son proveedores de liquidez profesionales y de confianza. La gobernanza puede actualizar la lista de prestatarios permitidos y sus asignaciones de fondos.

Cuando los usuarios solicitan retirar USDC, el saldo asignado de un prestatario para la próxima etapa puede caer por debajo del monto del prestatario actualmente prestado. En esta situación, el prestatario es responsable de pagar la diferencia entre sus saldos prestados y asignados antes del final de la etapa.

Si un prestatario no paga al fondo un saldo adeudado al final de la etapa, se considera que está en incumplimiento y no se le permitirá pedir prestado más USDC hasta que pague la deuda. Los inversores pueden perder USDC en caso de que un prestatario nunca pague una deuda. Los inversores pueden perder una parte de los USDC invertidos si un creador de mercado pierde USDC y no puede reponer el fondo de participación de liquidez.

Los inversores también están expuestos al riesgo del contrato inteligente si existe una vulnerabilidad en el código del contrato inteligente subyacente. Todos los contratos inteligentes de DYDX y gobernanza han sido auditados y probados rigurosamente.

Con el fin de reducir el riesgo para los inversores, cada inversor y proveedor de liquidez deberá convertirse en parte del acuerdo de crédito rotativo (enlace [aquí](https://dydx.foundation/revolving-credit-agreement)), pero celebrar el contrato no garantiza que un proveedor de liquidez reembolse todos los montos prestados, incluso si se hacen cumplir los derechos de una parte interesada en virtud del acuerdo.

## Prestatarios aprobados

El contrato de fondo de participación de liquidez como un sistema de liquidez libre de intereses, sin colateral y bilateral.

El monto que se puede retirar depende del porcentaje de asignación del prestatario y de los USDC total disponibles invertidos en el fondo. Tanto el porcentaje de asignación como los USDC total disponibles pueden cambiar, en momentos predefinidos especificados por el `LS1EpochSchedule` Los USDC prestados solo se puede usar en el Protocolo de capa 2 de dYdX; esto se aplica a través del contrato `StarkProxy` que interactúa con el `contrato de bolsa de perpetuals de StarkEx`.

Los proveedores de liquidez aprobados inicialmente incluyen `Wintermute`, `Amber Group`, `Wootrade (Kronos)`, `Sixtant` y `DAT Trading`, que han estado creando mercado activamente en el protocolo de capa 2 de dYdX.

| Prestatarios previamente aprobados | Porcentaje de asignación inicial | Dirección de Ethereum | StarkProxy | Detalles sobre proveedores de liquidez |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wintermute | 25% | [0x4f3a120E72C76c22ae802D129F599BFDbc31cb81](https://etherscan.io/address/0x4f3a120E72C76c22ae802D129F599BFDbc31cb81) | [0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6](https://etherscan.io/address/0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6) | [https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/](https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/) |
| Amber Group | 25% | [0x39Ad99E33ab7Ee85818741dD6076112188bc2611](https://etherscan.io/address/0x39Ad99E33ab7Ee85818741dD6076112188bc2611) | [0x3e6E9EFb0A677a24F47093a22044dc5451A028cF](https://etherscan.io/address/0x3e6E9EFb0A677a24F47093a22044dc5451A028cF) | [https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/](https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/) |
| WOO Network (Kronos) | 20% | [0x38d981c3c42b2ec8e9572f560552407d0f1279fb](https://etherscan.io/address/0x38d981c3c42b2ec8e9572f560552407d0f1279fb) | [0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06](https://etherscan.io/address/0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06) | [https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/](https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/) |
| Sixtant | 20% | [0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c](https://etherscan.io/address/0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c) | [0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2](https://etherscan.io/address/0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2) | [https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/](https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/) |
| DAT Trading  | 10% | [0x83E8fb8f4DAE0f42d68FdbBf85d4191a5e6f92F8](https://etherscan.io/address/0x83e8fb8f4dae0f42d68fdbbf85d4191a5e6f92f8) | [0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874](https://etherscan.io/address/0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874) | [https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/](https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/) |

## Contabilidad de saldo invertido

Un saldo invertido puede estar en uno de dos estados:

* **Activo**: Disponible para pedir prestado, gana recompensas de participación y no puede ser retirado por el inversor.
* **Inactivo**: no disponible para pedir prestado, no gana recompensas y puede ser retirado por el inversor.

Un participante puede tener una combinación de saldos activos e inactivos. Los USDC se contabilizan etapa por etapa como se muestra en el siguiente ejemplo:

![Staked balance accounting](<.. /.gitbook/assets/image (34).png>)

Las siguientes operaciones afectan a los saldos invertidos de la siguiente manera:

* **Depósito**: aumentar el saldo activo.
* **Solicitud de retiro**: al final de la etapa actual, pasar de algunos USDC activos a inactivos.
* **Retirar**: disminuir el saldo inactivo.
* **Transferir**: pasar algunos USDC activos a otro participante.

Para codificar el hecho de que un saldo puede programarse para cambiar al final de una determinada etapa, cada saldo se almacena como una estructura de tres campos: currentEpoch, currentEpochBalance y nextEpochBalance. Los saldos de usuarios inactivos también hacen uso del sector shortfallCounter.

### ¿Qué es stkUSDC?

Los titulares de USDC que depositen e inviertan sus USDC en el fondo de participación de liquidez recibirán una posición tokenizada (**stkUSDC**). stkUSDC se acuña cuando un usuario invierte en USDC y se quema cuando un usuario utiliza el `withdrawStake` En la misma transacción en la que los USDC salen de la billetera de un inversor, stkUSDC ingresa a la billetera del inversor o viceversa cuando se desinvierte.

Un saldo de stkUSDC puede estar activo o inactivo. Los stkUSDC activos se pueden transferir como ERC-20, pero no se pueden retirar. Los stkUSDC inactivos se pueden retirar, pero no se pueden transferir. Por ejemplo, un usuario puede tener 100 stkUSDC activos y 100 inactivos en su billetera, y el saldo del usuario mostrará 200 stkUSDC, pero la transferencia se revertirá si el usuario intenta transferir más de 100 stkUSDC.

Un saldo invertido para el cual el participante haya solicitado un retiro antes del final de la etapa se consideraría inactivo y, por lo tanto, no transferible.

## Preguntas frecuentes **de los participantes**

### ¿Cómo puedo ganar recompensas de participación?

Los inversores pueden depositar USDC en cualquier momento en el fondo de participación de liquidez y comenzar a ganar recompensas de inmediato. Las recompensas de DYDX se obtienen de forma continua según la participación de cada inversor en el fondo total en el lapso de un segundo. Las recompensas se pueden reclamar y retirar en cualquier momento.

Los USDC invertidos ganan recompensas por el período de tiempo que permanecen activos. Esto significa que después de solicitar un retiro de algunos USDC, estos USDC continuarán ganando recompensas hasta el final de la etapa. Por ejemplo:

![Rewards accounting](<.. /.gitbook/assets/image (65).png>)

En el escenario anterior, el usuario ganaría recompensas por **el** período 0 al **periodo 2**, que variaría con el saldo total invertido en ese período. Si el usuario solicita únicamente un retiro de parte del saldo del usuario, entonces el saldo restante continuará ganando recompensas más allá del **periodo 2**.

### ¿Cómo deposito e invierto USDC en el fondo de liquidez?

Para apostar USDC en el fondo de liquidez, sigue estos pasos:

* Dirígete a [https://dydx.community/dashboard/pools/liquidity](https://dydx.community/dashboard/pools/liquidity)
* Haz clic en “invertir”
* Debes habilitar la opción de USDC la primera vez que deposites. Solo tendrás que hacer esto una vez y pagar las tasas de gas solo una vez.
* Ingresa la cantidad de USDC que deseas invertir en el fondo.
* Haz clic en “Fondos de participación” - tendrás que pagar las tasas de gas para invertir, solicitar retiros y retirar USDC.

![](<.. /.gitbook/assets/image (57).png>)

Los USDC invertidos ahora están activos y puedes empezar a ganar recompensas inmediatamente.

Para depositar e invertir USDC directamente en el contrato inteligente`,` los usuarios solicitan la función de participación. Los usuarios también pueden depositar e invertir USDC en nombre de otra dirección llamando a la función `stakeFor`. Incluso si inviertes USDC directamente en el contrato inteligente, se considerará que has recibido una notificación y ha revisado el acuerdo de crédito renovable (enlace [aquí](https://dydx.foundation/revolving-credit-agreement))

### ¿Qué es la ventana de bloqueo?

Una ventana de bloqueo es un período de tiempo durante el cual los usuarios no pueden solicitar retiros de USDC invertidos. La función `de solicitud de retiro` no se puede utilizar durante una ventana de bloqueo, que inicialmente se configura como los últimos `14 días` de una etapa. Las nuevas etapas comienzan cada 28 días. En otras palabras, los usuarios pueden solicitar un retiro para la próxima etapa hasta `14 días` antes del final de una etapa determinada.

### ¿Cómo retiro USDC del fondo de participación? ¿Cuánto tiempo tarda?

Se aplica un cronograma de etapas para los retiros a fin de brindar previsibilidad y una cadencia regular para la disponibilidad de USDC en el fondo. Un inversor debe solicitar retirar los USDC al menos `14 días` antes del final de una etapa para poder retirar los USDC del inversor después del final de esa etapa. Si los inversores no solicitan retirar, sus USDC invertidos se transferirán a la siguiente etapa.

Para retirar USDC, los usuarios utilizan la función `de solicitud de` retiro para solicitar el retiro de USDC para la próxima etapa. Los fondos de los usuarios permanecerán invertidos y no se podrán retirar durante la etapa actual. A partir de la siguiente etapa, los fondos estarán “inactivos” y disponibles para el retiro.

En la próxima etapa, los usuarios solicitan la función de `withdrawStake` para transferir USDC inactivos a una dirección específica. Los usuarios pueden seleccionar la cantidad de fondos inactivos que desean retirar o utilizar la función \`withdrawMaxStake\` para retirar todos los fondos inactivos. La función `withdrawMaxStake` es menos eficiente en gas que consultar el máximo a través de eth\_call y utilizar `el withdrawMaxStake()`

Para desinvertir USDC del fondo de liquidez, sigue los siguientes pasos:

* Ve a [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)****
* Haz clic en “**Solicitar**”, para abrir el siguiente modo:

![Requesting withdraw](<.. /.gitbook/assets/image (58).png>)

* Ingresa la cantidad de USDC que deseas solicitar retirar del fondo y haz clic en "**Solicitar retiro**". Tendrás que pagar las tasas de gas para desinvertir USDC.
* Los inversores que solicitan desinvertir USDC al menos 14 días (**ventana de bloqueo**) antes de que la etapa final actual pueden retirar sus USDC al inicio de la siguiente etapa.

### ¿Qué parámetros pueden cambiar la gobernanza?

La gobernanza de dYdX es responsable de:

* Hacer la debida diligencia en los prestatarios existentes
* Añadir nuevos prestatarios a y/o eliminar prestatarios existentes del fondo de liquidez de participación
* Cambiar las asignaciones de los USDC prestados a los prestatarios aprobados
   * Las `setBorrowerAllocations` de prestatarios y de asignación de fondos de `setBorrowerAllocations` requieren cambiar las asignaciones de ciertos prestatarios. Se pueden utilizar para agregar y eliminar prestatarios. Los aumentos entran en vigor en la próxima etapa, pero las reducciones restringirán el endeudamiento de inmediato. Estas funciones no se pueden solicitar durante la ventana de bloqueo.
* La duración de la etapa y la ventana de bloqueo se establecen al crear el contrato, pero pueden modificarse

## **Preguntas frecuentes de los prestatarios**

### **Solicitud de préstamos**

Los USDC invertidos ingresan a un fondo asignado a los prestatarios aprobados. Cada prestatario tiene un porcentaje de asignación controlado por la gobernanza y puede pedir prestado hasta esta asignación. La desinversión está sujeta a un “calendario de etapa”: los USDC invertidos solo pueden ser retirables (es decir, “inactivos”) al inicio de una etapa.

Los USDC solicitados para el retiro deben ser devueltos por los prestatarios antes del final de la etapa. En caso de pago insuficiente, la cantidad pagada de manera insuficiente se convierte en un "saldo en mora" y el contrato de participación se vuelve a estabilizar. El prestatario infractor debe pagar el saldo de la deuda y se le restringirá el endeudamiento hasta que la gobernanza lo restablezca.

Los prestatarios están sujetos a todos los términos del Acuerdo de crédito rotativo (enlace [aquí](https://dydx.foundation/revolving-credit-agreement)).

### **Características de StarkProxy**

#### **Auto-pago**

Los prestatarios pueden utilizar `autoPayOrBorrow()` para garantizar el máximo uso de los USDC asignados y el reembolso de los retiros solicitados. La función solo debe ser utilizada correctamente una vez por etapa para que un prestatario pueda asegurar que cumple con sus responsabilidades.

La función se revertirá si se utiliza en la primera mitad de la etapa, ya que está fuera de la ventana de bloqueo. Se revertirá si el contrato de `StarkProxy`contract no tiene suficientes USDC para realizar el reembolso. En este caso, se deben agregar o retirar USDC de la bolsa antes de utilizar el `autoPayOrBorrow()`

#### **USDC de propiedad de los prestatarios**

Un prestatario puede depositar sus propios USDC de forma `segura` en el protocolo de la capa 2 de dYdX y en la misma cuenta que los USDC prestados. Los USDC pueden retirarse de `StarkProxy` en cualquiera de las siguientes situaciones:

* Los USDC mantenidos dentro del contrato `StarkProxy` en exceso del saldo prestado se puede retirar en cualquier momento.
* La gobernanza puede aprobar el retiro de una cantidad determinada.
   * Nota: Esto se puede usar para permitir que el prestatario retire ganancias sin tener que retirar la mayor parte de USDC del Protocolo de la Capa 2 de dYdX.

#### **Roles de los prestatarios**

El contrato `StarkProxy`contract soporta los siguientes roles controlados por los prestatarios. Estos pueden ejercerse en una sola dirección o direcciones separadas dependiendo de las necesidades de seguridad del prestatario. Cada rol puede ser ocupado por cualquier número de direcciones.

Propietario

* Otorga o revoca el rol de administrador de delegación.
* Agrega o elimina destinatarios permitidos para USDC retirados de `StarkProxy`.
* Agrega o elimina claves STARK permitidas para usar en el protocolo de capa 2 de dYdX.
* Establece las asignaciones de ERC20 en los contratos de `LiquidityStakingV1` y `StarkPerpetual`   
* Llama a `forcedWithdrawalRequest()` o `forcedTradeRequest()` en el contrato `de bolsa de Perpetuals de StarkEx`.

Administrador de delegación

* Otorga o revoca el prestatario, el operador de bolsa y los roles de operador de retiro.

Prestatario

* Utiliza el `autoPayOrBorrow()`, `borrow()`, `repay()`, y `repayDebt()` en el contrato de participación de liquidez.

Operador intercambio

* Utiliza el `registerUserOnExchange()`, `depositToExchange()`, y `withdrawFromExchange()` en el contrato `de bolsa de perpetuals de StarkEx`.

Operador de retiro

* Hace un retiro externo válido (ver arriba) fuera de `StarkProxy` a un destinatario permitido.

#### **Limitaciones**

Las transferencias de la capa 2 en el Protocolo de la capa 2 de dYdX están desactivadas para las cuentas controladas por un `StarkProxy`.

#### **Poderes de Custodio**

El rol de custodio será controlado por la gobernanza de dYdX. Su función es garantizar la seguridad de los USDC prestados y permitir que sean devueltos a los inversores en caso de pérdida o uso indebido de la clave privada del prestatario.

El custodio puede tomar las siguientes acciones en cualquier momento (sujeto al bloqueo de tiempo):

* Restringir el endeudamiento y el depósito de USDC prestado a la bolsa.
* Repagar un saldo prestado usando USDC en el contrato de `StarkProxy`.
* Repagar un saldo en mora usando USDC en el contrato de `StarkProxy`.
* Transferir del contrato de StarkEx al contrato de `StarkProxy` (por ejemplo, como el segundo paso de un retiro lento de la bolsa).
* Cancelar una solicitud de operación forzada iniciada por el prestatario.
* Aprobar al prestatario para retirar una cantidad del contrato `StarkProxy` mientras elude la verificación de saldo.
* Actualizar el contrato inteligente.

**El custodio puede tomar las siguientes acciones si el prestatario tiene un saldo en mora pendiente (sujeto al bloqueo de tiempo):**

* Hacer un retiro forzado del Protocolo de la capa 2 de dYdX.
* Hacer una operación forzada (reducir-únicamente) en el Protocolo de la capa 2 de dYdX.

## Preguntas frecuentes de riesgos de participación

### ¿Cuáles son los riesgos de invertir en el fondo de participación de liquidez? ¿Qué sucede si un prestatario no paga los fondos prestados?

Un sistema de préstamos sin garantía requiere un estándar de confianza mucho más alto que el prestatario debe cumplir. Los proveedores de liquidez que toman prestado del grupo de participación de liquidez no pueden transferir fondos prestados fuera del sistema de participación de liquidez y el Protocolo de capa 2 de dYdX. Sin embargo, los USDC invertidos podrían perderse si un proveedor de liquidez perdiera la bolsa de fondos y no pudiese reponer sus asignaciones prestadas a través de fuentes de financiación externas.

En este caso, los fondos inactivos pueden estar sujetos a pérdidas socializadas como se establece a continuación en el caso de un déficit en el que un prestatario se atrasa en el pago de los fondos que se han solicitado para retirar. En caso de incumplimiento de los fondos prestados, un prestatario moroso enfrentará un daño significativo para su reputación.

Aunque cada participante y prestatario son parte del Acuerdo de crédito rotativo (enlace [aquí](https://dydx.foundation/revolving-credit-agreement)), este acuerdo no brinda una garantía de que los prestatarios pagarán sus obligaciones.

### ¿Cómo mantiene el contrato la solvencia?

En cualquier momento, el contrato estará en uno de los siguientes estados según la relación entre los saldos invertidos y los prestados:

![Contract Solvency](<.. /.gitbook/assets/image (41).png>)

Se dice que el contrato es **insolvente**:

* si el saldo total prestado es mayor que el saldo total activo;
* o equivalentemente, si el saldo total inactivo es mayor que el saldo total no prestado;
* o equivalentemente, si el saldo total de retirable es mayor que el saldo de USDC del contrato.

De lo contrario, se dice que el contrato es **solvente**.

Debido a que el préstamo se limita a la proporción asignada al prestatario de USDC activos, y puesto que el saldo inactivo solo puede aumentar entre etapas, el contrato generalmente solo puede pasar de un estado solvente a insolvente durante las transiciones realizadas entre etapas.

Si, al comienzo de una nueva etapa, el contrato es insolvente, ¿es importante reestabilizarlo lo antes posible? La solvencia se restaura a través de un mecanismo llamado "contabilidad de la deuda". Cuando el contrato sea insolvente, se puede utilizar la función `markDebt()` por cualquier persona, especificando una lista de prestatarios que hayan superado sus asignaciones. La cantidad por la cual el saldo prestado de un prestatario excede su asignación se llama la cantidad de déficit del prestatario.

Cuando se llama `markDebt()`, la cantidad de déficit de cada prestatario se elimina de su saldo prestado y a un saldo llamado saldo en mora. Al mismo tiempo, el total de estos montos faltantes se extrae de los saldos inactivos de los participantes y se distribuye como recibos de deuda de los inversores. El saldo inactivo de cada participante se reducirá y cada participante recibirá una cantidad equivalente en forma de deuda. De esta forma, la pérdida por insolvencia se socializa (prorratea) entre todos los interesados que mantienen saldos inactivos.

Este proceso se describe a continuación:

![Default](<.. /.gitbook/assets/image (46).png>)

### ¿Qué representa una deuda?

En caso de incumplimiento del prestatario, el monto del déficit (hasta el 100% de los saldos inactivos) pasa de ser un saldo inactivo a un saldo deudor (pérdida socializada entre los titulares de saldos inactivos). El saldo de la deuda de un inversor no le da derecho a retirarse del grupo de USDC invertidos debe devolverse específicamente a modo de reembolso de la deuda.

La deuda representa un recibo de USDC que luego se puede canjear por USDC, ya sea cuando el prestatario realiza un pago de la deuda o mediante otro medio de recuperación, según lo determine la gobernanza.

### Si un prestatario incumple, ¿qué recursos están disponibles para las partes interesadas?

Los interesados y los prestatarios son partes del Acuerdo de Crédito Rotatorio (enlace [aquí](https://dydx.foundation/revolving-credit-agreement)) que tiene como objetivo crear un acuerdo exigible entre cada interesado y cada prestatario. Además, el contrato inteligente de fondo de participación liquidez está diseñado para brindar a los participantes un recurso contra los prestatarios, aunque no puede garantizar el pago.

Cuando se utiliza un `markDebt()` en un prestatario, ese prestatario pierde el derecho a tomar prestados más fondos del contrato. Este derecho puede ser restablecido por la gobernanza.

Una vez que la deuda ha sido "marcada", se elimina del sistema principal de contabilidad y los participantes pueden recuperarla de varias maneras. Si el prestatario endeudado paga la deuda (o si otra parte, como la gobernanza, la paga en su nombre), entonces las partes interesadas a las que se les debía la deuda pueden recuperar los fondos por orden de llegada. Se pueden implementar soluciones más flexibles a través de la interfaz de "operador de deuda" en el contrato inteligente.

Lo que suceda en la práctica después de que las partes interesadas reciban la deuda dependerá del contexto. Si fue un error de un prestatario aprobado en buena fe, los participantes pueden esperar que se les pague rápidamente y en su totalidad. Si los fondos en USDC se perdieron, la gobernanza puede emitir un reembolso parcial a las partes interesadas afectadas. Si la resolución es incierta, el gobierno puede optar por emitir  a las partes afectadas un recibo ERC20, lo que les permite liquidez instantánea mientras esperan una resolución. Si lo considera apropiado, la gobernanza podría optar por emitir pagos de intereses a los titulares de recibos hasta que se llegue a una resolución.

Todos estos casos están respaldados fundamentalmente por el contrato de participación, pero la gobernanza de dYdX debe decidir y ejecutar la respuesta adecuada. Dependiendo de la situación, esto puede requerir que se redacte e implemente un contrato inteligente periférico.
