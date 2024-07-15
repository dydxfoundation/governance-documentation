---
description: Uma visão geral de alto nível da arquitetura de governança.
---

#

## Visão geral

$ethDYDX, $stkDYDX e $wethDYDX ("Tokens de Governança") concedem aos detentores o direito de propor e votar em alterações na dYdX v3. A governança da dYdX é baseada nos contratos de governança da AAVE e suporta a votação com base nos ativos dos Tokens de Governança.

As propostas devem passar em um determinado limiar e porcentagem de votos com base no tipo de proposta.



Há oito contratos inteligentes no núcleo da governança da dYdX:

* **Os contratos `de token $ethDYDX, $stkDYDX e $wethDYDX`**: têm snapshots do poder de votação de cada endereço em diferentes blocos no tempo.
* **O contrato `de estratégia de governança V2`**: contém lógica para medir o poder relativo dos usuários para propor e votar. A comunidade da dYdX [votou](https://dydx.community/dashboard/proposal/15) para atualizar o contrato `de estratégia de governança` para a `estratégia de governança V2` para conceder ao $wethDYDX a mesma funcionalidade de governança do ethDYDX para votação e proposição na governança da dYdX v3.
*
* **Contrato de `governador`**: rastreia propostas e as executa por meio de contratos inteligentes de timelock.
* **Contratos de `timelock`**: podem enfileirar, cancelar ou executar transações votadas pela Governança. As funções em uma proposta são iniciadas pelo contrato timelock. As transações em fila podem ser executadas após um atraso e antes do término do período de carência.
* **Contrato `de timelock de prioridade`**: o mesmo que o contrato de timelock, mas que permite que um controlador de prioridade execute transações dentro do **período** de prioridade (7 dias) antes do fim do atraso de timelock.

![Arquitetura do contrato inteligente](../.gitbook/assets/1-smart-contract-architectue.png)

A governança da dYdX on-chain permite:

* Votação de propostas a serem executadas por qualquer contrato executor autorizado
* Criação de snapshots de tokens no início de uma proposta
* Separação de delegação de poderes de votação e de proposição
* Definição dos limites da governança, incluindo propostas, quóruns e poderes diferenciais de votação
* Alteração de como os votos são contados (alterando o endereço de contrato inteligente “Estratégia de Governança” no contrato de governador)

## Tipos de proposta

Um executor deve validar cada tipo de proposta.

#### **Executor de timelock curto**

O executor de timelock curto controla o seguinte:

* Contratos de incentivo incluindo o módulo de liquidez, módulo de segurança e módulo de distribuidor Merkle
* fundos nas recompensas e Tesouros da Comunidade
* mint de novos tokens
* todos os contratos de proxy, exceto o módulo de segurança
* funções de guardião nos contratos de proxy da Stark

**Executor de timelock de prioridade de Starkware**



#### **Executor de timelock longo**

O executor de timelock longo pode realizar propostas que geralmente alteram partes da dYdX v3 e afetam o consenso de governança.

#### **Executor Merkle-Pauser**

O executor Merkle-pauser é capaz de executar propostas que congelam a raiz Merkle, que é atualizada periodicamente com o saldo de recompensas cumulativa de cada usuário. Isso permite que novas recompensas sejam distribuídas aos usuários ao longo do tempo, caso a raiz proposta esteja incorreta ou seja maliciosa. Também pode vetar solicitações de trades forçadas por qualquer um dos contratos de proxy da Stark.

Os parâmetros de timelock iniciais são os seguintes:

![Parâmetros de timelock iniciais](../.gitbook/assets/1-initial-timelock-parameters.png)
