---
description: Resumen del programa de recompensas de proveedores de liquidez.
---

# Recompensas de proveedores de liquidez

**El 3,2 %** del suministro inicial de tokens (`31 643 838 $ethDYDX`) se distribuirá entre los proveedores de liquidez (LP) en función de una fórmula que recompensa una combinación de volumen del Maker, tiempo de actividad, profundidad bilateral, diferenciales de oferta y demanda y cantidad de mercados admitidos. Inicialmente, **el 7,5 %** (`75 000 000 $ethDYDX`) del suministro de tokens se asignó para recompensas de proveedores de liquidez.

* En [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md), la comunidad dYdX [votó](https://dydx.community/dashboard/proposal/14) por reducir las recompensas de los proveedores de liquidez en un 50 %, de `1 150 685 $ethDYDX` por etapa a `575 343 $ethDYDX` por etapa. Como resultado, la asignación de recompensas de LP bajó del `7,5 %` al `5,2 %`.
*   En [DIP 29](https://dydx.community/dashboard/proposal/16), la comunidad dYdX [votó](https://dydx.community/dashboard/proposal/16) por reducir las recompensas de los proveedores de liquidez en ⅓ de la etapa 30 a 32 en dYdX v3 a los siguientes valores:

    * Etapa 30: 383 562 $ethDYDX
    * Etapa 31: 191 781 $ethDYDX
    * Etapa 32: 0 $ethDYDX

    Después de la etapa 31, no habrá recompensas para LP en dYdX v3. Como resultado, la asignación de recompensas a LP bajó del `5,2 %` al `3,2 %`.

Dado que no hay distribución de las recompensas de los proveedores de liquidez en la cadena dYdX, la comunidad dYdX en DIP 29 votó por migrar la asignación restante de las recompensas de los proveedores de liquidez a la Tesorería de la comunidad de la cadena dYdX.

**Objetivos**

* Mejorar la liquidez bilateral y recompensar programáticamente a los proveedores de liquidez.

## **Visión general**

Para incentivar la liquidez del mercado, $ethDYDX se distribuirá entre los proveedores de liquidez en función de una fórmula que recompensa la participación en los mercados, el volumen del Maker, la profundidad bilateral, el diferencial (frente al mercado medio) y el tiempo de actividad en dYdX v3. Cualquier dirección de Ethereum puede ganar estas recompensas, sujetas a un umbral de volumen mínimo del Maker del 0,25 % del volumen del Maker en la etapa anterior. $ethDYDX se distribuirá en una etapa de 28 días durante cinco años y no está sujeta a ninguna adquisición ni bloqueo.

Las siguientes funciones se utilizan para calcular la cantidad de $ethDYDX con los que se debe recompensar a cada proveedor de liquidez por etapa. En el [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), la comunidad de dYdX votó para revisar la fórmula de recompensas de LP al dividir las funciones para los mercados de BTC y ETH y los mercados que no son de BTC o ETH. En [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md), dYdX la comunidad votó para reasignar una ponderación de 0,05 stkDYDX a MakerVolume.

En general, la ponderación del volumen en las funciones se incrementó en todos los mercados. La cantidad de ethDYDX ganada es determinada por la participación relativa de los $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) de cada participante.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Se excluyen las órdenes por debajo de una determinada **profundidad mínima** (tamaño) ($$MinDepth$$) por mercado, y también se excluyen las órdenes por encima de un cierto **diferencial máximo** (diferencial de mercado medio) ($$MaxSpread$$).

El desempeño del proveedor de liquidez se monitorea y calcula minuto a minuto (mediante un muestreo aleatorio) y se agrega a un $$Q_{SCORE}$$ para un mercado determinado. Dado el muestreo minuto a minuto, cada época tiene 28 días \* 24 horas \* 60 minutos de puntos de datos: 40,320 puntos de datos por etapa en total.

Los proveedores de liquidez obtienen recompensas mensuales en función de su participación relativa de $$Q_{FINAL}$$ por etapa.

A continuación, la fórmula anterior se desglosa en cálculos paso a paso para obtener más detalles:

| _Volumen de creador_ | Volumen total de creador para la etapa |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>Supón que un proveedor de liquidez tiene varias órdenes de oferta abierta (1 BTC a $29 900, 5 BTC a $29 850, 10 BTC a $29 500) en el libro de órdenes de BTC-USD y BTC está actualmente a $30,000 (basado en el mercado medio). Supongamos que el MinDepth es de $ 5000 y MaxSpread frente al mercado medio es de $ 200, o 67 puntos básicos ($ 200/30,000). Un BP es la centésima de uno por ciento.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/3000}\right)) + (5\ \times \left(\frac{$29,850}{$150/300}\right))</span><p></p><br><span class="math">Q_{BID}</span> se calcula cada minuto utilizando un muestreo aleatorio.<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>Supongamos que un proveedor de liquidez tiene varias órdenes de compra abiertas (0,1 BTC a $ 30 100, 5 BTC a $ 30 150, 10 BTC a $ 30 175) en el libro de órdenes BTC-USD y BTC cotiza actualmente a $ 30 000 (basado en el mercado medio). Supongamos que el MinDepth es de $5,000 y MaxSpread frente al mercado medio es de $200, o 67 puntos básicos ($200/30,000). Un BP es la centésima de uno por ciento.<p></p><span class="math">1···Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))1</span><p></p><br><span class="math">Q_{ASK}</span> se calcula cada minuto en un intervalo aleatorio. |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p>Recompensa la liquidez bilateral tomando el mínimo de <span class="math">Q_{BID}</span> y <span class="math">Q_{ASK}</span>.<br><p></p>Se calcula cada minuto. |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$ es la suma de todos los $$Q_{MIN}$$ en una etapa determinada. |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$ es el tiempo en una etapa en que un creador de mercado determinado estuvo activo y cotizando tanto en el lado de la oferta como en el de la demanda, con órdenes con montos mayores que el mínimo por orden establecido (indicado abajo por el mercado) y diferenciales más pequeños que el máximo establecido diferencial (indicado abajo por el mercado). |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$ normaliza $$Q_{EPOCH}$$ para tener en cuenta el tiempo de actividad |

Cada mercado tendrá su propio fondo de recompensas que se calculará de manera diferente. En [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), la comunidad de dYdX votó para reducir la asignación de recompensas totales en BTC-USD y ETH-USDC al 10 % cada una. El conjunto inicial de ponderaciones aplicado a cada mercado es el siguiente:

| Mercado | % Asignación del grupo de recompensas totales |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | 10% |
| ETH-USD | 10 % |
| Otros mercados de perpetuals | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## Preguntas frecuentes

### ¿Quién es elegible para las recompensas de proveedores de liquidez?

Todos los proveedores de liquidez que hayan alcanzado un mínimo del 0,25 % del volumen del Maker en dYdX v3 en la etapa anterior son elegibles para recibir ethDYDX como recompensa en una etapa determinada.

dYdX v3 no está disponible para los proveedores de liquidez en los Estados Unidos o en los territorios restringidos, tal como se define en los [Términos de uso](https://dydx.exchange/terms) de dYdX Trading Inc.

### ¿Cuántos $ethDYDX gané en el programa de Recompensas a proveedores de liquidez?

En una etapa determinada, los proveedores de liquidez obtienen un rendimiento en función de su $$Q_{SCORE}$$ relativo en el mercado de un par determinado. Cada par tiene su propia cantidad de recompensas relativas establecidas por la gobernanza. La cantidad esperada de ethDYDX ganada se muestra en el [Panel de recompensas de LP](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) y se puede determinar en función de la cantidad de proveedores de liquidez involucrados, el $$Q_{SCORE}$$ relativo y la cantidad de la recompensa disponible para un determinado par.

### ¿Cómo reclamo mis recompensas de proveedores de liquidez?

Las recompensas de proveedores de liquidez se muestran en la [API de dYdX](https://docs.dydx.exchange/). Aunque no aparecen en la interfaz de usuario de gobernanza, todavía se pueden reclamar a través de la gobernanza al final de cada etapa [aquí](https://dydx.community/dashboard).

### ¿Cuándo puedo retirar y transferir mis Recompensas de proveedores de liquidez en $ethDYDX canjeadas?

Los tokens $ethDYDX recompensados a través de las Recompensas de Proveedores de Liquidez serán reclamables y transferibles una vez que el período de restricción de transferencia inicial sea levantado.

A partir de la etapa 1, los tokens $ethDYDX recompensados a través de las Recompensas de proveedores de liquidez se podrán canjear `7 días` (**período de espera**) después del final de cada etapa.

### A partir de la etapa 1, los tokens DYDX recompensados a través de Recompensas de Proveedores de Liquidez se podrán reclamar 7 días (período de espera) después del final de cada etapa.

**Profundidad bilateral**

Un proveedor de liquidez bilateral es una empresa o individuo que cotiza activamente mercados bilaterales en dYdX v3, suministrando ofertas y demandas para un mercado determinado. Proporcionan liquidez al protocolo en general.

Por ejemplo, un proveedor de liquidez en el mercado BTC-USD puede ofrecer una cotización de $30,000-$30,100, 10x50. Esto significa que ofertan (comprarán) 10 BTC por $30,000 y también ofrecen (venderán) 50 BTC por $30,100. Otros participantes del mercado pueden entonces comprar (elevar la oferta) del proveedor de liquidez a $30,100 o venderles (golpear la oferta) a $30,000.

Los proveedores de liquidez se evalúan en función de su capacidad para ofrecer ofertas y demandas en un mercado determinado. Los proveedores de liquidez que solo cotizan en 1 lado (ya sea solo ofertas o demandas) están excluidos de recibir recompensas debido a la función min().

**Diferencial del mercado medio**

Una medida común de la liquidez es el diferencial de oferta y demanda: el diferencial entre el precio de oferta más alto (orden de compra) y el precio de venta más bajo (orden de venta) en un mercado. La diferencia entre la oferta y la demanda y el diferencial, es el principal costo de transacción de la negociación (fuera de las comisiones), y lo cobra el proveedor de liquidez mediante el procesamiento de órdenes a los precios de oferta y demanda. El diferencial mide el costo de realizar transacciones de inmediato para un usuario.

El diferencial del mercado medio toma específicamente el punto medio del mercado. Con esta fórmula, también se excluyen las órdenes por debajo de la cantidad de MinDepth para cada mercado.

Por ejemplo, si el precio de oferta de un proveedor de liquidez para BTC-USD es de $30,000 y el precio de venta es de $30,100, el diferencial de oferta y demanda es de $100. El precio del mercado medio es de $30,050 y el diferencial del mercado medio es de $50.

**Tiempo de actividad**

El tiempo de actividad del proveedor de liquidez es fundamental para los mercados, especialmente en períodos de alta volatilidad. Al aplicar un exponente de 5 a $$Uptime_{epoch}$$ como aporte a $$Q_{FINAL}$$, las recompensas se desvían hacia los proveedores de liquidez que mantienen constantemente la liquidez bilateral. En otras palabras, un proveedor de liquidez que brinda tiempo de actividad el 99% del tiempo es exponencialmente más valioso que un proveedor de liquidez que brinda el 90% de tiempo de actividad.

El tiempo de actividad se define como el porcentaje de tiempo que las órdenes están en un mercado determinado proporcionando liquidez minuto a minuto (con muestreo aleatorio). El tiempo de actividad excluye los períodos de tiempo en los que existen interrupciones en el propio protocolo de Capa 2 de dYdX. Puede haber casos extremos en los que la operación sea lenta o no acepte órdenes (pero no es una interrupción), en cuyo caso lo anterior no se aplicaría (pero eso se consideraría un error y todos los proveedores de liquidez se verían afectados de manera similar, como con las interrupciones).

### ¿Cómo se definen los diferenciales máximos por mercado?

No se generarán $$Q_{BID}$$ ni $$Q_{ASK}$$ cuando el diferencial esté por encima del $$MaxSpread$$ de un mercado determinado.

Los diferenciales máximos iniciales son los siguientes:

| Mercado | Máximo diferencial vs Mercado medio (oferta y demanda) |
| ----------------------- | -------------------------------------- |
| BTC-USD | 20 bps |
| ETH-USD | 20 bps |
| Otros mercados de perpetuals | 40 bps |

### ¿Cómo se define la profundidad mínima (tamaño) por mercado?

No se generarán ni $Q_{BID}$$ ni $Q_{ASK}$$ cuando el tamaño esté por debajo de los $MinDepth$$.

Las profundidades mínimas iniciales son las siguientes:

| **Mercado** | **Profundidad mínima (oferta y demanda)** |
| ----------------------- | --------------------------- |
| BTC-USD | $5,000 |
| ETH-USD | $5,000 |
| Otros mercados de perpetuals | $1,000 |
