---
description: Visión general del programa de recompensas por operaciones.
---

# Recompensas por operaciones



* En [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/8) para reducir las recompensas de trading en 25.0 %. Como resultado, la asignación de recompensas de trading bajó del `25,0 %` al `20,2 %`.
* En [DIP20](https://dydx.community/dashboard/proposal/11), la comunidad de dYdX [votó](https://dydx.community/dashboard/proposal/11) para reducir las recompensas de trading en otro 45.0 %. Como resultado, la asignación de recompensas de trading bajó del `20,2 %` al `14,5 %`.



**Objetivos**

*
* Acelerar la liquidez del mercado y el uso de los productos en general.

## **Visión general**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Tarifas pagadas y recompensas estimadas en una etapa determinada</p></figcaption></figure>





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





###

En la época actual, los usuarios pueden ver las recompensas de trading pagadas y estimadas en [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) donde están los datos de trading de los usuarios.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Tarifas pagadas y recompensas estimadas en una etapa determinada</p></figcaption></figure>

Las recompensas de las etapas anteriores se pueden ver en [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### ¿Cómo reclamo mis recompensas de trading?





Pasos:

1. En la página [de contrato del distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) en Etherscan, haz clic en la pestaña `Contrato` y selecciona `Escribir como proxy.`
2. Haz clic en el botón `Conectar a Web3` y conecta tu billetera Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Desplázate hasta el parámetro de `updateRoot` y haz clic en el botón `Escribir`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Esta transacción requeriría ETH para las tarifas de gas, y la transacción fallará si:**

* El período de espera de 7 días aún está en efecto, o
* Un miembro de la comunidad ya ha utilizado con éxito el parámetro `updateRoot` en el [contrato de distribuidor de Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Una vez finalizada la transacción, los traders pueden reclamar sus recompensas de trading  [aquí](https://dydx.community/dashboard).

![Visión general de la cartera de recompensas](../.gitbook/assets/1-portfolio-overview-rewards.png)
