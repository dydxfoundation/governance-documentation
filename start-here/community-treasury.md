---
description: Una visión general de la Tesorería de la comunidad.
---

# Tesorería de la comunidad

**`El 24.2 %`** (`241 735 862 $DYDX`) del suministro de tokens se asigna a la tesorería de la comunidad para que la comunidad dYdX lo use de forma continua para subvenciones de contribuyentes, iniciativas comunitarias, minería de liquidez y otros programas. Inicialmente, el `5,0 %``` del suministro de tokens ([50 000 000 $DYDX](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations)) se asignó a la Tesorería de la comunidad y 766 703 $DYDX se invierten en la Tesorería de la comunidad en cada etapa. Actualmente, 3 787 251 $DYDX se invierten en la tesorería de la comunidad porque tres propuestas de gobernanza dieron como resultado un aumento de 3 020 548 $DYDX en la cantidad de $DYDX disponible para la comunidad de dYdX en cada época:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - fija las recompensas por la inversión de USDC en 0 (383 562 $DYDX por etapa);
* [DIP 16](https://dydx.community/dashboard/proposal/8) - reduce las recompensas de trading en un 25 % (958 904 $DYDX por etapa);
* [DIP 17](https://dydx.community/dashboard/proposal/9) - fija las recompensas por invertir $DYDX en 0 (383 562 $DYDX por etapa),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - reduce aún más las recompensas de trading en un 45 % (1 294 520 $DYDX por etapa), y
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md): reduce las recompensas de proveedores de liquidez en un 50 % (575 342 $DYDX por etapa).



**Objetivos**

* Financiar programas e iniciativas que impulsen el crecimiento de dYdX.
* Desarrollar programas de subvenciones para financiar NFT comunitarios, hackatones, paneles de análisis, memes, obsequios, herramientas de terceros, traducciones y otros proyectos.
* Desarrollar un sistema de gobernanza de primer nivel e incentivar una gobernanza sólida.

## Resumen general

La Tesorería de la comunidad retendrá $DYDX para usarlos según lo decidan los titulares de $DYDX, ya sea para subvenciones, nuevos fondos de minería de liquidez o cualquier otro programa. Los $DYDX se otorgarán a la Tesorería de la comunidad de manera continua en el transcurso de cinco años. Se requerirá un voto de gobernanza para gastar cualquier $DYDX de la Tesorería de la comunidad.

Si, después de cinco años, la gobernanza decide promulgar la inflación de los perpetuals (a una inflación anual máxima del `2 %`), cualquier $DYDX recién acuñado estará disponible para la Tesorería de la comunidad.

## Preguntas frecuentes

### ¿Cómo se invierten $DYDX en la Tesorería de la comunidad?

Cada segundo, el Otorgante de la Tesorería de la comunidad (ver detalles [aquí](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) otorga [`0,3169242627`](tel:03169242627) $DYDX a la Tesorería de la comunidad. Una vez que se han otorgado los $DYDX, la solicitud de la función de `reclamación` al Otorgante de la Tesorería de la comunidad hará que se transfieran los $DYDX invertidos a la Tesorería de la comunidad. Cualquier miembro de la comunidad dYdX puede utilizar la función `claim` (reclamo) en Etherscan [aquí](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) (lo que requeriría ETH para las tarifas de gas) para transferir el $DYDX invertido del Otorgante de la Tesorería de la comunidad a la Tesorería de la comunidad.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### ¿Cuál es el balance invertido de la Tesorería de la comunidad?

Los miembros de la comunidad dYdX pueden ver el balance invertido de la Tesorería de la comunidad [aquí](https://dydx.shippooor.xyz/)\\. Además, la Fundación dYdX publica el balance invertido de la Tesorería de la comunidad en la [Revisión de la etapa](https://dydx.foundation/blog) al final de cada etapa. Además del dYdX invertido en el Fondo de la comunidad, la comunidad de dYdX también puede acceder al $DYDX que se acumula en el Fondo de Recompensas como resultado de los votos a:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - fija las recompensas por la inversión de USDC en 0 (383 562 $DYDX por etapa);
* [DIP 16](https://dydx.community/dashboard/proposal/8) - reduce las recompensas de trading en un 25 % (958 904 $DYDX por etapa);
* [DIP 17](https://dydx.community/dashboard/proposal/9) - fija las recompensas por invertir $DYDX en 0 (383 562 $DYDX por etapa),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - reduce aún más las recompensas de trading en un 45 % (1 294 520 $DYDX por etapa), y
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md): reduce las recompensas de proveedores de liquidez en un 50 % (575 342 $DYDX por etapa).

A partir de la etapa 26, 3 595 890 $DYDX se acumularán en la Tesorería de Recompensas en cada etapa y estos podrán ser utilizados por la comunidad de dYdX con un [voto de gobernanza](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

### ¿Quién puede presentar propuestas para gastar $DYDX de la Tesorería de la comunidad?

Cualquier usuario con poder de propuesta suficiente puede presentar propuestas. Se requerirá un voto de gobernanza para gastar cualquier $DYDX de la Tesorería de la comunidad. Para enviar una propuesta, envía una propuesta de mejora de dYdX (DIP) tal como se describe en el [ciclo de vida de la propuesta de DIP](../voting-and-governance/dip-proposal-lifecycle.md).

### ¿Cómo se construye una propuesta para gastar fondos de la Tesorería de la comunidad?

Reverie ha elaborado una completa y detallada guía técnica sobre cómo cada miembro de la comunidad dYdX con más de 5 M de $DYDX ([umbral de propuesta](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) para un [voto de bloqueo de tiempo corto](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) de poder de propuesta puede crear una propuesta para transferir $DYDX de la Tesorería de la comunidad a una dirección de destino. Haz clic [aquí](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) para acceder a la guía técnica.

### ¿Qué tipos de propuestas pueden enviarse a la Tesorería de la comunidad?

Una tesorería administrada por la comunidad ofrece un mundo de posibilidades. Esperamos ver varios experimentos e iniciativas, incluidas las subvenciones de ecosistema, que pueden fomentar el crecimiento de los ecosistemas de la Capa 2 de dYdX.
