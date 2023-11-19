---
description: Uma visão geral do tesouro da comunidade.
---

# Tesouro da Comunidade

**`24,2%`** (`241.735.862 $ethDYDX`) do fornecimento de token é alocado para o tesouro da comunidade, de modo que a dYdX o use de forma contínua para subvenções de contribuidores, iniciativas da comunidade, mineração de liquidez e outros programas. Inicialmente, `5,0%` do fornecimento de token (`50.000.000 $ethDYDX`) foram [alocados](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations) ao tesouro da comunidade e 766.703 $ethDYDX foram investidos no tesouro da comunidade a cada epoch. Atualmente, 3.787.251 $ethDYDX foram coletados no tesouro da comunidade, porque várias propostas de governança resultaram em um aumento de 3.020.548 $ethDYDX no valor de $ethDYDX disponível para a comunidade dYdX a cada epoch:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - Definição as recompensas de staking de USDC para 0 (383.562 $ethDYDX por epoch),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - Redução de recompensas de trading em 25% (958.904 $ethDYDX por epoch),
* [DPI 17](https://dydx.community/dashboard/proposal/9) - Definição de recompensas de staking de $DYDX para 0 (383.562 $ethDYDX por epoch).
* [DPI 20](https://dydx.community/dashboard/proposal/11) - Redução de recompensas de trading em 45% (1.294.520 $ethDYDX por epoch) e
* [DPI 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - Redução de recompensas de provedor de liquidez em 50% (575.342 $ethDYDX por epoch).



**Objetivos**

* Financiar programas e iniciativas que impulsionem o crescimento da dYdX.
* Desenvolver programas de concessões para financiar NFTs da comunidade, hackathons, painéis de análise, memes, swag, ferramentas de terceiros, traduções e outros projetos.
* Desenvolver um sistema de governança de alto nível e incentivar uma governança robusta.

## Visão geral

O tesouro da comunidade manterá $ethDYDX para ser usado conforme os detentores de $ethDYDX decidirem, seja para doações, novos pools de mineração de liquidez ou qualquer outro programa. O $ethDYDX será investido ao tesouro da comunidade de forma contínua ao longo de cinco anos. Será necessário haver uma votação por parte da governança para gastar qualquer ethDYDX no tesouro da comunidade.

Se, após cinco anos, a governança decidir promover uma inflação perpétua (numa inflação máxima anual de `2%`), qualquer mint de $ethDYDX futuro ficará disponível para o tesouro da comunidade.

## Perguntas e respostas

### Como $ethDYDX é investido no Tesouro da Comunidade?

A cada segundo, o Investidor do Tesouro da Comunidade (veja detalhes [aqui](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) investe [`0,3169242627`](tel:03169242627) $ethDYDX no Tesouro da Comunidade. Após o $ethDYDX ter sido investido, chamar a função `reivindicação` no Investidor do Tesouro da Comunidade transferirá o $ethDYDX investido para o Tesouro da Comunidade. Qualquer membro da comunidade DYDX pode chamar a função `reivindicação` na Etherscan [aqui](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) (o que exigiria algum ETH para cobrir as taxas de gás) e mover o $ethDYDX investido do Investidor do Tesouro da Comunidade para o Tesouro da Comunidade.

Consulte os [Termos de uso](https://dydx.foundation/terms) da dYdX Foundation para obter mais detalhes sobre o controle do tesouro da comunidade pela comunidade dYdX.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### Qual é o saldo investido do Tesouro da Comunidade?

Os membros da comunidade DYDX podem visualizar o saldo investido do Tesouro da comunidade [aqui](https://dydx.shippooor.xyz/). \
\
Além disso, a dYdX Foundation publica publica apenas para fins informativos o saldo investido do Tesouro da Comunidade no [Relatório da Epoch](https://dydx.foundation/blog) ao final de cada epoch. Além do $ethDYDX investido no Tesouro da Comunidade, a comunidade dYdX também pode acessar o $ethDYDX acumulado no Tesouro de Recompensas como resultado dos votos para:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - Definição as recompensas de staking de USDC para 0 (383.562 $ethDYDX por epoch),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - Redução de recompensas de trading em 25% (958.904 $ethDYDX por epoch),
* [DPI 17](https://dydx.community/dashboard/proposal/9) - Definição de recompensas de staking de $ethDYDX para 0 (383.562 $ethDYDX por epoch).
* [DPI 20](https://dydx.community/dashboard/proposal/11) - Redução de recompensas de trading em 45% (1.294.520 $ethDYDX por epoch) e
* [DPI 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - Redução de recompensas de provedor de liquidez em 50% (575.342 $ethDYDX por epoch).

A partir da Epoch 26, 3.595.890 $ethDYDX serão acrescidos no Tesouro de Recompensas a cada época e poderão ser usados pela comunidade dYdX com um [voto de governança](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

### Quem pode enviar propostas de gasto de ethDYDX do Tesouro da Comunidade?

Qualquer usuário com poder de proposição suficiente pode enviar propostas. Será necessário haver uma votação por parte da governança para gastar qualquer ethDYDX no tesouro da comunidade. Para enviar uma proposta, é preciso enviar uma proposta de melhoria da dYdX (DIP, na sigla em inglês) conforme estabelecido no [ciclo de vida da proposta DIP](../voting-and-governance/dip-proposal-lifecycle.md).

### Como você vai criar uma proposta de fundos do Tesouro da Comunidade?

A Reverie criou um guia abrangente e técnico que dá o passo-a-passo sobre como qualquer membro da comunidade dYdX com mais de 5M $ethDYDX ([limite de proposta](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) para um [curto voto de timelock](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) em poder proposicional pode criar uma proposta para transferir $ethDYDX do Tesouro da Comunidade para um endereço de destino. Clique [aqui](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) para acessar o guia técnico.

### Quais tipos de propostas podem ser enviadas ao Tesouro da Comunidade?

Um tesouro gerenciado pela comunidade abre muitas possibilidades. Esperamos ver vários experimentos e iniciativas, incluindo contribuições ao ecossistema, o que poderá promover o crescimento do ecossistema da dYdX v3.
