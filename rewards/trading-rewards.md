---
description: Visión general del programa de recompensas por operaciones.
---

# Recompensas por operaciones

`20,2`**`%` ** (20`1.883.560 $DYDX`) del suministro de tokens se asigna para distribuirse entre los usuarios que comercian en el protocolo de capa 2 de dYdX en función de las tarifas pagadas. Inicialmente, el`25,0 %` del suministro de tokens (`250 000 000 DYDX`) se asignó para recompensas de trading.

* En [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/8) para reducir las recompensas de trading en 25.0 %. Como resultado, la asignación de recompensas de trading bajó del `25,0 %` al `20,2 %`.
* En [DIP20](https://dydx.community/dashboard/proposal/11), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/11) para reducir las recompensas de trading en otro 45.0 %. Como resultado, la asignación de recompensas de trading bajó del `20,2 %` al `14,5 %`.

Las recompensas de trading distribuidas en una etapa dada se redujeron de 3 835 616 $DYDX a 2 876 712 $DYDX en la etapa 15, y de 2 876 712 $DYDX a 1 582 192 $DYDX en la etapa 21.

**Objetivos**

* Incentivar a todos los traders a utilizar el Protocolo de Capa 2 de dYdX.
* Acelerar la liquidez del mercado y el uso de los productos en general.

## **Visión general**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Tarifas pagadas y recompensas estimadas en una etapa determinada</p></figcaption></figure>

Se distribuirán $DYDX a los traders en función de las tarifas pagadas en el Protocolo de la capa 2 de dYdX. Los $DYDX serán distribuidos en una etapa de 28 días durante cinco años y no están sujetos a ningún tipo de adquisición o bloqueo. Se distribuirán 1 582 192 $DYDX por etapa.

Con la votación de la comunidad para proceder con una reducción del 25 % en las recompensas de trading en 958 904 $DYDX en [DIP16](https://dydx.community/dashboard/proposal/8), y otro 45 % en 1 294 520 $DYDX en [DIP20](https://dydx.community/dashboard/proposal/11), los 2 253 424 $DYDX restantes que se acumulan en el Fondo de Recompensas se pueden utilizar o dirigir por parte de la comunidad de dYdX con un [voto de gobernanza](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ ,n=1,2..k $$

| Plazo | Definición |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Recompensa para un trader específico. |
| R | La recompensa total se dividirá entre todos los traders en el fondo para la etapa. |
| f | El total de las tasas pagadas por un trader en esta etapa. |
| w | Puntaje individual de cada trader. |
| $${\sum\limits _{n} w_{n}}$$ | Suma de todos los puntajes de cada trader. |
| k | Número total de traders en esta etapa. |

En el [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), la Comunidad de dYdX votó para simplificar la fórmula para que se basara en el total de las tarifas pagadas por un trader en una época dada.

## Preguntas frecuentes

### ¿Quién es elegible para las recompensas por operaciones?

Todos los traders del protocolo de la Capa 2 de dYdX son elegibles para recibir $DYDX como recompensas de trading.

El Protocolo de la Capa 2 de dYdX no está disponible para los traders en los Estados Unidos o en los territorios restringidos, tal como se describe en los [Términos de uso de](https://dydx.exchange/terms) dYdX Trading Inc.

### ¿Cuántos DYDX gané en el programa de recompensas por operaciones?

En la época actual, los usuarios pueden ver las recompensas de trading pagadas y estimadas en [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) donde están los datos de trading de los usuarios.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Tarifas pagadas y recompensas estimadas en una etapa determinada</p></figcaption></figure>

Las recompensas de las etapas anteriores se pueden ver en [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### ¿Cómo reclamo mis recompensas de trading? ¿Cuándo puedo retirar y transferir mis $DYDX ganados?

Los tokens $DYDX ganados a través de las recompensas por trading serán transferibles al final de cada etapa. Los titulares de tokens $DYDX están obligados a esperar aproximadamente `7 días` (período de **espera**) después del final de la etapa para reclamar sus tokens $DYDX.

Después del período de espera de 7 días, cualquier miembro de la comunidad puede utilizar la función `Write` (escribir) en el parámetro `updateRoot` (actualizar raíz) en el [contrato de Distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) para reclamar las recompensas de DYDX.

Pasos:

1. En la página [de contrato del distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) en Etherscan, haz clic en la pestaña `Contrato` y selecciona `Escribir como proxy`.
2. Haz clic en el botón `Conectar a Web3` y conecta tu billetera Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Desplázate hasta el parámetro de `updateRoot` y haz clic en el botón `Escribir`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Esta transacción requeriría ETH para las tarifas de gas, y la transacción fallará si:**

* el periodo de espera de 7 días aún está en efecto; o
* Un miembro de la comunidad ya ha utilizado con éxito el parámetro `updateRoot` en el [contrato de distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Una vez finalizada la transacción, los traders pueden reclamar sus recompensas de trading  [aquí](https://dydx.community/dashboard). Los usuarios deberán hacer clic en `Reclamar`, firmar una transacción y pagar tarifas de gas para poder reclamar $DYDX.

![Visión general de la cartera de recompensas](../.gitbook/assets/1-portfolio-overview-rewards.png)
