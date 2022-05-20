---
description: Visão geral dos pools de staking de liquidez.
---

# Pool de staking de liquidez

2,5% \(`25.000.000 DYDX`\) serão distribuídos aos usuários que fazem staking de USDC em um pool de staking de liquidez.

### Objetivos

* Promover os efeitos da rede de liquidez dYdX

## Visão geral

A liquidez, especialmente quando usada corretamente, é um componente essencial de qualquer exchange bem-sucedida. Para promover ainda mais os efeitos de rede de liquidez e incentivar os provedores de liquidez profissionais, a DYDX será distribuída a usuários que fizerem stake de USDC no pool de staking de liquidez. Os makers de mercado conhecidos e aprovados usarão o USDC em staking para criar os mercados no protocolo, aumentando a liquidez disponível neles. Os makers de mercado não poderão sacar o USDC do protocolo, o que exige que eles usem o USDC apenas no protocolo. No entanto, uma parte de USDC em staking poderia ser perdida se um maker de mercado perdesse os fundos \(por meio de trades não lucrativos\) e não conseguisse repor o pool de staking de liquidez. Os stakers recebem DYDX, que será distribuída continuamente de acordo com a parte em USDC total de cada staker no pool. Um staker deve solicitar para remover o USDC do staker pelo menos `14 dias` \(**janela de bloqueio**\) antes da epoch para poder sacar seu USDC após o final desta epoch. Se os stakers não solicitarem o saque, o USDC em staking acumulará para a próxima epoch.

## Mutuários aprovados

O contrato de pool de staking de liquidez funciona como um sistema de empréstimos sem garantias e de dois lados.

O valor que pode ser sacado depende da porcentagem de alocação de um mutuário e dos fundos totais disponíveis no pool de staking. Tanto a porcentagem de alocação quanto os fundos totais disponíveis podem mudar em momentos predefinidos especificados pela `LS1EpochSchedule`. Os fundos emprestados só podem ser usados na exchange da dYdX Layer 2. Isso é aplicado por meio do contrato de `TrustedBorrowerL2Proxy` que interage com o contrato da exchange L2 \(`StarkPerpetual`\).

Os provedores de liquidez aprovados inicialmente incluem `Wintermute`, `Sixtant`, `Kronos`, `Amber` e `MGNR`, que têm sido ativos na criação de mercados dentro do protocolo desde o lançamento.

| Mutuários pré-aprovados | Porcentagem de alocação inicial | Detalhes sobre os provedores de liquidez |
| :--- | :--- | :--- |
| Wintermute | `X%` a ser designado | [https://dydx.exchange/blog/ama-recap-wintermute](https://dydx.exchange/blog/ama-recap-wintermute) |
| Sixtant | Y% a ser designado | [https://dydx.exchange/blog/ama-recap-sixtant](https://dydx.exchange/blog/ama-recap-sixtant) |
| Kronos \(Wootrade\) | Z% a ser designado | [https://dydx.exchange/blog/ama-recap-wootrade](https://dydx.exchange/blog/ama-recap-wootrade) |
| Amber | Z% a ser designado |  |
| MGNR | Z% a ser designado |  |

Quando os usuários solicitam a remoção dos fundos em staking, o saldo alocado de um mutuário para a próxima epoch pode ficar abaixo do valor que se encontra emprestado no momento. Nesta situação, o mutuário fica responsável por devolver a diferença entre seus saldos emprestados e alocados antes do final da epoch. Se o saldo emprestado de um mutuário for maior do que o da sua alocação no início da próxima epoch, espera-se que este devolva a diferença antes do início da epoch.

Como os mutuários emprestam e reembolsam os fundos, seus saldos emprestados líquidos ficam registrados. O saldo emprestado líquido total entre todos os mutuários também é rastreado. O saldo restante mantido pelo contrato é chamado de saldo não emprestado.

A seguinte igualdade é válida em todos os momentos quando se considera o contrato como um todo:

total ativo + total inativo = total emprestado + total não emprestado

### Governança

A governança da dYdX é responsável por:

* Fazer a auditoria legal sobre os mutuários existentes
* Adicionar novos mutuários no pool de staking
* Alterar as alocações de fundos emprestados para mutuários aprovados
   * As funções \`setBorrowerAllocations\` e \`setBorrowingRestriction\` são chamadas para alterar as alocações de certos mutuários. Elas podem ser usadas para adicionar e remover os mutuários. Os aumentos entram em vigor na próxima epoch, mas as reduções restringirão empréstimos imediatamente. Essas funções não podem ser chamadas durante a janela de bloqueio.
* O tamanho da epoch e a janela de bloqueio são configurados na criação do contrato, mas podem ser alterados pela governança da dYdX

### Contabilização do saldo em stake

Um saldo em staking está em um dos dois estados:

* ativo: disponível para empréstimos; recebe recompensas de staking; não pode ser sacado pelo staker.
* inativo: não disponível para empréstimos; não recebe recompensas; pode ser sacado pelo staker.

Um staker pode ter uma combinação de saldos ativos e inativos. Os fundos são contabilizados por epoch, como mostrado no seguinte exemplo:

As operações seguintes afetam os saldos em staking da seguinte forma:

* depósito: aumenta o saldo ativo.
* solicitar saque: no final da epoch atual, movimenta alguns fundos ativos para inativos.
* saque: diminui o saldo inativo.
* transferência: movimenta alguns fundos ativos para outro staker.

Para codificar o fato de que um saldo pode ser alterado conforme um agendamento ao final de uma determinada epoch, armazenamos cada saldo como uma estrutura de três campos: currentEpoch, currentEpochBalance e nextEpochBalance. Os saldos inativos de um usuário também fazem uso do campo shortfallCounter.

## Perguntas e respostas

### Como posso ganhar recompensas de staking?

Os stakers podem depositar USDC a qualquer momento no pool de staking de liquidez e começar a ganhar recompensas imediatamente. As recompensas da DYDX são obtidas de forma contínua de acordo com a parte de cada staker do pool total. As recompensas podem ser resgatadas e sacadas a qualquer momento.

### Como posso depositar e fazer stake de USDC no pool de liquidez?

Para depositar e fazer stake de fundos, os usuários chamam a [função](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) \`stake\`. Os usuários também podem depositar e fazer stake em nome de outro endereço, chamando a [função](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) \`stakeFor\`.

Para adicionar o USDC ao stake no pool de liquidez, siga as seguintes etapas:

* Clique em “Stake (Fazer stake)”
* É preciso habilitar o USDC na primeira vez que fizer o depósito. Você só fará isso uma vez.
* Digite o valor em USDC que deseja fazer o stake no pool
* Clique em “Stake Funds (Fazer stake dos fundos)”. Você precisará pagar as taxas de gás para fazer stake e desbloquear os fundos

![](https://lh4.googleusercontent.com/caSDz783Gi-asRNYP8Gm8L5qv_yAuJZwEmUAfl8I1MfHecIF2In10IQCqZBCIpxeXl90eT28GGLbZyts8-x9U5w4Y6LBC4kyehMEalsZu_-aI11S6V7nwPrwtcc75m2M8847jFvv)

Os fundos em staking ficam ativos e começam a ganhar recompensas imediatamente.

### Contabilização de recompensas

Os fundos ativos ganham recompensas pelo período em que permanecem ativos. Isso significa que após solicitar um saque de fundos, estes continuarão a ganhar recompensas até o final da epoch. Por exemplo:

No cenário acima, o usuário ganharia recompensas pelo período de t\_0 a t\_2, havendo variações no saldo em staking total nesse período. Se o usuário solicitar apenas um saque por uma parte do saldo, o saldo restante continuará a receber recompensas além de t\_2.

### O que é a janela de bloqueio?

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques dos fundos em staking. A função \`requestWithdrawal\` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos 14 dias de uma epoch. Novas epochs começam a cada 28 dias. Em outras palavras, os usuários podem solicitar um saque para a próxima epoch até 7 dias antes do final de uma determinada epoch.

### Como posso sacar os fundos do pool de staking? Quanto tempo demora?

Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de fundos no pool. Um staker deve solicitar a remoção dos fundos do staking pelo menos 14 dias antes do final de uma epoch, a fim de realizar o saque dos fundos após o final da epoch. Se os stakers não solicitarem o saque, o USDC em staking acumulará para a próxima epoch.

Para sacar os fundos, os usuários chamam a [função](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L73-L83) \`requestWithdrawal\` para solicitar o saque de fundos para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função \`[withdrawStake](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L91)\` para sacar os fundos inativos para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função \`withdrawMaxStake\` para sacar todos os fundos inativos. A função \`withdrawMaxStake\` é menos eficiente em termos de gás do que a consulta do valor máximo via eth\_call e a chamada \`withdrawStake\(\)\`.

### Quais são os riscos de fazer staking no pool de staking de liquidez? O que acontece se um mutuário não pagar sua dívida?

Os empréstimos não garantidos têm um padrão de confiança muito mais alto que deve ser atendido por um mutuário. Os provedores de liquidez não podem sacar o USDC em staking do protocolo, o que exige que eles o usem apenas no protocolo. No entanto, o USDC em staking poderia ser perdido se um provedor de liquidez perdesse fundos e não fosse capaz de restituir suas alocações emprestadas por meio de fontes de financiamento externas.

Neste caso, os fundos inativos podem estar sujeitos a perdas socializadas proporcionalmente no caso de uma inadimplência na qual um mutuário atrasa os pagamentos de fundos que foram solicitados. No caso de não cumprimento de um empréstimo não garantido, um mutuário devedor vai enfrentar danos de reputação significativos.

Solvência do contrato:

A qualquer momento o contrato estará em um dos seguintes estados com base na relação entre os saldos de staking e os emprestados:

| ![](https://lh3.googleusercontent.com/nTJuAC4WSmhOiAGkM6r-YWzy6z2MIHQnydr8U0n-TReAh_gfqD6ZyalxQpYv9RNBsJzrlw78QB_wp9utqBc-PQZipwzWpxDifD1_zEtyVBhYXRl_f8V-iDMwLBO70LQsftDlXrsr) | ![](https://lh3.googleusercontent.com/x_Yev8ZJrYYm8FTDSdoj0jDXEBY_b9xOC69lpQudQdoALQ_tuQFEbFc5hAU6TbpGNCB6J2BsjMwHb59GrCqR52747j45jSC_BmyzyiY72gTRk4oamv35gO8PPZalA43COZF1pgtP) |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/wX37DQoW9oR4OhJzb4hc5ZxPE1X05OPfyETbUv7WTY0b__WH2PydjJoBuQIREHgeWL18GDn7E1ORgGmcre0R6iYPmwSsdFNzBZ7DBPs0wkajjoDBjxDYDPHcet_-dPPAyS1GWL0v) |  |

O contrato se encontrará em estado de insolvência se:

* o saldo em empréstimo total for maior do que o saldo ativo total
* de modo similar: se o saldo inativo total for maior que o saldo não emprestado total
* de modo equivalente: se o saldo total em saques for maior do que o saldo de USDC do contrato

Caso contrário, o contrato estará em solvência.

Como o empréstimo está limitado à proporção de fundos ativos alocados de um mutuário e o saldo inativo só pode aumentar entre as epochs \(exceto no caso de transferências de USDC abertas para o contrato\), o contrato só pode sair do estado de solvência para um de insolvência durante as transições entre epochs.

Um mutuário individual terá sempre pelo menos uma semana antes de seu saldo alocado ficar abaixo do saldo emprestado pendente. Tal transição só pode acontecer entre epochs.

Enquanto o contrato estiver em insolvência, os usuários não poderão sacar todos os fundos que lhes são devidos. Além disso, a situação representa riscos adicionais se houver incertezas quanto à resolução do déficit e quão rapidamente tal situação será resolvida:

1. Os usuários podem perder o interesse em fazer o staking de novos fundos, pois isso pode colocá-los em uma posição onde não será possível recuperar seus fundos.
2. Os usuários atualmente em staking podem “procurar por uma saída”, isto é, sacar os fundos assim que possível, a fim de maximizar suas chances de recuperar os fundos.

As perdas são rastreadas por meio de índices que representam a fração de fundos inativos que foram convertidos em dívida durante um determinado evento de déficit. Cada saldo inativo do staker possui um contador de déficit armazenado em cache, o que representa o número de déficits anteriores quando o saldo foi atualizado pela última vez. Quaisquer perdas incorridas por um saldo inativo refletirão um crédito igual ao do saldo de dívida do staker. Confira LS1DebtAccounting para obter mais informações sobre como o índice é calculado.

Se o contrato estiver em insolvência, a função markDebt\(\) pode ser chamada \(por qualquer pessoa\), visando um mutuário que excedeu sua alocação. O valor saldo emprestado que excede o saldo da alocação é chamado de saldo de dívida. O valor do saldo da dívida é removido do saldo emprestado para um saldo especial usado especificamente para contabilizar a dívida que não foi paga.

Um ajuste igual é feito na contabilização dos fundos em staking. Um valor igual ao valor da dívida é removido de saldos inativos e adicionado a um saldo especial que representa a dívida devida aos stakers. O saldo inativo de cada staker sofrerá um desconto no valor da dívida e eles receberão um valor equivalente na forma de dívida. Desta forma, a perda de insolvência é socializada \(proporcional ao dia)\ em todos os stakers que detêm saldos inativos.

Este processo é mostrado abaixo:

![](https://lh5.googleusercontent.com/2b2e67wVF3DL32NU0ykTVV0PJWaJ_bdmRQRKgx-5c3_qr_nWNYsuE77JviLtbBxXzASEfIp2Fw4hvzRPeM1a7TAIxq0NYUfo3dZLUhChilDpa5Ygq-YugSvNXKmyf2ul3GQM22SZ)

Se o mutuário em dívida devolver o valor da dívida \(ou se outra parte, como a governança, reembolsá-lo em seu nome\), os stakers poderão recuperar os fundos por ordem de chegada.

### O que a dívida representa?

A dívida

### No caso de inadimplência por parte de um mutuário, há algum recurso para os stakers?

Quando a função markDebt\(\) é chamada em um mutuário, e esse mutuário perde o direito de emprestar quaisquer outros fundos do contrato. Este direito pode ser reintegrado pela governança.

Adicionar potencialmente o conteúdo no contrato de maker de mercado com a Fundação

