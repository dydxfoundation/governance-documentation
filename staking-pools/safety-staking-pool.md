---
description: Uma visão geral do pool de staking de segurança
---

# Módulo de segurança

`2,50%` do fornecimento de token inicial (`25.000.000 DYDX`) será distribuído para os usuários que fizerem staking da DYDX em um pool de segurança para a proteção do sistema.

**Objetivos**

* Promover um fundo descentralizado que será usado no caso de insolvência ou outros problemas com o protocolo.
* Incentivar os detentores de DYDX a governar corretamente: os holders da DYDX colocam-se em risco no caso de eventos de diluição, agindo como última proteção e atuando como os governadores de risco dentro do sistema.

A DYDX em staking no módulo de segurança mantém os direitos de voto e de proposição, assim como as capacidades de delegação.

Comece a fazer staking em [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*

## Visão geral

A segurança e a proteção do usuário têm sido fundamental desde o lançamento do protocolo. Por essa razão, tokens DYDX serão distribuídos aos usuários que fizerem stake em DYDX no pool de segurança, de modo a criar uma rede de segurança adicional para os usuários do protocolo. Os stakers receberão DYDX continuamente e de modo proporcional à sua parte total de DYDX no pool.

O pool de segurança entrará em vigor quando a DYDX se tornar transferível, em 8 de setembro de 2021, 15:00 UTC.

## Saques

Os stakers devem solicitar saques de fundos pelo menos `14 dias` **(janela de bloqueio**) antes do final da epoch, a fim de poderem sacar os fundos após o final da epoch. Se os stakers não solicitarem o saque, sua DYDX em staking acumulará para a próxima epoch.

## Riscos

A DYDX em staking pode ser reduzida caso haja um evento de déficit. Reduções ocorrem a critério da governança da DYDX, o que exige uma votação da governança para entrar em vigor.

Como os participantes em qualquer protocolo de DeFi, os stakers no módulo de segurança ficam expostos ao risco do contrato inteligente, caso haja uma vulnerabilidade no código de contrato. Todos os contratos inteligentes DYDX e de governança foram auditados e rigorosamente testados.

## Eventos de déficit

A interpretação para a ocorrência de um evento de déficit está sujeita a uma votação por parte da governança da dYdX. No entanto, isso pode incluir:

* Solvência de Exchange (por exemplo, a exchange ficar sem garantias devido a liquidações não lucrativas)
* Ataques ao contrato inteligente
* Outros eventos que resultem em um déficit, de acordo com a governança da dYdX

Em um evento de déficit, os saldos do detentor de tokens podem ser reduzidos e transferidos para outro endereço ou contrato (definido pela governança da dYdX caso a caso). A governança da dYdX deve propor um timelock curto para reduzir os tokens em staking. Após a decisão da governança de reduzir os tokens DYDX em staking, as DYDX reduzidas podem ser leiloadas no mercado, sendo negociadas por outros ativos a fim de mitigar o déficit incorrido.

## Perguntas e respostas

### Como posso ganhar recompensas de staking?

Os stakers podem depositar DYDX a qualquer momento no pool de staking de segurança e começar a ganhar recompensas imediatamente. As recompensas DYDX são obtidas de forma contínua de acordo com a parte de cada staker do pool total, segundo a segundo. As recompensas podem ser resgatadas e sacadas a qualquer momento.

Os fundos ativos ganham recompensas pelo período em que permanecem ativos. Isso significa que após solicitar um saque de fundos, estes continuarão a ganhar recompensas até o final da epoch. Isso é mostrado no seguinte exemplo do [pool de staking de liquidez](https://docs.dydx.community/dydx-governance/staking-pools/liquidity-staking-pool):

![](<../.gitbook/assets/image (65).png>)

No cenário acima, o usuário ganharia recompensas pelo período de **Time0** a **Time2**, havendo variações no saldo em staking total nesse período. Se o usuário solicitar apenas um saque por uma parte do saldo, o saldo restante continuará a receber recompensas além de **Time2**.

### Como posso depositar e fazer stake de DYDX no pool de segurança?

Para fazer stake de DYDX no pool de segurança, siga estas etapas:

* Visite [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Clique em “**Stake (Fazer stake)**”
* É preciso habilitar a DYDX na primeira vez que fizer o depósito. Você só terá de fazer isso e pagar a taxa de gás uma vez.
* Digite o valor de DYDX com o qual deseja fazer o stake no pool.
* Clique em “**Fazer stake de fundos**”. Você precisará pagar as taxas de gás para fazer stake ou remover os fundos dele.

Os fundos em staking ficam ativos e começam a receber recompensas imediatamente.

Para depositar e fazer stake com os fundos diretamente no contrato inteligente, os usuários podem chamar a [função](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) \`stake\`. Os usuários também podem depositar e fazer stake em nome de outro endereço, chamando a [função](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) \`stakeFor\`.

### O que é o stkDYDX?

Para contribuir com a segurança do protocolo e receber os incentivos, os detentores de tokens DYDX depositarão seus tokens no módulo de segurança. Em troca disso, receberão uma posição em tokenização (**stkDYDX**) que pode ser sacada ou transferida como ERC-20. O token **stkDYDX** tem os mesmos direitos de voto e de proposição da DYDX na governança da dYdX.

### O que é a janela de bloqueio?

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques dos fundos em staking. Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de fundos no pool. Um staker deve solicitar a remoção de fundos em stake antes da janela de bloqueio para poder sacar seus fundos após o final da epoch. Se um staker não solicitar o saque, seus fundos em staking serão mantidos para a próxima epoch.

A janela de bloqueio recomendada para o pool de segurança é de `14 dias`.

### Como funciona a contabilização do saldo em staking?

Um saldo em staking está em um dos dois estados:

* **Ativo**: disponível para empréstimos; recebe recompensas de staking; não pode ser sacado pelo staker.
* **Inativo**: não disponível para empréstimos; não recebe recompensas; pode ser sacado pelo staker.

Um staker pode ter uma combinação de saldos ativos e inativos. Os fundos são contabilizados por epoch, como mostrado no seguinte exemplo:

![](<../.gitbook/assets/image (36) (1).png>)

As operações seguintes afetam os saldos em staking da seguinte forma:

* **Depósito**: aumenta o saldo ativo.
* **Solicitar** **saque**: no final da epoch atual, movimenta alguns fundos ativos para inativos.
* **Saque**: diminui o saldo inativo.
* **Transferência**: movimenta alguns fundos ativos para outro staker.

Para codificar o fato de que um saldo pode ser alterado conforme um agendamento ao final de uma determinada epoch, armazenamos cada saldo como uma estrutura de três campos: currentEpoch, currentEpochBalance e nextEpochBalance.

### Como posso sacar os fundos do pool de staking? Quanto tempo demora?

Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de fundos no pool. Um staker deve solicitar o saque dos fundos pelo menos `14 dias` antes do final de uma epoch, a fim de realizar o saque dos fundos após o final da epoch. Se os stakers não solicitarem o saque, sua DYDX em staking acumulará para a próxima epoch.

Para sacar os fundos, os usuários chamam a função \`requestWithdrawal\` para solicitar o saque de fundos para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função \`withdrawStake\` para sacar os fundos inativos para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função \`withdrawMaxStake\` para sacar todos os fundos inativos. Considere que a função \`withdrawMaxStake\` é menos eficiente em termos de gás do que a consulta do valor máximo via eth\_call e a chamada \`withdrawStake\(\)\`.

Para sacar a DYDX do pool de liquidez, siga estas etapas:

* Visite [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Clique em “**Solicitar**” e digite o valor de DYDX que deseja sacar do pool.
* Clique em “**Solicitar saque**”. Será necessário pagar as taxas para sacar os fundos.
* Os stakers que solicitarem o saque de DYDX pelo menos 14 dias antes que a epoch atual termine poderão sacar sua DYDX no início da próxima epoch.

### Quais são os riscos para os stakers no pool de staking de segurança? O que acontece caso haja um evento de déficit?

A decisão de um staker de bloquear DYDX no pool de segurança o expõe ao risco de um evento de déficit, o que pode resultar na redução dos fundos DYDX do stake, sendo mediada a critério da governança da DYDX.

Todos os fundos no contrato, ativo ou inativo, são reduzidos. Dentro do contrato, a redução é implementada por meio de uma atualização na taxa de câmbio entre DYDX e stkDYDX. Isso significa que, à medida que ocorram reduções, a taxa de câmbio entre DYDX e stkDYDX divergirá do valor inicial de 1:1. Observe que o recebimento de recompensas de staking não é afetado pelas reduções.
