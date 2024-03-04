---
description: Visión general del programa de recompensas por operaciones.
---

# Recompensas por operaciones

`El 14,5` **`%`** (`144 693 506 $ethDYDX`) del suministro de tokens se asigna para distribuirse a los usuarios que operan en dYdX v3 según las tarifas pagadas. Inicialmente, el `25,0 %` del suministro de tokens (`250 000 000 $ethDYDX`) se asignó para recompensas de trading.

* En [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/8) para reducir las recompensas de trading en 25.0 %. Como resultado, la asignación de recompensas de trading bajó del `25,0 %` al `20,2 %`.
* En [DIP 20](https://dydx.community/dashboard/proposal/11), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/11) por reducir las recompensas de trading en otro 45,0 %. Como resultado, la asignación de recompensas de trading bajó del `20,2 %` al `14,5 %`.
*   En [DIP 29](https://dydx.community/dashboard/proposal/16), la comunidad dYdX [votó](https://dydx.community/dashboard/proposal/16) por reducir las recompensas de trading en ⅓ de la etapa 30 a 32 en dYdX v3 a los siguientes valores:

    * Etapa 30: 1 054 795 $ethDYDX
    * Etapa 31: 527 398 $ethDYDX
    * Etapa 32: 0 $ethDYDX

    Ten en cuenta que en DIP 29 la comunidad dYdX votó por migrar la asignación restante de las Recompensas de trading a la cadena dYdX para las Recompensas de trading.

Las recompensas de trading distribuidas en una etapa determinada se redujeron de 3 835 616 $ethDYDX a:

* 2 876 712 $ethDYDX en la etapa 15,
* 1 582 192 $ethDYDX en la etapa 21,
* 1 054 795 $ethDYDX en la etapa 30,
* 527 398 $ethDYDX en la etapa 31,
* 0 $ethDYDX a partir de la etapa 32.

Después de la etapa 31, no habrá recompensas de trading en dYdX v3. En [DIP 29](https://dydx.community/dashboard/proposal/16) en dYdX v3 y [la Propuesta 2](https://www.mintscan.io/dydx/proposals/2) en la cadena dYdX, la comunidad dYdX votó por acreditar la cantidad restante de $ethDYDX no otorgada en el [vester de Tesorería de recompensas](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) de dYdX v3 al [vester de Tesorería de recompensas de la cadena dYdX `(dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk) y posteriormente distribuirlas como recompensas de trading en la cadena dYdX, sujeto a la aprobación de la gobernanza en la cadena dYdX.

**Objetivos**

* Incentivar a todos los operadores a usar dYdX v3.
* Acelerar la liquidez del mercado y el uso de los productos en general.

## **Visión general**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Tarifas pagadas y recompensas estimadas en una etapa determinada</p></figcaption></figure>

Antes, $ethDYDX se distribuía a los operadores en función de las tarifas pagadas en dYdX v3. $ethDYDX se distribuyó en una etapa de 28 días durante cinco años y no está sujeto a ninguna adquisición de derechos ni bloqueo.

En [DIP 29](https://dydx.community/dashboard/proposal/16), la comunidad dYdX [votó](https://dydx.community/dashboard/proposal/16) por reducir las recompensas de trading en ⅓ de la etapa 30 a 32 en dYdX v3 a los siguientes valores:

* Etapa 30: 1 054 795 $ethDYDX
* Etapa 31: 527 398 $ethDYDX
* Etapa 32 y todas las etapas restantes: 0 $ethDYDX



<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ ,n=1,2..k $$

| Plazo | Definición |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Recompensa para un trader específico. |
| R | La recompensa total se dividirá entre todos los traders en el fondo para la etapa. |
| f | El total de las tasas pagadas por un trader en esta etapa. |
| w | Puntaje individual de trader. |
| $${\sum\limits _{n} w_{n}}$$ | Suma de todos los puntajes de cada trader. |
| k | Número total de traders en esta etapa. |

En el [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), la Comunidad de dYdX votó para simplificar la fórmula para que se basara en el total de las tarifas pagadas por un trader en una época dada.

## Preguntas frecuentes

### ¿Quién es elegible para las recompensas por operaciones?

Todos los traders en dYdX v3 eran elegibles para recibir $ethDYDX como recompensas de trading.

dYdX v3 no está disponible para los operadores en los Estados Unidos o en los territorios restringidos, tal como se define en los [Términos de uso](https://dydx.exchange/terms) de dYdX Trading Inc.

### ¿Cuántos $ethDYDX gané en el programa de Recompensas de trading?

En la época actual, los usuarios pueden ver las recompensas de trading pagadas y estimadas en [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) donde están los datos de trading de los usuarios.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Tarifas pagadas y recompensas estimadas en una etapa determinada</p></figcaption></figure>

Las recompensas de las etapas anteriores se pueden ver en [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### ¿Cómo reclamo mis recompensas de trading? ¿Cuándo puedo retirar y transferir mis $ethDYDX ganados?

Los tokens $ethDYDX ganados a través de las Recompensas de trading serán transferibles al final de cada etapa. Los titulares de tokens $ethDYDX deben esperar aproximadamente `7 días` (**período de espera**) después del final de la etapa para reclamar sus tokens $ethDYDX.

Después del período de espera de 7 días, cualquier miembro de la comunidad puede utilizar la función `Escribir` en el parámetro `updateRoot` (actualizar raíz) en el [contrato de Distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) para reclamar las recompensas de $ethDYDX.

Pasos:

1. En la página [de contrato del distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) en Etherscan, haz clic en la pestaña `Contrato` y selecciona `Escribir como proxy.`
2. Haz clic en el botón `Conectar a Web3` y conecta tu billetera Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Desplázate hasta el parámetro de `updateRoot` y haz clic en el botón `Escribir`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Esta transacción requeriría ETH para las tarifas de gas, y la transacción fallará si:**

* El período de espera de 7 días aún está en efecto, o
* Un miembro de la comunidad ya ha utilizado con éxito el parámetro `updateRoot` en el [contrato de distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Una vez finalizada la transacción, los traders pueden reclamar sus recompensas de trading  [aquí](https://dydx.community/dashboard). Los usuarios deberán hacer clic en `Reclamar`, firmar una transacción y pagar tarifas de gas para poder reclamar $ethDYDX.

![Visión general de la cartera de recompensas](../.gitbook/assets/1-portfolio-overview-rewards.png)
