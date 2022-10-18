---
description: Uma visão geral de alto nível da arquitetura de governança.
---

# Arquitetura

## Visão geral

A DYDX concede aos titulares o direito de propor e votar em alterações para o protocolo. A governança da DYDX é baseada nos contratos de governança da AAVE e permite a votação com base em participações do token DYDX.

As propostas devem passar em um determinado limiar e porcentagem de votos com base no tipo de proposta.

Estes tokens DYDX podem ser usados para fazer propostas ou votar em propostas de governança, além de poderem ser delegados a outros endereços Ethereum.

Há seis contratos inteligentes no núcleo da governança da dYdX:

* **Contrato do `token DYDX`**: possui snapshots do poder de voto de cada endereço em diferentes blocos ao longo do tempo.
* **Contrato de `estratégia de governança`**: contém lógica para medir o poder relativo dos usuários para propor e votar.
* **Contrato de `módulo de segurança`**: contém a lógica para fazer o stake de tokens DYDX, tokenizar posições e obter recompensas. O token em staking no módulo de segurança mantém os direitos de governança completos.
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

Há quatro tipos de propostas com diferentes parâmetros que afetam o comprimento e a execução de uma proposta, isto é, propostas críticas que afetam o consenso da governança exigem mais tempo de votação e um diferencial de votos mais alto, já as propostas que afetam apenas os parâmetros do protocolo exigem menos tempo de votação e podem ser implementadas rapidamente. Um executor deve validar cada tipo de proposta.

#### **Executor de timelock curto**

O executor de timelock curto controla o seguinte:

* Contratos de incentivo incluindo o módulo de liquidez, módulo de segurança e módulo de distribuidor Merkle
* fundos nas recompensas e Tesouros da Comunidade
* mint de novos tokens
* todos os contratos de proxy, exceto o módulo de segurança
* funções de guardião nos contratos de proxy da Stark

**Executor de timelock de prioridade de Starkware**

O executor de timelock de prioridade de Starkware possui o contrato da StarkEx Perpetual Exchange. Ele pode executar propostas que controlam a configuração da exchange do dYdX Layer 2.

Dependendo da ação a ser tomada, a equipe da Starkware pode precisar envolver-se para implementar corretamente a alteração na exchange. Por esta razão, este executor é fornecido com uma função “controlador de prioridade”, que fornece à Starkware um período de 7 dias (**período de prioridade**) no qual só eles têm a capacidade de desencadear a execução de uma proposta.

A Starkware não tem controle sobre _quais_ alterações do protocolo são feitas. Apenas os holders do token DYDX, por meio da governança da dYdX, têm a capacidade de aprovar ou não alterações no protocolo de exchange.

#### **Executor de timelock longo**

O executor de timelock longo pode executar propostas que geralmente alteram partes do protocolo que afetam o consenso da governança.

#### **Executor Merkle-Pauser**

O executor Merkle-pauser é capaz de executar propostas que congelam a raiz Merkle, que é atualizada periodicamente com o saldo de recompensas cumulativa de cada usuário. Isso permite que novas recompensas sejam distribuídas aos usuários ao longo do tempo, caso a raiz proposta esteja incorreta ou seja maliciosa. Também pode vetar solicitações de trades forçadas por qualquer um dos contratos de proxy da Stark.

Os parâmetros de timelock iniciais são os seguintes:

![Parâmetros de timelock iniciais](../.gitbook/assets/1-initial-timelock-parameters.png)
