---
description: Resumen de la arquitectura de gobernanza y los contratos inteligentes.
---

# Resumen técnico

## Resumen de la arquitectura de gobernanza

La gobernanza en la cadena de dYdX soporta las siguientes características:    

* Creación y votación en propuestas
* Participaciones de token instantáneas al comienzo de una propuesta
* Delegar la votación por separado y las facultades de la propuesta
* Establecimiento de umbrales de gobernanza que incluyen la propuesta, el quórum y los umbrales diferenciales de votos
* Sustitución del contrato inteligente de la “Estrategia de gobernanza”, que determina cómo se cuentan los votos
* Configuración de múltiples contratos de ejecución que permiten:
   * actualizaciones rápidas del protocolo y la distribución de fondos a través de ejecutores de bloqueo de corto tiempo;
   * Mejoras de gobernanza a través de ejecutores de bloqueo de largo tiempo.

Hay 6 contratos inteligentes que admiten la gobernanza de dYdX:

* **El contrato de `DydxToken`**: Mantiene capturas que respaldan las consultas para el poder de voto o propuesta de una dirección en cualquier número de bloque. Apoya la delegación separada de votos y las facultades de propuesta.
* **El contrato de `DydxGovernor`**: realiza un seguimiento de las propuestas y puede ejecutar propuestas a través de los contratos inteligentes de ejecutor.
* **Los contratos `de ejecutor`**: Puede poner en cola, cancelar y ejecutar transacciones votadas por Gobernanza. Si se aprueba una propuesta, las llamadas a función en la propuesta pueden ser ejecutadas por el contrato de Ejecutor especificado en la propuesta. Las transacciones en cola se pueden ejecutar después de un retraso, cuya duración está determinada en el contrato de ejecutor.
* **El** **contrato** **`de Bloqueo cronométrico de prioridad`**: Lo mismo que el contrato de bloqueo de tiempo, pero permite que un controlador de prioridad ejecute transacciones dentro del **período** prioritario (7 días) antes del final del retraso del bloqueo de tiempo.
* **El contrato `de estrategia de gobernanza`**: contiene la lógica para contar votos. Actualmente, cuenta los votos del Token de DYDX el módulo de seguridad. Se puede actualizar a través del bloqueo de tiempo prolongado.
* **El contrato `del módulo de seguridad`**: contiene la lógica para apostar tokens de DYDX, tokenizar una posición apostada y ganar recompensas, mientras conserva los derechos de votación y propuesta y las funciones de delegación de los tokens subyacentes.

{% pestañas %} {% título de la pestaña="Mainnet" %} | Contrato                             | Dirección                                |                    | ------------------------------------ | ------------------------------------------ | | DydxToken                           | 0x92D6C1e31e14520e676a687F0a93788B716BEff5  | | DydxGovernor                        | 0x7E9B1672616FF6D6629Ef2879419aE79A9018D2   | | Ejecutor de bloqueo de corto tiempo | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc | | Ejecutor de bloqueo de largo tiempo   | 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B |      |Ejecutor de bloqueo de tiempo Merkle-Pauser                 |0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52| | Ejecutor de bloqueo de tiempo de prioridad de Starkware | 0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE | |Tesorería de recompensas      | 0x639192D54431F8c816368D3FB4107Bc168d0E871 | | Tesorería comunitaria                | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b | | Módulo de seguridad           | 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC | | GovernanceStrategy                   | 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 | | Tesorería de recompensas Vester | 0xb9431E19B29B952d9358025f680077C3Fd37292f | | Tesorería comunitaria Vester         | 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 | | Distribuidor de Merkle          | 0x01d3348601968aB85b4bb028979006eac235a588 | | Adaptador de enlaces de cadena | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 | | Participación de liquidez    | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 | | Proxy de reclamos              | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e | | Gobernador auxiliar de StarkEx  | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a | | Gobernador de eliminación de StarkEx V2  |0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 | | Admin de proxy de tesorería de recompensas     | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d | | Admin de proxy de tesorería comunitaria      |0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 | | Admin de proxy de módulo de seguridad     | 0x6aD0BCfbD91963Cf2c8FB042091fd411FB05b3C | | Admin de proxy de distribuidor de Merkle     | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 | | Admin de proxy de liquidez           | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 | | StarkProxy \[0]                     | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 | | StarkProxy \[1]                     | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF | | StarkProxy \[2]                     | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 | | StarkProxy \[3]                     | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 | | StarkProxy \[4]                     | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 | | Admin de proxy de StarkProxy \[0]  | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 | | Admin de proxy de StarkProxy \[1]     | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 | | Admin de proxy de StarkProxy \[2]   | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 | | Admin de proxy de StarkProxy \[3]   | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA | | Admin de proxy de StarkProxy \[4]     | 0xfa45DCDbEc82C94082d283B62506320DB8632054 | {% endtab %} {% endtabs %}

## Código de fuente abierta y auditado

Todo el código fuente de contratos inteligentes para los contratos de gobernanza y los fondos de participación se pueden encontrar en [https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts).

El código fuente para el frontend de gobernanza alojado en dydx.community se puede encontrar [aquí](https://github.com/dydxfoundation/pnyx).

Todos los contratos inteligentes nuevos principales han sido auditados por Peckshield. No se encontraron problemas de seguridad significativos o de alta prioridad. Los contratos básicos de gobernanza y tokens se basan en los contratos de gobernanza de Aave que fueron auditados por [CertiK](https://www.certik.io/), [Certora](https://www.certora.com/) y [Peckshield](https://peckshield.com/en) y se han puesto a prueba en vivo en la red principal durante meses.

## Contratos básicos de gobernanza

![Las líneas rojas discontinuas indican que el contrato es actualizable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.17.43 PM (1).png>)

### DydxToken

El contrato de DydxToken está inspirado en Aave. El equipo de dYdX ha realizado cambios menores

DYDX se implementa en [0x92D6C1e31e14520e676a687F0a93788B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5) en la principal Ethereum. Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

### DydxGovernor

El contrato de DydxGovernor está inspirado en Aave. dYdX ha realizado cambios menores.

Gobernador se implementa en [0x7E9B1672616FF6D6629Ef2879419aE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2) en la red principal de Ethereum. Fue construido a partir de la comisión \[próximamente].

### Estrategia de Gobernanza

El contrato de Estrategia de Gobernanza está inspirado en Aave.

La estrategia se implementa en [0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9) en la red principal de Ethereum. Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

### Ejecutores

El contrato de ejecutor está inspirada en Aave. dYdX ha realizado cambios menores.

El **bloqueo de tiempo largo** se implementa en [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) en la red principal de Ethereum. Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

El **bloqueo de corto tiempo** se implementa en [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) en la red principal de Ethereum. Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

El **bloqueo de tiempo de Merkle** se implementa en [0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52) en la red principal de Ethereum. Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

El **bloqueo de tiempo de prioridad de Starkware** se implementa en [0xa306989BA6BcacdECCf3C0614FfF2B8C668e3Ca](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae), en la red principal de Ethereum.         Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

## Contratos de incentivos de DYDX

### Distribuidor Merkle

![Las líneas rojas discontinuas indican que el contrato es actualizable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.23.50 PM (1).png>)

El contrato inteligente de distribuidor Merkle distribuye recompensas de token de DYDX de acuerdo con un árbol de saldos de Merkle. El árbol se puede actualizar periódicamente con el saldo de recompensas acumulado de cada usuario, permitiendo que las nuevas recompensas se distribuyan a los con el tiempo.

Una actualización se realiza configurando la raíz de Merkle propuesta al último valor devuelto por el contrato de oráculos. La raíz de Merkle propuesta se puede hacer activa después de que haya transcurrido un período de espera. Durante el período de espera, la Gobernanza de dYdX tiene la oportunidad de congelar la raíz de Merkle, en caso de que la raíz propuesta sea incorrecta o maliciosa. Las actualizaciones de la raíz pueden ser utilizadas por ShortTimelockExecutor.

El contrato inteligente de Distribuidor de Merkle estaba inspirado en los diseños de Uniswap y Badger. El contrato inteligente se implementa en 0x01d3348601968aB85b4bb028979006eac235a588 en la red principal de Ethereum. Fue construido a partir de la comisión \[próximamente].

**ABI**

\[próximamente]

### Módulo de seguridad

![Las líneas rojas discontinuas indican que el contrato es actualizable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.24.45 PM (1).png>)

El módulo de seguridad es una reserva de participación que ofrece recompensas de DYDX a los usuarios que están apostando en DYDX con miras a la seguridad del Protocolo.

**ABI**

\[próximamente]

### Módulo de liquidez

![Las líneas rojas discontinuas indican que el contrato es actualizable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.25.30 PM (1).png>)

El módulo de liquidez es una colección de contratos inteligentes para apostar y pedir prestado, que incentivan la asignación de fondos USDC con fines de crear mercado en las operaciones de capa 2 de dYdX.

Los participantes ganan recompensas de DYDX por apostar en USD. Los fondos en juego pueden ser tomados prestados por ciertos socios previamente aprobados, de forma reputacional, sin garantía. Los fondos solo pueden ser utilizados en el intercambio de L2, esto se aplica a través del contrato de StarkProxy que interactúa con el contrato de intercambio perpetuo de StarkEx.

![Un diagrama del módulo de liquidez](<../.gitbook/assets/image (66).png>)

### StarkProxy

Este contrato permite al propietario tomar préstamos de LiquidityStaking y utilizar esos fondos en StarkPerpetual. Los fondos adicionales pueden ser depositados por el propietario, y cualquier fondo que exceda el monto prestado puede ser retirado libremente. Este contrato interactúa con el contrato de [StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual) escrito por Starkware y previamente auditado e implementado.

### Contratos de tesorería

![Las líneas rojas discontinuas indican que el contrato es actualizable](<../.gitbook/assets/Screen Shot 2021-09-03 at 5.26.09 PM (1).png>)

El contrato de TreasuryVester estaba inspirado en [Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol).

El Breve cronograma solo puede ejecutar acciones aprobadas por la gobernanza.

Hay dos vesters de tesorería y contratos de tesorería, uno es para recompensas de contratos de incentivo y el otro es para sostener fondos de tesorería de "propósito general".

Dado que la gobernanza controla cada tesorería, puede transferir fondos a cualquier dirección y/o aprobar cualquier dirección para gastar fondos de cualquiera de las tesorerías. Por ejemplo, los programas de recompensas necesitarán tener límites de aprobación de tokens establecidos por gobernanza.

Cada vester de tesorería ganará tokens linealmente en \~5 años (3 de agosto de 2021 - 3 de agosto de 2026) a la tesorería correspondiente.

## Contratos periféricos

### Chainlink Oracle-Powered Rewards (Recompensas de proveedores de operaciones y liquidez)

El objetivo de este sistema es calcular y publicar, a través de una red descentralizada de firmantes de oráculos, las recompensas de token de DYDX ganadas por los traders utilizando el intercambio de la capa 2 de dYdX. Las recompensas se almacenan en un árbol de Merkle, que contiene las recompensas acumuladas ganadas por cada usuario desde el inicio del programa de distribución. Cada época, la raíz de Merkle se actualiza en el contrato inteligente de MerkleDistributorV1 para reflejar las recompensas ganadas en la última época.

Hemos integrado con el sistema de Chainlink Oracle para publicar los datos de las recompensas en la cadena. Utilizamos IPNS para publicar los datos de operaciones que Chainlink utiliza para construir el árbol de Merkle. Mediante el uso de IPNS, podemos publicar los datos de operaciones para la última época bajo el mismo enlace de IPNS que en las épocas anteriores, lo que significa que la ubicación de los datos no cambiará.

Después de calcular las recompensas apropiadas de los datos de operaciones en bruto, Chainlink publica el árbol de recompensas de Merkle a IPFS. El CID de IPFS con los datos del árbol de Merkle se almacena en el contrato de distribuidor de Merkle junto con la raíz de Merkle para las recompensas de esa época.

El siguiente gráfico de flujo muestra la arquitectura de sistema de recompensas con energía de Chainlink Oracle-Powered Rewards:

![](<../.gitbook/assets/Merkle Distributor (1).png>)

### Otros activos

* Los activos de la marca de la Fundación dYdX están disponibles [**aquí**](https://dydx.foundation/brand)\*\*\*\*
