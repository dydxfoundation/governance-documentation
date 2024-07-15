---
description: Visão geral do ciclo de vida de propostas de melhoria da dYdX (DIP).
---

#

## **Fases da proposta**

O processo de governança da dYdX é alimentado por fóruns de governança em [**https://dydx.forum/**](https://dydx.forum/) e ratificado por meio de propostas de melhoria da dYdX (“DIPs”).

Abaixo descrevemos um rascunho preliminar que explica como o processo de governança da dYdX v3 fluirá desde o início e a definição do conceito até a implementação atual. Esses processos estão sujeitos a alterações conforme o feedback da comunidade da dYdX.

O fluxograma a seguir mostra as etapas iniciais propostas para aprovar uma proposta:

![Etapas de uma DIP](../.gitbook/assets/1-proposal-stage-flow-chart.png)

## 0. Discussão no fórum

Qualquer um pode se inscrever e configurar uma discussão em qualquer tópico nos fóruns de governança da dYdX, que estão hospedados em [**https://dydx.forum/**](https://dydx.forum/). Os membros da comunidade são obrigados a se registrar usando um endereço de e-mail ou carteira Ethereum.

## 1. Criação de DRC (Off-chain)

A criação de **solicitação dYdX de comentários** (DRC, em inglês) é o primeiro passo no processo de melhoria da governança. Qualquer um pode participar do [Fórum de Governança](https://dydx.forum/), criar DRCs off-chain e discutir melhorias.

Para criar um DRC, use [este modelo](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) (disponível em nosso Github). A DRC deve cobrir todas as informações da DIP final em potencial.

No mínimo, as DRCs devem incluir:

* Títulos curtos e concisos para a DRC
* Descrição de proposta curta e concisa
* A lógica para a DRC, por exemplo, por quê?
* O título da postagem no fórum deve incluir DRC: com o título curto da DRC. Por exemplo, DRC: nova solicitação de mercado
* Uma votação comunitária que os membros da comunidade usam para votar em melhorias off-chain

## 2. Discussão e feedback de DRC

Uma vez postados no fórum de governança, todas as perguntas e comentários devem ser abordados e levados em consideração, de modo a melhorar ainda mais a DRC.

## 3. Pesquisas de snapshots de DRC

As pesquisas de snapshots servem a dois fins: análise de sentimento para DIPs on-chain futuras e votos de vinculação para variáveis controladas off-chain.

Uma vez que uma DRC off-chain tenha um consenso muito aproximado, um membro da comunidade com um poder de proposição total de mais de `10.000` Tokens de Governança pode criar um **voto off-chain** para a DRC no **Snapshot**. Incentivamos a comunidade da dYdX a criar pesquisas de snapshots nas segundas-feiras para aumentar a visibilidade durante a semana.

Um snapshot é uma interface simples de votação que permite aos usuários indicar sentimentos off-chain. Os votos em Snapshots são ponderados de acordo com o poder de voto do endereço usado para tal.

Para pesquisas de snapshots relacionadas à sinalização de sentimentos, o proponente precisará fornecer:

* detalhes da DRC,
* um sistema de votação,
* um período de votação — data de início e data de término da votação, definidas em um período de 4 dias e
* um atraso de votação: um número de bloco de Snapshot que é de 6570 blocos (aproximadamente 1 dia com base no tempo de bloqueio de 13,2 segundos) no futuro. O número de bloco do snapshot trava o estado de membros da comunidade que podem votar. Os holders de tokens que tenham tokens antes do número de bloco do snapshot se tornam elegíveis para votar. Antes do snapshot do respectivo poder de voto de cada endereço, o atraso de votação dá aos detentores de Tokens de Governança tempo para adquirir tokens, delegar o poder de voto e mover tokens entre carteiras. Observe que a movimentação entre carteiras se aplica apenas a $ethDYDX e $wethDYDX.

Os votos de snapshot são considerados finais e vinculativos para decisões que não exijam uma chamada no contrato inteligente on-chain e mudanças consideráveis às fórmulas de recompensas de trades a provedores de liquidez. O proponente precisará incluir os requisitos acima e fornecer:

* opções de voto binárias e, para fins de clareza, um endereço vota a favor ou contra uma proposta.

As alterações propostas serão implementadas pela dYdX Trading Inc. se os resultados da pesquisa do snapshot atenderem aos seguintes critérios:

* o quorum mínimo - pelo menos `1.000.000` de Tokens de Governança. O quórum mínimo contribui para a descentralização da tomada de decisões e protege contra a tomada de decisões unilaterais e
* o diferencial de voto mínimo, ou seja, pelo menos 67% dos votos devem ser a favor da proposta. O diferencial de voto mínimo auxilia na filtragem das propostas que são altamente contenciosas e exigem mais discussões.

A dYdX Trading Inc. terá até 1 epoch (28 dias), um período de carência de execução, para implementar alterações de uma pesquisa de snapshot bem-sucedida.

Observações, propostas e votos são apenas mensagens assinadas, armazenadas em IPFS disponíveis por meio do portal da Commonwealth.

## 4. Criação de DIP (on-chain)

Quando um consenso é atingido, uma DIP on-chain pode ser submetida por um membro da comunidade que detenha poder de proposição suficiente para o tipo de proposta. Uma DIP on-chain é iniciada por meio de uma chamada do contrato inteligente. A proposta deve ser baseada no resultado que venceu a votação da DIP off-chain no snapshot e pode consistir em uma ou várias ações, até no máximo de 10 ações por proposta.

A criação de uma DIP está sujeita a um número mínimo de tokens que são mantidos/delegados por uma conta. Um executor de timelock deve ser especificado quando uma proposta é criada. Os parâmetros iniciais são os seguintes (e podem ser modificados pela governança):

| Parâmetro | Descrição | Executor de timelock curto | Executor Merkle-Pauser | Executor de timelock longo | Executor de Starkware |
| ------------------ | ------------------------------------------------ | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Limiar de propostas | Mínimo de tokens mantidos/delegados para criar proposta | 0,5% do fornecimento total | 0,5% do fornecimento total | 2% do fornecimento total | 0,5% do fornecimento total |

## 5. Votação de DIP (on-chain)

Após uma DIP on-chain ser criada, a proposta entra em um estado `pendente` por um período definido pelo **atraso de votação**, que está configurado para `6570` blocos ou aproximadamente 1 dia (assumindo 13,2 segundos por bloco). Em outras palavras, os snapshots de usuário são registrados 1 dia após a DIP ser criada, no momento em que a proposta é alterada para um estado `ativo`.

Após o atraso de votação, o período de votação é ativado. O comprimento do período de votação depende do tipo de proposta.

O gráfico a seguir mostra um fluxograma de estado de DIP:

<figure><img src="../.gitbook/assets/Proposal Lifecycle (1).png" alt=""><figcaption></figcaption></figure>

Depois que uma DIP é criada on-chain, ela fica sujeita a um **atraso de votação**, **período de votação**, **quórum mínimo** e um **diferencial de votação** mínimo. Os parâmetros iniciais são os seguintes:

| Parâmetro | Descrição | Executor de timelock curto | Executor Merkle-Pauser | Executor de timelock longo | Executor de Starkware |
| ----------------- | ----------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Atraso de votação | O número de blocos Ethereum que se deve esperar antes de votar em uma proposta pode começar após uma proposta ser enviada | 6.570 blocos | 6.570 blocos | 6.570 blocos | 6.570 blocos |
| Período de votação\* | Duração na qual as propostas ficam disponíveis para serem votadas | 4 dias | 2 dias | 10 dias | 4 dias |
| Quórum mínimo | Mínimo de votos positivos para uma proposta de DIP passar | 2% do fornecimento total | 1% do fornecimento total | 10% do fornecimento | 2% do fornecimento total |
| Diferencial de votos | É necessário que haja um diferencial entre votos a favor e contra para que uma proposta de DIP passe | 0,5% do fornecimento total | 0,5% do fornecimento total | 10% do fornecimento | 0,5% do fornecimento total |

_\*Temporização baseada em tempos de bloqueio de 13,2 segundos._

Apenas o atraso de votação pode ser modificado por parte da governança, este atraso só pode ser alterado para valores entre (inclusive) o atraso mínimo e máximo. O período de votação, quórum mínimo e diferencial de votos não podem ser alterados.

## 6. Filas de propostas e execução

Depois que uma DIP for aprovada, qualquer endereço poderá chamar o método de fila para mover a proposta para a fila de timelock. Uma DIP só pode ser enfileirada se tiver sido aprovada.

| Parâmetro | Descrição | Executor de timelock curto | Executor Merkle-Pauser | Executor de timelock longo | Executor de Starkware |
| ------------------------ | ------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Atraso de timelock\* | Trata-se do atraso antes da proposta ser executada após uma proposta ser aprovada e enfileirada | 2 dias | 0 dias | 7 dias | 2 a 9 dias |
| Período de carência de execução\* | O tempo após o qual uma proposta se torna executável e durante o qual ela deve ser executada. | 7 dias | 7 dias | 7 dias | 7 dias |
| Atraso mínimo de timelock\* | Atraso mínimo antes de uma proposta ser executada (após o enfileiramento) | 1 dia | 0 dias | 5 dias | 4 dias |
| Atraso máximo de timelock\* | Atraso máximo antes de uma proposta ser executada (após o enfileiramento) | 7 dias | 1 dia | 21 dias | 21 dias |

_\*Temporização baseada em tempos de bloqueio de 13,2 segundos._

Assim que o período de votação terminar e uma proposta tiver sido bem-sucedida, qualquer um pode chamar a função de fila para começar o atraso do timelock.

Para o executor de timelock de prioridade da Starkware, ele tem um período prioritário de 7 dias fora do atraso de timelock de 9 dias. Isso significa que após 9 dias qualquer um pode executar uma proposta. No entanto, a Starkware tem a opção de executar a proposta, no prazo de 2 a 9 dias (o período de prioridade).

Em termos práticos:

* Dias 0 a 2: ninguém pode executar
* Dias 2 a 9: apenas a Starkware pode executar
* Dia 9: qualquer um pode executar

## 7. Cancelamento de propostas (Opcional)

A qualquer momento em um ciclo de vida de DIP, o proponente pode cancelar a DIP. Uma proposta pode ser cancelada por qualquer um antes de ser executada se o proponente não tiver poder de proposição suficiente no bloco atual.

## Perguntas e respostas

### Qual é o propósito do atraso de votação?

O **Atraso de votação** é o número de blocos Ethereum de espera antes que a votação em uma proposta comece após seu envio.

O poder de voto deve ser delegado para um endereço, em sua totalidade, antes de uma proposta ser enviada ou durante o Atraso **de votação** da proposta.

Por enquanto, o **atraso de votação** está definido para `6.570 blocos`, o que é de cerca de 1 dia. Este valor é adicionado ao número do bloco atual quando uma proposta é criada.

No futuro, a governança da dYdX pode votar para aumentar ou diminuir o **atraso de votação**. Embora existam benefícios óbvios para um maior **Atraso de votação.** Isso pode apresentar alguns resultados adversos em potencial, como a exploração de casos de borda.

### Qual é o propósito do limiar de proposta?

Como $ethDYDX e $wethDYDX são ativos de livre comércio, qualquer pessoa pode tentar uma aquisição de governança por meio de compra de mercado. Dito isso, para forçar um voto de má-fé exigiria um mínimo de `5.000.000` de Tokens de Governança no caso de um timelock pequeno; ou `20`.000.000 de Tokens de Governança no caso de um timelock longo. Se não for possível, este valor se mostraria caro e provavelmente custaria mais contabilizando a flutuação de preço em vez do ganho líquido do ataque.

Se um grupo alcançar um consenso malicioso, o atraso do timelock daria aos agentes afetados tempo para sacar seus ativos do protocolo. Isso também seria uma oportunidade para fazer um fork do protocolo, um caminho que provavelmente seria tomado pelos atores de boa-fé restantes.

###
