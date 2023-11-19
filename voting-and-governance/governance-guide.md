---
description: >-
  Uma visão geral do processo de criação de DRC da governança, criação de pesquisas do snapshot, criação de DIPs, votação em uma pesquisa do snapshot, votação em uma DIP, enfileiramento de uma DIP e sua execução.
---

# Guia de governança

A dYdX Foundation criou este guia para ajudar a comunidade a entender o processo de governança da dYdX. O guia fornece uma visão geral passo a passo de:

* [Discussões de fórum (off-chain)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Criação de DRC (off-chain)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Criação de pesquisas de snapshot (off-chain)](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [Votação em uma pesquisa de snapshot](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [Criação de DIP (off-chain)](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [Criação de DIP (on-chain)](governance-guide.md#step-1-on-chain-dip-drafting)
* [Votação de uma DIP (on-chain)](governance-guide.md#how-to-vote-on-a-dip)
* [Enfileiramento de uma DIP (on-chain)](governance-guide.md#how-to-queue-a-proposal)
* [Execução de uma DIP (on-chain)](governance-guide.md#how-to-execute-a-proposal)

Os dois exemplos apresentados no guia são a _DIP 2 (proposta off-chain) - Redução do limiar de recompensas para provedores de liquidez_ e a _DIP 3 (proposta on-chain) - Restauração de módulo de segurança_.

## DIP 2 (proposta Off-chain) - Redução do limiar de recompensas para provedores de liquidez

_**Resumo:**_

Na epoch 6, a comunidade da dYdX votou no [snapshot](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43) para reduzir o limiar de volume de recompensas da LP para os makers de mercado de 1% para 0,25%. A redução do limiar de recompensas de LP de 5% para 1% na epoch 2 seguiu o mesmo processo que a redução da epoch 6 (1% para 0,25%). Veja abaixo a visão geral passo a passo para tal redução do limiar de volume de recompensas de LP de 5% para 1%.

A maioria da comunidade (399 eleitores e 86% da $ethDYDX) votaram no [snapshot](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN) para reduzir o limiar de volume para recompensas para o provedor de liquidez de 5% para 1%. Uma [DIP off-chain](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md) para reduzir o limiar de volume de recompensas para os makers de mercado de 5% para 1% foi enviado por Jacob Goh (jteam0x) na DeFiance Capital. Os makers de mercado que atenderam ao limiar de 1% na epoch 2 ficaram elegíveis para ganhar recompensas de provedor de liquidez na epoch 3. A proposta não exigiu nenhuma alteração no contrato inteligente on-chain.

_**Contexto:**_

Como parte do [programa de recompensas](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards) para provedores de liquidez, 1.150.685 em $ethDYDX é distribuído por epoch (28 dias) para provedores de liquidez para os makers de mercado do protocolo. As recompensas são distribuídas com base em uma fórmula que recompensa uma combinação de tempo de atividade, profundidade de dois lados, spreads de compra e venda e a quantidade de mercados aceitos. Para ser elegível para este programa de recompensas, os provedores de liquidez precisam fornecer uma porcentagem mínima do volume de maker durante a epoch anterior.

A comunidade da dYdX tem "controle imediato e irrevogável" sobre o limiar de recompensas para provedores de liquidez. A lista completa de parâmetros que a comunidade controla está [aqui](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

A comunidade foi motivada a reduzir o limiar de recompensas para provedores de liquidez porque isso incentivaria novos makers de mercado, em especial aqueles de pequeno e médio porte a aumentarem a liquidez na plataforma da dYdX. Além disso, aumentar a quantidade de makers de mercado na plataforma ajuda o protocolo da dYdX a se tornar mais descentralizado.

Em seguida, fornecemos uma visão geral passo a passo de como a governança da dYdX funciona na prática. Mais informações sobre o processo de governança da dYdX se encontram [aqui](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

### **PASSO 1 - Discussões de fórum, criação de DRC (Off-Chain) e feedback de DRC**

_**Descrição:**_

O processo de governança da dYdX é alimentado por [fóruns de governança](https://dydx.forum/). Os membros da comunidade postam e comentam a respeito de tópicos de discussão para chegar a um consenso off-chain. Mais informações sobre fóruns de discussões e criação de DRCs se encontram [aqui.](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) \
\
Aviso - As operações de subDAO lançaram [**https://dydx.forum/**](https://dydx.forum/) como o novo fórum de [acordo com a votação da comunidade para a transição da Commonwealth para o Discourse](https://snapshot.org/#/dydxgov.eth/proposal/0xa5e77732dd24edd26bd41b089969b3662c29eb41c3bacd35cb2931ca55882a8f). Algumas referências neste guia para discussões de DRC anteriores ainda apontam para a Commonwealth, mas quaisquer novas discussões devem acontecer no fórum do [**Discourse**](https://dydx.forum/) que foi recém-lançado. \


_**Envio de DIP 2:**_

Su Zhu (zhusu) da Three Arrows Capital criou um [fórum de discussão off-chain](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/) para reduzir o limiar de recompensas para provedores de liquidez. Vários membros da comunidade, como a Evgeny da Wintermute, Ben da Kronos, Josh da Sixtant e muitos outros participaram da discussão e ofereceram feedback valioso.

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives.png)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives-2.png)

#### _Como postar e comentar no Discourse:_

* Registre-se no Discourse com sua conta de e-mail e junte-se à comunidade dYdX [aqui](https://dydx.forum/).

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 10.59.27 AM.png" alt=""><figcaption></figcaption></figure>

* Selecione uma thread, confira os comentários, dê likes ou responda aos comentários.
* Crie um novo tópico de discussão ou publique uma DRC clicando em “**Novo Tópico**” e selecionando a categoria.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.03.33 AM.png" alt=""><figcaption></figcaption></figure>

* Se você estiver [criando](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) uma DRC, siga este modelo aqui. Conforme descrito na _criação de DRC_ no [ciclo de vida de propostas](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle), DRCs devem incluir ao menos os seguintes itens:
  * Um título curto e conciso da DRC.
  * Descrição de proposta curta e concisa.
  * A lógica da DRC (por exemplo, por quê?).
  * O título da postagem no fórum deve incluir DRC: \[inserir título curto da DRC] (por exemplo, DRC: nova solicitação de mercado).
  * Uma pesquisa da comunidade na qual os membros podem votar em melhorias off-chain.

### **PASSO 2 — Pesquisas de snapshot de DRC (Off-Chain)**

_**Descrição:**_

Depois que a comunidade chegar a um consenso, um membro da comunidade com poder de proposição de 10 mil pode criar um voto off-chain para a DRC no [snapshot](https://snapshot.org/#/). O [poder de proposição](https://docs.dydx.community/dydx-governance/voting-and-governance/voting) dá acesso à criação e sustentação de uma proposta. Um snapshot é uma interface simples de votação que permite aos usuários indicar sentimentos off-chain. Os votos no snapshot são ponderados pelo número de Tokens de Governança detidos ou delegados ao endereço usado para votar. O membro da comunidade que cria a pesquisa do snapshot deve fornecer detalhes sobre a DRC, um sistema de votação, data de início e fim da votação, além do número de bloco do snapshot. O período de votação deve ter 5 dias de duração e a votação deve começar após um atraso de votação de 1 dia ( _com base em tempos de bloqueio de 13,2 segundos)_. O atraso de votação fornece tempo para os membros da comunidade da dYdX saberem detalhes sobre a DRC, comprar $ethDYDX ou delegarem o poder de votação dos tokens de governança. Os membros da comunidade que possuem Tokens de Governança ou que tenham sido delegados o poder de voto antes do número de bloco de Snapshot são elegíveis para votar. Mais informações sobre pesquisas de snapshot são encontradas [aqui](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

_**Envio de DIP 2:**_

Os membros da comunidade forneceram feedback sobre o post de Su Zhu. Os seguintes limiares de recompensas foram sugeridos pela comunidade:

* [0,5%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Su Zhu da Three Arrows Capital,
* [1%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) — Sam da BitTrading,
* [2,5%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Ben da Kronos / WOO Network, e
* [5%](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - Evgeny da Wintermute.

Em seguida, Su Zhu criou uma pesquisa de snapshot com as seguintes opções:

* Limiar de MM inferior a 1%
* Limiar de MM inferior a 2,5%
* Manter o limiar de MM a 5%

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWaeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-create-snapshot.png)

#### _Como votar em uma pesquisa do snapshot:_

* Registre-se no snapshot com sua carteira Ethereum e siga as propostas da dYdX [aqui](https://snapshot.org/#/dydxgov.eth).

![https://snapshot.org/#/dydxgov.eth](../.gitbook/assets/2-register-snapshot.png)

* Para votar em pesquisas de snapshot ativas, você precisa ser um holder de tokens de governança ou ter poder de votação delegado para seu endereço antes do número de bloco de snapshot quando a pesquisa se tornou ativa.
* Para votar, clique na proposta e selecione “Yes (Sim)” ou “No (Não)” e, depois “Vote (Votar)”.

#### _Como criar uma pesquisa no snapshot:_

* Para criar uma pesquisa de snapshot, você precisará **ter um mínimo de 10 mil tokens de governança** **e/ou ter poder de voto delegado para o endereço que usa** para criar a proposta.
* A proposta de snapshot pode consistir em uma ou várias ações, até um máximo de 10 ações por proposta. As ações são alterações detalhas em uma proposta.
* Se você atender ao requisito de 10 mil tokens de poder de proposição, selecione “**New Proposal** (Nova proposta)” e preencha os campos de acordo com os requisitos de conteúdo abaixo.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.08.42 AM.png" alt=""><figcaption><p>Página de snapshot da dYdX - Botão "Criar nova proposta"</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.09.33 AM.png" alt=""><figcaption><p>Inclua detalhes do Snapshot aqui, e não deixe de incluir um link para a DRC</p></figcaption></figure>

Requisitos de conteúdo de pesquisa de snapshot de DRC:

* detalhes da DRC com um link para a discussão de fórum,
* um sistema de votação,
* data de início e data de término de votação definida como 4 dias de duração total  (_com base em tempos de bloqueio de 13,2 segundos)_, e
* A pesquisa de snapshot é postada 1 dia (\~6570 blocos) antes de a votação começar.

Requisito de envio de pesquisas de snapshot:

Para a maioria das decisões, uma pesquisa de snapshot atua como sinalização, já uma votação on-chain é necessária para um resultado definitivo que altera o contrato inteligente. Os votos de snapshot são considerados finais e vinculativos para decisões que não exijam uma chamada no contrato inteligente on-chain e mudanças consideráveis às fórmulas de recompensas de trades a provedores de liquidez. Além dos requisitos de conteúdo acima, pesquisas de snapshot que sejam votos vinculativos para variáveis controladas off-chain devem incluir:

* Opções de votação binária. Para maior clareza, um endereço deve votar a favor ou contra uma proposta.

![](../.gitbook/assets/2-snapshot-binary-voting.png)

* Após o voto, as informações relacionadas serão armazenadas em IPFS, e um relatório será gerado automaticamente, ficando disponível para download.

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWaeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-snapshot-ipfs.png)

### **PASSO 3 — Criação de DIP (proposta Off-chain)**

_**Descrição**:_

Uma DIP precisa ser criada quando (1) uma pesquisa de snapshot resulta em um parâmetro off-chain (como modificações nas fórmulas de recompensas de trades ou recompensas de LP) sendo atualizado e (2) quando um membro da comunidade quiser enviar uma proposta para modificar contratos inteligentes on-chain. Para votos que não exijam atualizações do contrato inteligente on-chain, o resultado da pesquisa de snapshot deve ser formalizado em uma DIP off-chain e enviado por meio de uma solicitação pull ao branch de DIP pendente da Github da dYdX Foundation. A DIP deve refletir o resultado vencedor do snapshot. A DIP [deve](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) especificar as informações incluídas no seguinte modelo.

_**Envio de DIP 2:**_

Neste caso, a [DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md) foi escrita por @Jteamdc.

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](../.gitbook/assets/2-dip-example.png)

Quando o projeto de proposta para a DIP 2 foi concluído, @Jteamdc criou uma \*\*\*\* [solicitação de pull](https://github.com/dydxfoundation/dip/pull/8) da ramificação em funcionamento na ramificação de DIPs pendentes da fundação da dYdX. Após a dYdX Foundation revisar a proposta e assiná-la, as alterações das DIPs pendentes foram incorporadas ao branch principal.

![https://github.com/dydxfoundation/dip/pulls](../.gitbook/assets/2-dip-pending-merge.png)

Ao passo que a redução do limiar de recompensas dos provedores de liquidez não requer nenhuma alteração no contrato inteligente on-chain, o processo é concluído e as alterações entram em vigor durante a próxima epoch.

#### _Como criar uma DIP:_

* A DIP deve ser baseada no resultado que venceu a votação da DIP off-chain no snapshot e pode consistir em uma ou várias ações, até no máximo de 10 ações por proposta. As ações são alterações detalhas em uma proposta. Mais informações podem ser encontradas em [Criação de DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution).
* Registre-se no Github: [https://github.com/signup](https://github.com/signup).
* Visite a página do repositório da dYdX [aqui](https://github.com/dydxfoundation/dip) e faça um fork do repositório em sua conta da Github.

![https://github.com/dydxfoundation/dip](../.gitbook/assets/2-dip-create-1.png)

* No repositório de DIP em fork, acesse o diretório que contém o conteúdo das DIPs: [https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips).

![](../.gitbook/assets/2-dip-create-2.png)

* Selecione a pasta de DIPs: [https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content).

![](../.gitbook/assets/2-dip-create-3.png)

A pasta de DIPs inclui um diretório de propostas anteriores que seguem o modelo de DIP [aqui.](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)

![https://github.com/dydxfoundation/dip/tree/master/content/dips](../.gitbook/assets/2-dip-create-4.png)

* Antes de começar a elaborar uma proposta, certifique-se de que o branch que você criou esteja atualizado com a versão mais recente do branch principal. Se estiver usando uma versão antiga do repositório de DIP, confirme se a sua versão em fork está atualizada com as alterações mais recentes. Para obter assistência ao mudar a base da sua versão forked, siga os seguintes passos aqui: [https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master).
* Edite o [modelo de DIP](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) com as informações da sua proposta. Se você não fez o fork do repositório de DIP, selecione o ícone de edição que vai criar automaticamente o repositório principal, visto que você não é um administrador.

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](../.gitbook/assets/2-dip-create-5.png)

* Siga o [modelo](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) e adicione sua DIP ao fork do repositório no diretório `content/dips/`. Siga as convenções de nomeação de status de DIP incluídas abaixo.

![](../.gitbook/assets/2-dip-create-6.png)

Status da DIP:

* WIP — uma DIP que ainda está sendo desenvolvida.
* Proposed (Proposta) – uma DIP que está pronta para ser proposta on-chain.
* Approved (Aprovada) - uma DIP que foi aceita para implementação pela comunidade da dYdX.
* Implemented (Implementada) - uma DIP que foi lançada para mainnet.
* Rejected (Rejeitada) - uma DIP que foi rejeitada.
* Depois de verificar se todo o conteúdo está correto, crie uma solicitação pull a partir de seu branch de trabalho com o branch de DIPs pendentes da dYdX Foundation. **Não** envie esta solicitação pull ao branch principal da dYdX Foundation, pois a tarefa IPFS falhará se quaisquer partes externas quiserem dar merge no branch principal. Use a solicitação pull [aqui](https://github.com/dydxfoundation/dip/pull/8) como exemplo.

![](../.gitbook/assets/2-dip-status-1.png)

* Após revisão, a dYdX Foundation fará o merge das alterações do branch de DIPs pendentes para o branch principal.

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/2-dip-status-2.png)

* Antes **do merge,** uma tarefa será executada automaticamente para enviar a DIP ao IPFS. Você pode verificar o upload da DIP para o IPFS aqui: [https://github.com/dydxfoundation/dip/pull/9/checks](https://github.com/dydxfoundation/dip/pull/9/checks).
* A DIP é adicionada em [**`dip`**](https://github.com/dydxfoundation/dip)`/`[`content`](https://github.com/dydxfoundation/dip/tree/master/content)/**`dips`**`/```.

![](../.gitbook/assets/2-dip-status-3.png)

Como a proposta não requer nenhuma alteração no contrato inteligente on-chain, o processo está completo e as alterações entram em vigor durante a próxima epoch

## DIP 3 (proposta on-chain) — Restauração do módulo de segurança

_**Resumo:**_

Em 1º de novembro, uma [DIP](https://dydx.community/dashboard/proposal/3) on-chain foi criada por Dan Robinson da Paradigm para restaurar a funcionalidade do pool de staking no módulo de segurança. A maioria da comunidade (251 eleitores e quase 142 milhões em ethDYDX) votaram a favor de restaurar a funcionalidade do módulo de segurança. Após um período de votação de 10 dias, foram necessários quase três dias para um membro da comunidade chamar a função de fila e mover a proposta para o atraso de timelock de 7 dias. Em 20 de novembro, o módulo de segurança foi restaurado e redefinido para um estado vazio.

_**Contexto:**_

O módulo de segurança da dYdX é um contrato de staking projetado para promover um pool descentralizada de fundos que podem ser usados para servir como barreira do protocolo dYdX. Os usuários fazem stake de $ethDYDX no pool de segurança e recebem $stkDYDX (1:1). $stkDYDX é uma posição tokenizada transferida como ERC-20 que tem os mesmos direitos de voto e de proposta que $ethDYDX. No caso de um evento de déficit, uma votação de governança é necessária para reduzir a $ethDYDX em staking para mitigar perdas. Do fornecimento de token $ethDYDX, 2,5% (25.000.000 $ethDYDX) do fornecimento dele será distribuído para usuários que fizeram stake de ethDYDX no pool de staking de segurança. Mais informações sobre o pool de staking de segurança podem ser encontradas [aqui](https://dydx.foundation/blog/en/safety-staking).

Como parte das [recompensas de pool de staking de segurança](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool), 383.562 em $ethDYDX serão distribuídos por epoch (28 dias) para os stakers. As recompensas são distribuídas proporcionalmente ao dia aos stakers.

A comunidade da dYdX tem "controle imediato e irrevogável sobre" os parâmetros do contrato inteligente do módulo de segurança. A lista completa de parâmetros que a comunidade controla está [aqui](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

Em 8 de setembro, às 15:00 UTC, a restrição de transferência nos tokens $ethDYDX foi removida e efetivamente aberta para staking no Módulo de Segurança da dYdX. Mais de 50 endereços diferentes fizeram o staking de aproximadamente 157 mil ethDYDX ao longo de quase 1 hora. Um bug causou um erro no processo de implantação e nenhum stkDYDX foi emitido para os endereços que fizeram stake no módulo de segurança. Como resultado, os fundos de cada staker ficaram presos no contrato e a equipe da dYdX desabilitou o staking na UI de governança da dYdX.

A [DIP 1](https://dydx.community/dashboard/proposal/0) propôs restaurar a funcionalidade para o módulo de segurança e permitir que os endereços afetados recuperassem os fundos e recebessem um adicional de 10% em tokens em staking como compensação. Embora o sentimento da comunidade fosse fortemente a favor da [DIP 1 — Restauração de módulo de segurança e recuperação para stakers](https://dydx.community/dashboard/proposal/0), a proposta não foi aceita porque não cumpriu o quórum mínimo de 100 milhões em $ethDYDX necessário para que o voto de timelock longo fosse aprovado. Como resultado, Jacob Goh (jteam0x) da DeFiance Capital criou a [Reembolso e compensação de stakers no módulo de segurança](https://dydx.community/dashboard/proposal/2) para reembolsar e compensar os endereços afetados por recompensas e inconveniências. [A DIP 4](https://dydx.community/dashboard/proposal/2) envolveu a implantação do contrato de recuperação de tokens em staking de usuários e a compensação dos endereços afetados com um adicional de 10% do Tesouro de recompensas. A DIP foi governada pelos parâmetros de governança menos rigorosos de um timelock curto.

Geralmente, o ciclo de vida de uma DIP é consistente com a criação da DIP. A principal diferença entre a DIP 3 (on-chain) e a DIP 2 (off-chain) foi que a DIP 3 exigiu uma votação on-chain e a implantação do contrato inteligente. Como o processo dos fóruns de discussão, criação de DRC e criação de DIP em rascunho são os mesmos, iniciamos nossa discussão passo a passo com os requisitos de conteúdo para o rascunho de um DIP on-chain. Para obter mais informações siga os links abaixo:

* Processo de governança da dYdX - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
* Relatório de incidentes do módulo de segurança - [https://dydx.foundation/blog/en/outage-1](https://dydx.foundation/blog/en/outage-1).
* Discussão do fórum Off-Chain **-** [https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause).
* DRC Off-Chain **-** [https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* Pesquisas de snapshot de DRC Off-Chain **-** [https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* DIP proposta na Github **-** [https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **PASSO 1 — Rascunho de DIP on-Chain**

_**Descrição:**_

Elaboração de uma DIP on-chain que afeta o consenso da governança no protocolo da dYdX deve seguir as etapas específicas para implementar alterações no contrato inteligente. Após a comunidade atingir um consenso a partir do snapshot ou de uma DIP que falhou anteriormente, um membro da comunidade com poder de proposição suficiente pode enviar a nova DIP on-chain. Mais informações sobre o limiar de poder de proposição, o executor de timelock e outros parâmetros de governança estão detalhadas [aqui](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

_**Envio da DIP 3:**_

Neste caso, a [DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md) foi escrita por Dan Robinson da Paradigm. Devido a proposta incluir alterações no contrato inteligente on-chain, a proposta incluiu um link para as implementações específicas do contrato inteligente.

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/2-dip3-example-1.png)

Navegando do contrato de implantação SafetyModuleV2.sol para a pasta Segurança, encontramos o arquivo README que contém os detalhes específicos de como a proposta será implementada.

![](../.gitbook/assets/2-dip3-example-1a.png)

Os passos para implementar a proposta incluída no README estão detalhados aqui: [https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety).

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-2.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-3.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-4.png)

#### _Como elaborar uma DIP on-Chain (WIP):_

* Crie uma nova carteira para criar a DIP. O processo de implantação exigirá que você insira sua seed phrase como uma variável de ambiente. Desse modo, recomendamos que você use uma carteira de único uso para a criação da DIP on-chain.
* Delegue poder de proposição suficiente para a carteira a fim de criar a DIP. Você pode delegar o poder de proposição [aqui](https://dydx.community/dashboard). Os diferentes limiares de poder de proposição estão incluídos abaixo e estão detalhados [aqui](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).
  * Timelock curto: 0,5% do fornecimento total (5 milhões em poder de proposição).
  * Executor de Starkware: 0,5% do fornecimento total (5 milhões em poder de proposição).
  * Executor de timelock longo: 2,0% do fornecimento total (20 milhões em poder de proposição).
  * Executor Merkle Pauser: 0,5% do fornecimento total (5 milhões em poder de proposição).
* Crie uma chave Alchemy. Com a chave Alchemy, você não precisa executar um node Ethereum para interagir com a rede Ethereum e implementar o contrato inteligente. O guia para criar uma chave Alchemy está detalhado [aqui](https://docs.alchemy.com/alchemy/introduction/getting-started).

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-1.png)

Escolha Ethereum e “Get Started (Começar)”.

![](../.gitbook/assets/2-draft-dip-example-2.png)

Preencha as informações necessárias, selecione a rede Goerli e selecione “create app" (criar aplicativo).

<figure><img src="../.gitbook/assets/2-draft-dip-example-3.png" alt=""><figcaption></figcaption></figure>

Depois de criar sua conta, siga as instruções de configuração fornecidas [aqui](https://docs.alchemy.com/alchemy/introduction/getting-started).

Em “4. Start Building (4. Começar a criar)”, selecione “try deploying your first smart contract (tente implantar seu primeiro contrato inteligente)” e siga o guia.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-4.png)

* Abra a linha de comando do Windows, o terminal padrão de aplicativos ou baixe o iTerm: [https://iterm2.com/](https://iterm2.com/).
* Baixe e instale o Node.js e o npm, se você ainda não os tiver, em: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* O Hardhat é uma ferramenta de desenvolvimento para compilar e testar o software Ethereum. Instale o Hardhat, se você ainda não o tiver, em: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Projete sua implementação de contrato inteligente proposto.
* O hash do IPFS é gerado automaticamente e pode ser obtido [aqui](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips). O hash de IPFS estará no diretório da dYdX Foundation, sob o nome do arquivo `DIP-[New DIP #]-ipfs-hashes.json`.

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](../.gitbook/assets/2-draft-dip-example-5.png)

* Depois de selecionar o novo arquivo (`DIP-[New DIP #]-ipfs-hashes.jso`), certifique-se de que você usará encodedHash.

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](../.gitbook/assets/2-draft-dip-example-6.png)

### **PASSO 2 — Envio de uma DIP on-chain**

_**Descrição:**_

Após um membro da comunidade confirmar que a implementação do contrato inteligente proposto está correto e a DIP é finalizada, ela poderá ser enviada on-chain. Quando uma DIP on-chain é criada, a proposta entra em um estado “Pending (Pendente)” para o atraso de votação, que dura aproximadamente 1 dia (aproximadamente 6570 blocos). Os snapshots do usuário são registrados após o atraso de votação a fim de contabilizar as participações $ethDYDX e o poder de votação delegado. Em seguida, a proposta entra em um estado “Active (Ativo)” e a extensão da votação varia de 2 a 10 dias, dependendo do tipo da proposta. Para que uma proposta seja implementada, a votação deve passar o quórum e o diferencial de voto mínimos que são diferentes dependendo do tipo de proposta. Se a DIP satisfizer o quórum mínimo, o diferencial de votação mínima e a maioria dos membros da comunidade de votação a favor da DIP, qualquer endereço poderá chamar a função de fila e mover a proposta para a fila do timelock. Os contratos timelock podem ser enfileirados, cancelados ou ter transações executadas votadas pela comunidade da dYdX. A extensão da fila do timelock varia dependendo do tipo de proposta.

_**Envio da DIP 3:**_

A equipe da Paradigm finalizou o código em solidity para `SafetyModuleV2.sol.`

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/2-draft-dip-example-7.png)

A equipe da Paradigm simulou as atualizações em um ambiente local e em um ambiente mainnet em fork. O conjunto de testes foi então executado para garantir que a funcionalidade seria restaurada, seguindo a execução da proposta de governança na mainnet.

A equipe da Paradigm implantou as atualizações do contrato inteligente executando os scripts abaixo.

**Implantação de recuperação do módulo de segurança**

`export ALCHEMY_KEY=<… >`

`export MNEMONIC=<… >`

`npx hardhat --network mainnet deploy:safety-module-recovery`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**Proposta de Governança: resolução do módulo de segurança**

`export ALCHEMY_KEY=<… >`

`export MNEMONIC=<… >`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\
`--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\
`--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\
`--safety-module-new-impl-address 0x...`

**Proposta de Governança: compensação do módulo de segurança**

`export ALCHEMY_KEY=<… >`

`export MNEMONIC=<… >`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\
`--safety-module-recovery-address 0x...`

A DIP foi publicada simultaneamente em [https://dydx.community/dashboard](https://dydx.community/dashboard).

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-8.png)

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-9.png)

O contrato de governança da dYdX é o 0x7e9b1672616ff6d6629ef2879419aae79a9018d2: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).

A implantação da DIP pode ser confirmada em Etherscan: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

A DIP foi criada em 1º de novembro de 2021, no bloco 13532376. Para 6570 blocos no futuro, o status da DIP é “Pending (Pendente)”.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-10.png)

Os holders da ethDYDX puderam votar na DIP quando ela foi para um estado “Active (Ativa)” no bloco 13538946.

A primeira votação foi lançada em 2 de novembro de 2021, às 17:51:22 UTC (bloco 13538959), 6583 blocos a partir da criação on-chain da DIP.

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/2-draft-dip-example-11.png)

Após o período de votação de 10 dias com um timelock longo, qualquer membro da comunidade pode chamar a fila e mover a proposta para o atraso de timelock de 7 dias. Para a DIP 3, foram precisos quase 3 dias para que um membro da comunidade chamasse a fila.

![https://etherscan.io/tx/0x3402372aa549d2270a6b5d4f84884ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/2-draft-dip-example-12.png)

Após o atraso de timelock de 7 dias, a DIP foi executada on-chain.

![https://etherscan.io/tx/0xfd332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/2-draft-dip-example-13.png)

No momento em que a DIP foi executada on-chain o status das DIPs em [https://dydx.community/dashboard/proposal/3](https://dydx.community/dashboard/proposal/3) foi atualizado para “Executed (Executada)”.

![](../.gitbook/assets/2-draft-dip-example-14.png)

Observações: (1) propostas devem ser executadas dentro do período de carência de execução de 7 dias, que começa imediatamente após o atraso de timelock e (2) o endereço de proposição deve manter o valor mínimo de poder de proposição exigido pelo respectivo contrato de timelock até que a DIP seja executada (5 ou 20 milhões em poder de proposição).

#### _Como enviar uma DIP on-Chain:_

* Certifique-se de que você tenha poder de proposição suficiente para criar a DIP. Mais informações podem ser encontradas em [Criação de DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
  * Executor do timelock curto: 0,5% do fornecimento total (5 milhões em poder de proposição).
  * Executor de Starkware: 0,5% do fornecimento total (5 milhões em poder de proposição).
  * Executor de timelock longo: 2,0% do fornecimento total (20 milhões em poder de proposição).
  * Executor Merkle Pauser: 0,5% do fornecimento total (5 milhões em poder de proposição).
* Certifique-se de que haja ETH na carteira para pagar a taxa de gás.
* Crie um aplicativo na Alchemy para a rede Ethereum Mainnet.

![https://dashboard.alchemyapi.io/](../.gitbook/assets/2-draft-dip-example-15.png)

* Após a criação do aplicativo, clique em “View Key (Exibir chave)” para obter sua chave Alchemy (7LOaQtguSm2kSEcFXQH88B): [https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul).

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](../.gitbook/assets/2-draft-dip-example-16.png)

* Baixe e instale o Node.js e o npm: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Instale o Hardhat: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Execute o script que você planejou.
* Confira o contrato de governança para verificar se a proposta foi criada on-chain: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).
* Com o endereço que enviou a proposta, você deve manter o valor mínimo de poder de proposição exigido pelo contrato de timelock respectivo até que a proposta seja executada.

#### _Como Votar em uma DIP:_

* Certifique-se de que haja ETH na carteira para pagar a taxa de gás.
* Você pode votar em uma DIP ativo selecionando-a em: [https://dydx.community/dashboard](https://dydx.community/dashboard).

![](../.gitbook/assets/2-draft-dip-example-17.png)

O comprimento de votação depende do tipo de proposta. Mais informações podem ser encontradas em [Criação de DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

* Executor de timelock curto: 4 dias.
* Executor de Starkware: 4 dias.
* Executor de timelock longo: 10 dias.
* Executor Merkle Pauser 2 dias.

#### _Como enfileirar uma proposta:_

Uma proposta bem-sucedida pode ser enfileirada para iniciar o atraso de timelock.

* Certifique-se de que você esteja usando uma carteira compatível que tenha Eth.
* Acesse a guia “Contract (Contrato)” na Etherscan e clique em “Write Contract (Criar contrato)”. O contrato de governança se encontra [aqui](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-queue-1.png)

* Selecione a fila e envie o “proposalId (ID da proposta)”.

![](../.gitbook/assets/2-draft-dip-example-queue-2.png)

O “proposalId (ID da proposta)” pode ser encontrado na Etherscan quando a DIP foi criada: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

* Selecione “click to see more (clique para exibir mais)”.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-3.png)

* Selecione “Decode Input Data (Decodificar dados de entrada)”.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-4.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-5.png)

#### _Como executar uma proposta:_

Após o atraso de timelock, uma proposta bem-sucedida pode ser executada.

* Acesse a guia “Contract (Contrato)” na Etherscan e clique em “Write Contract (Criar contrato)”. O contrato de governança se encontra [aqui](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-1.png)

* Selecione “execute (executar)” e envie o “proposalId (ID da proposta)”.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-2.png)

* Siga as etapas acima (em _Como enfileirar uma proposta)_ para encontrar o “proposalId (ID da proposta)”.
* Digite ”0” em “payableAmount (ether) (Quantia a ser paga (ether))”.
