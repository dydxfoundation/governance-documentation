---
description: Visão geral da arquitetura de governança e contratos inteligentes.
---

# Visão geral técnica

## Visão geral de arquitetura de governança

A governança on-chain da dYdX fornece as seguintes funcionalidades:

* Criação e votação de propostas
* Criação de snapshots de tokens no início de uma proposta
* Delegação separada para poderes de voto e de proposição
* Definição de limites de governança, incluindo proposições, quórum e limites de diferenciais de voto
* Substituição do contrato inteligente de “estratégia de governança”, que determina como os votos são contados
* Configuração de vários contratos de execução que permitem:
   * melhorias de protocolo e distribuição de fundos rápidas por meio de executores de timelock curto;
   * atualizações de governança por meio de executores de timelock longo.

Existem seis contratos inteligentes que aceitam a governança da dYdX:

* **O contrato `DydxToken`**: mantém snapshots que permitem consultas de voto de um endereço ou poder de proposição em qualquer número de bloco. Permite a delegação separada para poderes de voto e de proposição.
* **O contrato `DydxGovernor`**: rastreia propostas e as executa por meio de contratos inteligentes de executor.
* **Os contratos `de executor`**: criam filas, cancelam e executam transações votadas pela Governança. Se uma proposta for aprovada, as funções de chamada na proposta podem ser executadas pelo contrato de execução especificado na proposta. As transações em fila podem ser executadas após um atraso, cuja duração é determinada pelo contrato de execução.
* ******Contrato** de **`timelock de prioridade`**: o mesmo que o contrato de timelock, mas que permite que um controlador de prioridade execute transações dentro do **período de prioridade** (7 dias) antes do fim do atraso de timelock.
* **Contrato de `estratégia de governança`**: contém a lógica da contagem de votos. Atualmente, conta votos a partir do token DYDX e do módulo de segurança. Pode ser atualizado por meio de timelock longo.
* **O contrato `de módulo de segurança`**: contém a lógica de stake para tokens DYDX, tokeniza posições em stake e recebe recompensas, ao passo que mantém os direitos de voto e de proposição, além das funções de delegação dos tokens.

{% tabs %}
 {% tab title="Mainnet" %}
 | Contrato                             | Endereço                                    | | ------------------------------------ | ------------------------------------------ |
 | DydxToken                            | 0x92D6C1e31e14520e676a687F0a93788B716BEff5 |
 | DydxGovernor                         | 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 |
 | Executor de timelock curto              | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc |
 | Executor de timelock longo               | 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B |
 | Executor de timelock Merkle-Pauser      | 0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52 |
 | Executor de timelock de prioridade Starkware | 0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE |
 | Tesouro de recompensas                     | 0x639192D54431F8c816368D3FB4107Bc168d0E871 |
 | Tesouro da Comunidade                   | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b |
 | Módulo de Segurança                        | 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC |
 | GovernanceStrategy                   | 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 |
 | Investidor do Tesouro de Recompensas              | 0xb9431E19B29B952d9358025f680077C3Fd37292f |
 | Investidor do Tesouro da Comunidade            | 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 |
 | Distribuidor Merkle                   | 0x01d3348601968aB85b4bb028979006eac235a588 |
 | Adaptador Chainlink                    | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 |
 | Staking de Liquidez                    | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 |
 | Proxy de Resgates                         | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e |
 | Governador do Assistente StarkEx              | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a |
 | Governador de Remoção StarkEx V2          | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 |
 | Administrador do Proxy do Tesouro de Recompensas         | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d |
 | Administrador do Proxy do Tesouro da Comunidade       | 0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 |
 | Administrador do Proxy do Módulo de Segurança            | 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C |
 | Administrador do Proxy do Distribuidor Merkle       | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 |
 | Administrador do Proxy de Staking de Liquidez        | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 |
 | StarkProxy \[0]                      | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 |
 | StarkProxy \[1]                      | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF |
 | StarkProxy \[2]                      | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 |
 | StarkProxy \[3]                      | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 |
 | StarkProxy \[4]                      | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 |
 | Administrador do Proxy StarkProxy \[0]          | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 |
 | Administrador do Proxy StarkProxy \[1]          | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 |
 | Administrador do Proxy StarkProxy \[2]          | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 |
 | Administrador do Proxy StarkProxy \[3]          | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA |
 | Administrador do Proxy StarkProxy \[4]          | 0xfa45DCDbEc82C94082d283B62506320DB8632054 |
 {% endtab %}
 {% endtabs %}

## Código aberto e auditado

Todo o código-fonte do contrato inteligente para os contratos de governança e pools de staking pode ser encontrado em [https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts).

O código-fonte do frontend de governança hospedado na dydx.community pode ser encontrado [aqui](https://github.com/dydxfoundation/pnyx).

Todos os principais novos contratos inteligentes foram auditados pela Peckshield. Não foram encontrados problemas de segurança significativos nem de alta prioridade. A principal governança e os contratos de token são derivados dos contratos de governança da Aave, que foram auditados pelos [CertiK](https://www.certik.io), [Certora](https://www.certora.com) e [Peckshield](https://peckshield.com/en) e foram testados pela mainnet por meses.

## Contratos de governança principal

![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.17.43 PM.png>)

### DydxToken

O contrato DydxToken foi inspirado pela Aave. Pequenas alterações foram feitas pela equipe da dYdX.

O DYDX está implantado em [0x92D6C1e31e14520e676a687F0a93788B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5) na mainet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

### DydxGovernor

O contrato DydxGovernor foi inspirado pela Aave. Pequenas alterações foram feitas pela dYdX.

O Governador está implantado em [0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2) na mainnet Ethereum. Criado a partir do commit \[em breve].

### GovernanceStrategy

O contrato GovernanceStrategy foi inspirado pela Aave.

O GovernanceStrategy foi implantado em [0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9) na mainnet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

### Executores

O contrato de execução foi inspirado pela Aave. Pequenas alterações foram feitas pela dYdX.

O **contrato de timelock longo** está implantado em [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) na mainnet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

O **contrato de timelock curto** está implantado em [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) na mainnet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

O **timelock Merkle** está implantado em [0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52) na mainnet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

O **contrato de timelock de prioridade Starkware** está implantado em [0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae) na mainnet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

## Contratos de incentivos DYDX

### Distribuidor Merkle



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.23.50 PM.png>)

O contrato inteligente Merkle distribui recompensas de token DYDX de acordo com uma árvore de Merkle de saldos. A árvore pode ser atualizada periodicamente com o saldo de recompensa cumulativo de cada usuário, permitindo que novas recompensas sejam distribuídas aos usuários ao longo do tempo.

Uma atualização é realizada definindo a raiz Merkle proposta para o valor mais recente retornado pelo contrato oracle. A raiz Merkle proposta pode ser ativada uma vez que o período de espera expire. Durante o período de espera, a Governança dYdX pode congelar a raiz Merkle, caso a raiz proposta se mostre incorreta ou maliciosa. As atualizações de raiz podem ser retomadas com o ShortTimelockExecutor.

O contrato inteligente Merkle foi inspirado por projetos como Uniswap e Badger. O contrato inteligente está implantado em 0x01d3348601968aB85b4bb028979006eac235a588 na mainnet Ethereum. Criado a partir do commit \[em breve].

**ABI**

\[em breve]

### Módulo de segurança



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.24.45 PM.png>)

O Módulo de Segurança é um pool de staking que oferece recompensas DYDX aos usuários que façam o stake de DYDX com vistas para a segurança do protocolo.

**ABI**

\[em breve]



### Módulo de liquidez



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.25.30 PM.png>)

O Módulo de Liquidez é uma coleção de contratos inteligentes para o staking e empréstimos, que incentivam a alocação de fundos em USDC para fins de criação de mercado na exchange dYdX Layer 2.

Os stakers ganham recompensas DYDX ao fazerem o staking de USDC. Os fundos em staked podem ser emprestados por certos parceiros pré-aprovados com base em reputação e sem garantia. Os fundos só podem ser usados na exchange L2, isto é aplicado por meio do contrato StarkProxy que interage com o contrato da Exchange StarkEx Perpetual.

![A diagram of the Liquidity module](<.. /.gitbook/assets/image (66).png>)

### StarkProxy

Este contrato permite que o proprietário empreste fundos da LiquidityStaking e use-os na StarkPerpetual. Fundos adicionais podem ser depositados pelo proprietário, e quaisquer fundos que excedam o valor emprestado podem ser retirados livremente. Este contrato interage com o contrato [StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual) que foi escrito pela Starkware e anteriormente auditado e implantado.



### Contratos do Tesouro



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.26.09 PM.png>)

O contrato do TreasuryVester foi inspirado pela [Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol).

O timelock curto só pode executar ações aprovadas pela governança.

Há dois investidores do tesouro e contratos do tesouro: um deles visa as recompensas do contrato de incentivo e o outro, a detenção dos fundos do tesouro para “propósitos gerais”.

Como a governança controla cada tesouro, ela pode transferir fundos para qualquer endereço e/ou aprovar qualquer endereço para gastar fundos de qualquer um dos tesouros. Por exemplo, os programas de recompensas precisarão ter limites de aprovação de token definidos pela governança.

Cada investidor do tesouro fará a aquisição de tokens de forma linear ao longo de \~5 anos (3 de agosto de 2021 - 3 de agosto de 2026) para o tesouro correspondente.



## Contratos periféricos

### Recompensas da Chainlink Oracle-Powered (Recompensas de provedores de liquidez e trades)

O objetivo deste sistema é calcular e publicar, por meio de uma rede descentralizada de signatários de oracle (oracle signers), as recompensas de token DYDX obtidas pelos traders usando a exchange dYdX layer 2. As recompensas são armazenadas em uma árvore de Merkle, que contém as recompensas cumulativas obtidas por cada usuário desde o início do programa de distribuição. A cada epoch, a raiz Merkle é atualizada no contrato inteligente MerkleDistributorV1 para refletir as recompensas obtidas na epoch anterior.

Integramos o sistema da Chainlink Oracle para postar dados de recompensas on-chain. Usamos IPNS para postar os dados de trades usados pela Chainlink para criar a árvore de Merkle. Usando IPNS, podemos postar os dados de trades para a epoch mais recente no mesmo link de IPNS que as epoch anteriores, o que significa que a localização dos dados não mudará.

Após calcular as recompensas apropriadas a partir dos dados de trades brutos, a Chainlink posta as recompensas da árvore de Merkle na IPFS. O CID IPFS com os dados da árvore de Merkle é armazenado no contrato de distribuidor Merkle juntamente com a raiz Merkle para as recompensas dessa epoch.

O fluxograma a seguir mostra a arquitetura do sistema de Recompensas da Chainlink Oracle-Powered:

![](<.. /.gitbook/assets/Merkle Distributor.png>)

### Outros ativos

* Os ativos da marca dYdX Foundation estão disponíveis [**aqui**](https://dydx.foundation/brand)****
