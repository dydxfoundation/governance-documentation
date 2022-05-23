---
description: Visión general del programa de recompensas por operaciones.
---

# Recompensas por operaciones

`El 25,00%` del suministro inicial de tokens (`250,000,000 DYDX`) se distribuirá a los usuarios que operen bajo el Protocolo de Capa 2 de dYdX basado en una combinación de tasas pagadas y de intereses abiertos.

**Objetivos**

* Incentivar a todos los traders a utilizar el Protocolo de Capa 2 de dYdX.
* Acelerar la liquidez del mercado y el uso de los productos en general.

## **Visión general**

![Gana recompensas al realizar operaciones en el protocolo de Capa 2 de dYdX](<../.gitbook/assets/image (17).png>)

DYDX se distribuirá a los traders según una fórmula que recompensa una combinación de tarifas pagadas e interés abierto en el Protocolo de Capa 2 de dYdX. Los DYDX serán distribuidos en una etapa de 28 días durante cinco años y no están sujetos a ningún tipo de adquisición o bloqueo. Se distribuirán 3,835,616 DYDX por etapa.

La función Cobb-Douglas se usa para calcular cuántos DYDX se otorgarán a cada trader durante cada época:

![](../.gitbook/assets/math-20211221.png)

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ ,n=1,2..k $$

| Plazo | Definición |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| r | Recompensa para un trader específico. |
| R | La recompensa total se dividirá entre todos los traders en el fondo para la etapa. |
| f | El total de las tasas pagadas por un trader en esta etapa. |
| w | Puntaje individual de trader. |
| $${\sum\limits _{n} w_{n}}$$ | Suma de todas las puntuaciones de cada trader. |
| d | El interés abierto promedio de un trader (medido por minuto) en todos los mercados durante esta etapa. |
| k | Número total de traders en esta etapa. |
| g | El stkDYDX promedio obtenido por un trader (medido aleatoriamente por minuto) a lo largo de la etapa |
| a | 0,80 |
| b | 0,15 |
| c | 0,05 |

En [DIP-10](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-10.md), la Comunidad de dYdX votó a favor de cambiar el peso del parámetro de la tasa de `a = 0,67` a `a = 0,8` y de disminuir el parámetro del interés abierto de `b = 0,28` a `b = 0,15.`

## Preguntas frecuentes

### ¿Quién es elegible para las recompensas por operaciones?

Todos los traders en el protocolo de Capa 2 de dYdX son elegibles para recibir DYDX como recompensas por operaciones.

El Protocolo de la Capa 2 de dYdX no está disponible para los traders en los Estados Unidos o en los territorios restringidos, tal como se describe en los [Términos de uso de](https://dydx.exchange/terms) dYdX Trading Inc.

### ¿Cuántos DYDX gané en el programa de recompensas por operaciones?

En la etapa actual, los usuarios pueden ver las tarifas pagadas, el interés abierto promedio y las recompensas comerciales estimadas en [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) donde se encuentran los datos de operaciones de los usuarios.

![Información sobre las recompensas para la etapa actual](<../.gitbook/assets/image (18).png>)

Las recompensas de las etapas anteriores se podrán ver en [**dydx.community/history/rewards**](https://dydx.community/history/rewards) **** (próximamente).

### ¿Cómo reclamo mis recompensas por operaciones? ¿Cuándo puedo retirar y transferir mis DYDX ganados?

Los tokens DYDX ganados a través de las recompensas por operaciones serán transferibles al final de cada etapa. Los titulares de tokens DYDX están obligados a esperar aproximadamente `7 días` (período de **espera**) después del final de la etapa para reclamar sus tokens. Una vez que se han reclamado los tokens, se pueden utilizar para la gobernanza de dYdX.

Los traders pueden reclamar sus recompensas comerciales al final de cada época, después del **período** de espera [aquí](https://dydx.community/dashboard)

Los usuarios tendrán que hacer clic en "Reclamo", firmar una transacción y pagar las tasas de gas para reclamar sus DYDX.

![Visión general de la cartera de recompensas](<../.gitbook/assets/image (20).png>)

### ¿Qué es un interés abierto?

El interés abierto total es el valor en USD de todas las posiciones largas o cortas pendientes (las unidades totales de posiciones largas siempre equivalen a las unidades totales de posiciones cortas) para un mercado determinado. El aumento del interés abierto representa la entrada de dinero nuevo o adicional en el mercado, mientras que la disminución del interés abierto indica que el dinero sale del mercado.

A continuación se muestra una tabla de actividad de operaciones para los traders, A, B, C, D y E. El interés abierto se calcula en términos de USDC, de acuerdo a la actividad comercial de cada día:

=======
| ${\sum\limits &lt;g id="1" ctype="italic" equiv-text="_"&gt;{n} w</g>{n}} | Suma de todas las puntuaciones de cada trader. |
| d | El interés abierto promedio de un trader (medido por minuto) en todos los mercados durante esta etapa. |
| k | Número total de traders en esta etapa. |
| g | El stkDYDX promedio obtenido por un trader (medido aleatoriamente por minuto) a lo largo de la etapa |
| a | 0,67 |
| b | 0,28 |
| c | 0,05 |

## Preguntas frecuentes

### ¿Quién es elegible para las recompensas por operaciones?

Todos los traders en el protocolo de Capa 2 de dYdX son elegibles para recibir DYDX como recompensas por operaciones.

El Protocolo de la Capa 2 de dYdX no está disponible para los traders en los Estados Unidos o en los territorios restringidos, tal como se describe en los [Términos de uso de](https://dydx.exchange/terms) dYdX Trading Inc.

### ¿Cuántos DYDX gané en el programa de recompensas por operaciones?

En la etapa actual, los usuarios pueden ver las tarifas pagadas, el interés abierto promedio y las recompensas comerciales estimadas en [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) donde se encuentran los datos de operaciones de los usuarios.

![Rewards info for the current epoch](<.. /.gitbook/assets/image (18).png>)

Las recompensas de las etapas anteriores se podrán ver en [**dydx.community/history/rewards**](https://dydx.community/history/rewards) **** (próximamente).

### ¿Cómo reclamo mis recompensas por operaciones? ¿Cuándo puedo retirar y transferir mis DYDX ganados?

Los tokens DYDX ganados a través de las recompensas por operaciones serán transferibles al final de cada etapa. Los titulares de tokens DYDX están obligados a esperar aproximadamente `7 días` (período de **espera**) después del final de la etapa para reclamar sus tokens. Una vez que se han reclamado los tokens, se pueden utilizar para la gobernanza de dYdX.

Los traders pueden reclamar sus recompensas comerciales al final de cada época, después del **período** de espera [aquí](https://dydx.community/dashboard)

Los usuarios tendrán que hacer clic en "Reclamo", firmar una transacción y pagar las tasas de gas para reclamar sus DYDX.

![Portfolio overview of rewards](<.. /.gitbook/assets/image (20).png>)

### ¿Qué es un interés abierto?

El interés abierto total es el valor en USD de todas las posiciones largas o cortas pendientes (las unidades totales de posiciones largas siempre equivalen a las unidades totales de posiciones cortas) para un mercado determinado. El aumento del interés abierto representa la entrada de dinero nuevo o adicional en el mercado, mientras que la disminución del interés abierto indica que el dinero sale del mercado.

A continuación se muestra una tabla de actividad de operaciones para los traders, A, B, C, D y E. El interés abierto se calcula en términos de USDC, de acuerdo a la actividad comercial de cada día:

| Tiempo | Actividad de operaciones | Interés abierto total por red (USDC) |
| ------- | -------------------------------------------------------------------------- | ------------------------------ |
| 1 de julio | **El trader A** compra 1 BTC a $30,000 y **el trader B** vende 1 BTC a $30,000 | $30,000 |
| 3 de julio | **El trader C** compra 5 BTC a $30,000 y **el trader D** vende 5 BTC a $30,000 | $180,000 |
| 5 de julio | **El trader A** vende 1 BTC a $30,000 y **el trader D** compra 1 BTC a $30,000 | $150,000 |
| 10 de julio | **El trader E** compra 5 BTC a $30,000 y **el trader C** vende 5 BTC a $30,000 | $150,000 |

En el contexto de la fórmula para obtener **Recompensas por Operaciones**, el interés abierto se mide cada minuto (en un momento aleatorio por minuto) en todos los mercados y se promedia en una etapa determinada para calcular las recompensas.

El propio interés abierto de un trader es el valor de USD de todas las posiciones abiertas de ese mismo trader. A los efectos de **obtener Recompensas por Operaciones**, el interés abierto de un comerciante se mide cada minuto (en un momento aleatorio por minuto) en todos los mercados y se promedia en una etapa determinada.
