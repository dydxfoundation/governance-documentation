---
description: Uma visão geral do sistema de epochs
---

# Epochs

Todas as recompensas e contratos de staking operam em ciclos de `28 dias`, referidos como **epochs**. Uma nova epoch começa automaticamente quando a epoch atual termina.

O seguinte acontecerá ao final de cada epoch:

* **As recompensas de trades** são distribuídas. As recompensas são resgatadas em [**dydx.community**](https://dydx.community) em aproximadamente `7 dias` após o final da epoch.
* **As recompensas para provedores de liquidez** são distribuídas. As recompensas são resgatadas em [**dydx.community**](https://dydx.community) em aproximadamente `7 dias` após o final da epoch.
* Saques solicitados para o **pool de staking de liquidez** podem ser feitos quando a epoch termina.
* Saques solicitados para o **pool de staking de segurança** podem ser feitos quando a epoch termina.

O seguinte acontecerá apenas ao final de **Epoch 0**:

* As recompensas de mineração retroativas serão distribuídas. As recompensas são resgatadas em [**dydx.community**](https://dydx.community) em aproximadamente `8 dias` após o final da epoch 0.
* As transferências de $ethDYDX ficam inicialmente restritas. O período de restrição de transferências inicial foi removido em torno de `8 dias` após o final da epoch 0.
* **A $ethDYDX tornou-se transferível em 8 de setembro de 2021, às 15:00:00 UTC.**

**A epoch 0** começou em **3 de agosto de 2021, às 15:00:00 UTC**. A tabela a seguir descreve as datas de início e final de epoch (que podem ser modificadas pela governança da dYdX v3):

| Epoch | Data de início (UTC) | Data de final (UTC) | Dias | Anos cumulativos |
| ----- | ------------------- | ------------------- | ---- | ---------------- |
| 0 | 03/08/2021 15:00:00 | 31/08/2021 15:00:00 | 28 | 0,08 |
| 1 | 31/08/2021 15:00:00 | 28/09/2021 15:00:00 | 28 | 0,15 |
| 2 | 28/09/2021 15:00:00 | 26/10/2021 15:00:00 | 28 | 0,23 |
| 3 | 26/10/2021 15:00:00 | 23/11/2021 15:00:00 | 28 | 0,31 |
| 4 | 23/11/2021 15:00:00 | 21/12/2021 15:00:00 | 28 | 0,38 |
| 5 | 21/12/2021 15:00:00 | 18/01/2022 15:00:00 | 28 | 0,46 |
| 6 | 18/01/2022 15:00:00 | 15/02/2022 15:00:00 | 28 | 0,54 |
| 7 | 15/02/2022 15:00:00 | 15/03/2022 15:00:00 | 28 | 0,61 |
| 8 | 15/03/2022 15:00:00 | 12/04/2022 15:00:00 | 28 | 0,69 |
| 9 | 12/04/2022 15:00:00 | 10/05/2022 15:00:00 | 28 | 0,77 |
| 10 | 10/05/2022 15:00:00 | 07/06/2022 15:00:00 | 28 | 0,84 |
| 11 | 07/06/2022 15:00:00 | 05/07/2022 15:00:00 | 28 | 0,92 |
| 12 | 05/07/2022 15:00:00 | 02/08/2022 15:00:00 | 28 | 1,00 |
| 13 | 02/08/2022 15:00:00 | 30/08/2022 15:00:00 | 28 | 1,07 |
| 14 | 30/08/2022 15:00:00 | 27/09/2022 15:00:00 | 28 | 1,15 |
| 15 | 27/09/2022 15:00:00 | 25/10/2022 15:00:00 | 28 | 1,23 |
| 16 | 25/10/2022 15:00:00 | 22/11/2022 15:00:00 | 28 | 1,30 |
| 17 | 22/11/2022 15:00:00 | 20/12/2022 15:00:00 | 28 | 1,38 |
| 18 | 20/12/2022 15:00:00 | 17/01/2023 15:00:00 | 28 | 1,46 |
| 19 | 17/01/2023 15:00:00 | 14/02/2023 15:00:00 | 28 | 1,53 |
| 20 | 14/02/2023 15:00:00 | 14/03/2023 15:00:00 | 28 | 1,61 |
| 21 | 14/03/2023 15:00:00 | 11/04/2023 15:00:00 | 28 | 1,69 |
| 22 | 11/04/2023 15:00:00 | 09/05/2023 15:00:00 | 28 | 1,76 |
| 23 | 09/05/2023 15:00:00 | 06/06/2023 15:00:00 | 28 | 1,84 |
| 24 | 06/06/2023 15:00:00 | 04/07/2023 15:00:00 | 28 | 1,92 |
| 25 | 04/07/2023 15:00:00 | 01/08/2023 15:00:00 | 28 | 1,99 |
| 26 | 01/08/2023 15:00:00 | 29/08/2023 15:00:00 | 28 | 2,07 |
| 27 | 29/08/2023 15:00:00 | 26/09/2023 15:00:00 | 28 | 2,15 |
| 28 | 26/09/2023 15:00:00 | 24/10/2023 15:00:00 | 28 | 2,22 |
| 29 | 24/10/2023 15:00:00 | 21/11/2023 15:00:00 | 28 | 2,30 |
| 30 | 21/11/2023 15:00:00 | 19/12/2023 15:00:00 | 28 | 2,38 |
| 31 | 19/12/2023 15:00:00 | 16/01/2024 15:00:00 | 28 | 2,45 |
| 32 | 16/01/2024 15:00:00 | 13/02/2024 15:00:00 | 28 | 2,53 |
| 33 | 13/02/2024 15:00:00 | 12/03/2024 15:00:00 | 28 | 2,61 |
| 34 | 12/03/2024 15:00:00 | 09/04/2024 15:00:00 | 28 | 2,68 |
| 35 | 09/04/2024 15:00:00 | 07/05/2024 15:00:00 | 28 | 2,76 |
| 36 | 07/05/2024 15:00:00 | 04/06/2024 15:00:00 | 28 | 2,84 |
| 37 | 04/06/2024 15:00:00 | 02/07/2024 15:00:00 | 28 | 2,92 |
| 38 | 02/07/2024 15:00:00 | 30/07/2024 15:00:00 | 28 | 2,99 |
| 39 | 30/07/2024 15:00:00 | 27/08/2024 15:00:00 | 28 | 3,07 |
| 40 | 27/08/2024 15:00:00 | 24/09/2024 15:00:00 | 28 | 3,15 |
| 41 | 24/09/2024 15:00:00 | 22/10/2024 15:00:00 | 28 | 3,22 |
| 42 | 22/10/2024 15:00:00 | 19/11/2024 15:00:00 | 28 | 3,30 |
| 43 | 19/11/2024 15:00:00 | 17/12/2024 15:00:00 | 28 | 3,38 |
| 44 | 17/12/2024 15:00:00 | 14/01/2025 15:00:00 | 28 | 3,45 |
| 45 | 14/01/2025 15:00:00 | 11/02/2025 15:00:00 | 28 | 3,53 |
| 46 | 11/02/2025 15:00:00 | 11/03/2025 15:00:00 | 28 | 3,61 |
| 47 | 11/03/2025 15:00:00 | 08/04/2025 15:00:00 | 28 | 3,68 |
| 48 | 08/04/2025 15:00:00 | 06/05/2025 15:00:00 | 28 | 3,76 |
| 49 | 06/05/2025 15:00:00 | 03/06/2025 15:00:00 | 28 | 3,84 |
| 50 | 03/06/2025 15:00:00 | 01/07/2025 15:00:00 | 28 | 3,91 |
| 51 | 01/07/2025 15:00:00 | 29/07/2025 15:00:00 | 28 | 3,99 |
| 52 | 29/07/2025 15:00:00 | 26/08/2025 15:00:00 | 28 | 4,07 |
| 53 | 26/08/2025 15:00:00 | 23/09/2025 15:00:00 | 28 | 4,14 |
| 54 | 23/09/2025 15:00:00 | 21/10/2025 15:00:00 | 28 | 4,22 |
| 55 | 21/10/2025 15:00:00 | 18/11/2025 15:00:00 | 28 | 4,30 |
| 56 | 18/11/2025 15:00:00 | 16/12/2025 15:00:00 | 28 | 4,37 |
| 57 | 16/12/2025 15:00:00 | 13/11/2026 15:00:00 | 28 | 4,45 |
| 58 | 13/11/2026 15:00:00 | 10/02/2026 15:00:00 | 28 | 4,53 |
| 59 | 10/02/2026 15:00:00 | 10/03/2026 15:00:00 | 28 | 4,60 |
| 60 | 10/03/2026 15:00:00 | 07/04/2026 15:00:00 | 28 | 4,68 |
| 61 | 07/04/2026 15:00:00 | 05/05/2026 15:00:00 | 28 | 4,76 |
| 62 | 05/05/2026 15:00:00 | 02/06/2026 15:00:00 | 28 | 4,83 |
| 63 | 02/06/2026 15:00:00 | 30/06/2026 15:00:00 | 28 | 4,91 |
| 64 | 30/06/2026 15:00:00 | 28/07/2026 15:00:00 | 28 | 4,99 |
| 65 | 28/07/2026 15:00:00 | 25/08/2026 15:00:00 | 28 | 5,06 |

A dYdX Foundation criou um arquivo público no Google Agenda com datas de início / final para Epochs e Janelas de Bloqueio. Inscreva-se [**aqui**](https://calendar.google.com/calendar/u/3?cid=Y19wZjIwYzBoZzQ3dTR2cHRja283NDl1ajQyb0Bncm91cC5jYWxlbmRhci5nb29nbGUuY29t).

## **Quando as recompensas e pools de staking serão ativadas?**

* As [recompensas de mineração retroativas](../rewards/retroactive-mining-rewards.md) foram distribuídas na dYdX v3. Essas recompensas foram realizadas até **31 de agosto de 2021, às 15:00:00 UTC**.
* Agora, as [recompensas de trades](https://github.com/dydxfoundation/governance-docs/tree/58816ba822cb40fdbf1128dbbf5b0f6dbaa23cc1/reward-pools-1/trading-rewards.md) estão funcionando no protocolo. Essas recompensas funcionarão até **3 de agosto de 2026, 15:00:00 UTC**.
* Agora, as [recompensas para provedores de liquidez](../rewards/liquidity-provider-rewards.md) estão funcionando no protocolo. Essas recompensas funcionarão até **3 de agosto de 2026, 15:00:00 UTC**.
* O [pool de staking de liquidez](../staking-pools/liquidity-staking-pool.md) foi encerrado em 29 de setembro de 2022.
* O [pool de staking de segurança](../staking-pools/safety-staking-pool.md) foi encerrado em 28 de novembro de 2022.

## A governança da dYdX pode modificar o cronograma de epoch?

O comprimento inicial da epoch é `de 28 dias`. A governança da dYdX v3 pode votar para modificar os comprimentos de epoch, nos limites especificados. Os comprimentos mínimo e máximo de epoch são de `6 dias` e `92 dias`, respectivamente.

## O que é a janela de bloqueio?

Relacionada à [pool de staking de liquidez](../staking-pools/liquidity-staking-pool.md) e [pool de staking de segurança](../staking-pools/safety-staking-pool.md), há um cronograma de epoch a ser aplicado no que diz respeito a saques, de modo a fornecer previsibilidade e uma cadência regular de disponibilidade de fundos no pool. Um staker deve solicitar a remoção de fundos em stake antes da janela de bloqueio para poder sacar seus fundos após o final da epoch. Se um staker não solicitar o saque, seus fundos em staking serão mantidos para a próxima epoch.

A janela de bloqueio recomendada para cada um no pool de staking de liquidez e no de segurança é `de 14 dias`. No [DIP 17](https://dydx.community/dashboard/proposal/9), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/7) pela redução do tempo da janela de bloqueio de `14` para `3 dias`. A governança da dYdX pode votar para modificar a janela de bloqueio dentro dos limites especificados. As janelas de bloqueio mínima e máxima são de `3` e `46 dias`, respectivamente.

## Quando posso sacar e transferir as recompensas $ethDYDX que recebi?

Os tokens $ethDYDX ganhos por meio das recompensas [de mineração retroativas](../rewards/retroactive-mining-rewards.md), recompensas [de trading](../rewards/trading-rewards.md) e [recompensas de provedor de liquidez](../rewards/liquidity-provider-rewards.md) são transferíveis ao final de cada epoch. Os detentores de $ethDYDX são obrigados a esperar aproximadamente `7 dias` (**Período de espera**) após o final da epoch para resgatar tokens. Uma vez que os tokens tenham sido resgatados, eles poderão ser transferidos ou delegados para a governança da dYdX.

Os tokens $ethDYDX obtidos por meio do pool de staking de liquidez e o pool de staking de segurança são resgatados a cada bloco e podem ser sacados a qualquer momento durante uma determinada epoch.

Em **8 de setembro de 2021 às 15:00:00 UTC**, 8 dias após o final da epoch 0, as restrições de transferência iniciais foram automaticamente removidas. Aproximadamente **8,11%** do fornecimento de $ethDYDX se tornou líquido.

## Qual é o propósito do período de espera? Como recompensas são armazenadas ao final de cada epoch?

As [recompensas de mineração retroativas](../rewards/retroactive-mining-rewards.md), [recompensas de trades](../rewards/trading-rewards.md) e [recompensas para provedores de liquidez](../rewards/liquidity-provider-rewards.md) são armazenadas em uma árvore de Merkle, que contém as recompensas cumulativas obtidas por cada usuário desde o início do programa de distribuição.

Ao final de cada epoch, a raiz de Merkle é atualizada por meio do sistema oracle da ChainLink no contrato inteligente `MerkleDistributorV1` a fim de refletir recompensas obtidas na última epoch. Uma atualização é realizada definindo a raiz Merkle proposta para o valor mais recente retornado pelo contrato oracle. A raiz Merkle proposta pode ser ativada após um **período de espera** de `7 dias` ter expirado. Durante o período de espera, a governança da dYdX pode congelar a raiz Merkle, caso a raiz proposta se mostre incorreta ou maliciosa. Se a raiz da Merkle não estiver congelada, a nova raiz Merkle será ativada e os usuários poderão resgatar suas recompensas a partir da epoch anterior.

Cada vez que a epoch se altera, o seguinte ocorre nessa ordem:

* Quando uma epoch termina, os dados de recompensas são calculados para toda a atividade do usuário a partir da última epoch.
* Esses dados são adicionados a uma estrutura de dados em IPFS, armazenados sob um nome IPNS fixo.
* O sistema oracle da ChainLink, além de notar alterações na epoch, faz consultas nos dados de recompensas mais recentes usando o nome IPNS conhecido.
* Cada signatário da oracle usa esses dados de recompensas para calcular recompensas recentes para cada usuário.
* Cada signatário da oracle calcula a nova árvore de Merkle cumulativa e sua raiz.
* Cada signatário da oracle grava os dados da árvore de Merkle em IPFS, recebendo um CID do IPFS. (Calculam a mesma árvore e, portanto, devem receber o mesmo CID.)
* Se os signatários da oracle concordarem com os mesmos valores, o campo RewardsOracle será atualizado com a nova raiz Merkle, CID do IPFS e quantidade de epoch.
* Um signatário da oracle (ou um terceiro) chama a função pública `MerkleDistributorV1.proposeRoot()` para definir a raiz Merkle proposta para o novo valor da oracle.
* Um período de espera ocorre durante o qual a governança pode chamar `MerkleDistributorV1.pauseRootUpdates()` para evitar que a raiz Merkle proposta entre em vigor.
* Após o período de espera, um signatário da oracle (ou um terceiro) chama a função pública `MerkleDistributorV1.updateRoot()` fazendo com que a raiz Merkle fique ativa.
* Uma vez que a nova raiz Merkle esteja ativa, os usuários poderão resgatar recompensas a partir da última epoch.
