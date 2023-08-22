---
description: Uma visão geral do tesouro da comunidade.
---

# Tesouro da Comunidade

**`24,2%`** (`241.735.862 $DYDX`) do suprimento de token é alocado ao tesouro da comunidade para que a comunidade dYdX use-o continuamente para subsídios de contribuinte, iniciativas da comunidade, mineração de liquidez e outros programas. Inicialmente, `5,0%``` do fornecimento de tokens de ([50.000.000 $DYDX](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations)) foram alocados ao tesouro da comunidade e 766.703 $DYDX foi investido no tesouro da comunidade a cada epoch. Atualmente, 3.787.251 $DYDX foi investido no tesouro da comunidade pois três propostas de governança resultaram em um aumento de 3.020.548 $DYDX na quantidade de $DYDX disponível para a comunidade dYdX a cada epoch:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - Definição as recompensas de staking de USDC para 0 (383.562 $DYDX por epoch),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - Redução de recompensas de trading em 25% (958.904 $DYDX por epoch),
* [DIP 17](https://dydx.community/dashboard/proposal/9) - Definição de recompensas de staking de $DYDX para 0 (383.562 $DYDX por época).
* [DIP 20](https://dydx.community/dashboard/proposal/11) - Redução de recompensas de trading em 45% (1.294.520 $DYDX por época) e
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - Redução de recompensas de provedor de liquidez em 50% (575.342 $DYDX por época).



**Objetivos**

* Financiar programas e iniciativas que impulsionem o crescimento da dYdX.
* Desenvolver programas de concessões para financiar NFTs da comunidade, hackathons, painéis de análise, memes, swag, ferramentas de terceiros, traduções e outros projetos.
* Desenvolver um sistema de governança de alto nível e incentivar uma governança robusta.

## Visão geral

O tesouro da comunidade manterá $DYDX para o uso conforme os holders de $DYDX decidirem, seja para subsídios, novas pools de mineração de liquidez ou qualquer outro programa. Haverá investimento de $DYDX no tesouro da comunidade de forma contínua ao longo de cinco anos. Será necessário uma votação por parte da governança para gastar qualquer $DYDX do tesouro da comunidade.

Se, após cinco anos, a governança decidir promover uma inflação perpétua (numa inflação máxima anual de `2%`), qualquer mint de $DYDX futuro ficará disponível para o tesouro da comunidade.

## Perguntas e respostas

### Como $DYDX é investido no Tesouro da Comunidade?

A cada segundo, o Investidor do Tesouro da Comunidade (veja detalhes [aqui](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) investe [`0,3169242627`](tel:03169242627) $DYDX no Tesouro da Comunidade. Assim que $DYDX é investido, chamar a função `reivindicação` no Investidor do Tesouro da Comunidade transferirá o $DYDX investido ao tesouro. Qualquer membro da comunidade DYDX pode chamar a função `reivindicação` na Etherscan [aqui](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) (o que exigiria algum ETH para cobrir as taxas de gás) e mover o $DYDX investido do Investidor do Tesouro da Comunidade para o Tesouro da Comunidade.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### Qual é o saldo investido do Tesouro da Comunidade?

Os membros da comunidade DYDX podem visualizar o saldo investido do Tesouro da comunidade [aqui](https://dydx.shippooor.xyz/). \
\
Além disso, a dYdX Foundation publica o saldo investido do Tesouro da Comunidade no [Relatório da Epoch](https://dydx.foundation/blog) ao final de cada epoch. Além do $DYDX investido no Tesouro da Comunidade, a comunidade dYdX também pode acessar o $DYDX acumulado no Tesouro de Recompensas como resultado dos votos para:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - Definição as recompensas de staking de USDC para 0 (383.562 $DYDX por epoch),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - Redução de recompensas de trading em 25% (958.904 $DYDX por epoch),
* [DIP 17](https://dydx.community/dashboard/proposal/9) - Definição de recompensas de staking de $DYDX para 0 (383.562 $DYDX por época).
* [DIP 20](https://dydx.community/dashboard/proposal/11) - Redução de recompensas de trading em 45% (1.294.520 $DYDX por época) e
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - Redução de recompensas de provedor de liquidez em 50% (575.342 $DYDX por época).

A partir da Época 26, 3.595.890 $DYDX  serão acrescidos no Tesouro de Recompensas a cada época e poderão ser usados pela comunidade dYdX com um [voto de governança](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

### Quem pode enviar propostas para gastar $DYDX do Tesouro da Comunidade?

Qualquer usuário com poder de proposição suficiente pode enviar propostas. Será necessário haver uma votação por parte da governança para gastar qualquer $DYDX no tesouro da comunidade. Para enviar uma proposta, é preciso enviar uma proposta de melhoria da dYdX (DIP, na sigla em inglês) conforme estabelecido no [ciclo de vida da proposta DIP](../voting-and-governance/dip-proposal-lifecycle.md).

### Como você vai criar uma proposta de fundos do Tesouro da Comunidade?

A Reverie criou um guia abrangente e técnico que dá o passo a passo sobre como qualquer membro da comunidade dYdX com mais de 5M $DYDX ([limite de proposta](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) para um [curto voto de timelock](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) em poder proposicional pode criar uma proposta para transferir $DYDX do Tesouro da Comunidade para um endereço de destino. Clique [aqui](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) para acessar o guia técnico.

### Quais tipos de propostas podem ser enviadas ao Tesouro da Comunidade?

Um tesouro gerenciado pela comunidade abre muitas possibilidades. Esperamos ver vários experimentos e iniciativas, incluindo contribuições ao ecossistema, o que poderá promover o crescimento do ecossistema do protocolo dYdX Layer 2.
