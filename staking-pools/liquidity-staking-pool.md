---
description: Uma visão geral do pool de staking de liquidez
---

# Módulo de liquidez

`0,6%` do fornecimento de token (`5.753.430 $DYDX)` foram distribuídos para usuários que fazem staking de USDC para o pool de staking de liquidez. Inicialmente, `2,50%` do fornecimento de tokens iniciais (`25.000.000 DYDX`), foram alocados para distribuição aos usuários que fazem stake de $USDC no pool de staking de liquidez. A pool de staking de liquidez não estará mais ativa a partir de 29 de setembro de 2022. No [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), a comunidade de dYdX [votou](https://dydx.community/dashboard/proposal/7) pela redução efetiva do Pool de staking de liquidez e do Pool de empréstimos, definindo as recompensas do pool de staking de liquidez por segundo como 0.

\\Anteriormente, a $DYDX era distribuída aos usuários que faziam stake de $USDC no Pool de staking de liquidez. Os provedores de liquidez aprovados pela comunidade usaram o USDC em staking para gerar mercados no protocolo dYdX Layer 2, aumentando a liquidez disponível em todos os mercados. Os provedores de liquidez foram restritos de usar fundos emprestados que estejam fora do protocolo dYdX Layer 2.

## Visão geral do **staking**

Atualmente, $USDC em staking no pool de staking de liquidez não está distribuindo recompensas.

Os 383.562 $DYDX anteriormente distribuídos para stakers de $USDC serão acumulados no Tesouro de Recompensas e poderão ser usados pela comunidade dYdX com um [voto de governança](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Remoção do USDC de stake e saques

Um staker deve solicitar saques de $USDC pelo menos `3 dias` (**janela de bloqueio**) antes do final de uma [**epoch**](../start-here/epochs.md) para poder sacar o $USDC do staker após o final da epoch. Se os stakers não solicitarem o saque, o $USDC em staking acumulará para a próxima epoch.

Os saques não podem ser solicitados durante a **janela de bloqueio**.

No [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/7) pela redução do Período de bloqueio de `14` para `3 dias`.

## O que é $stkUSDC?

Os titulares do $USDC que depositam e fazem stake de seu $USDC no pool de staking de liquidez receberão uma posição tokenizada ($**stkUSDC**). O mint de $stkUSDC é feito quando um usuário faz o stake $USDC. O $stkUSDC é queimado quando um usuário faz chamadas da função `withdrawStake`. Na mesma transação na qual o $USDC deixa a carteira de um staker, o $stkUSDC entra na carteira do staker ou vice-versa, quando o valor é retirado do staking.

Um saldo de $stkUSDC pode ser ativo ou inativo. O $stkUSDC ativo pode ser transferido como ERC-20, mas não pode ser sacado. O $stkUSDC inativo pode ser sacado, mas não pode ser transferido. Por exemplo, um usuário pode ter 100 $stkUSDC ativos e inativos na sua carteira e o saldo do usuário será exibido como 200 $stkUSDC. No entanto, uma transferência será revertida se o usuário tentar transferir mais de 100 $stkUSDC.

Um saldo em staking para o qual o staker solicitou um saque antes do final da epoch seria considerado inativo e, portanto, não transferível.

## Perguntas e respostas

### O que é a janela de bloqueio?

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques de $USDC em staking. A função `requestWithdrawal` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos `3 dias` de uma epoch. Novas epochs começam a cada 28 dias. Desse modo, os usuários podem solicitar um saque para a próxima epoch até `3 dias` antes do final de uma determinada epoch.

### Como posso sacar $USDC do pool de staking? Quanto tempo demora?

Um staker precisa solicitar a retirada de $USDC pelo menos `3 dias` antes do final de uma epoch a fim de sacar o $USDC do staker ao final da epoch. Se os stakers não solicitarem o saque, o $USDC em staking acumulará para a próxima epoch.

Para sacar o $USDC, os usuários chamam a função `requestWithdrawal` para solicitar o saque de $USDC para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função `withdrawStake` para sacar $USDC inativo para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função \`withdrawMaxStake\` para sacar todos os fundos inativos. A função `withdrawMaxStake` é menos eficiente em termos de gás do que consultar o valor máximo via eth\_call e chamar `withdrawStake()`.

Para remover o $USDC do stake para o pool de liquidez, siga as seguintes etapas:

* Visite [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Clique em “**Request**” (Solicitação), para abrir o seguinte modal:

![Solicitando saque](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Digite o valor de USDC que deseja solicitar para saque do pool e clique em “**Request withdraw**” (Solicitar saque). Você precisará pagar as taxas de gás para remover o USDC do stake.
* Os stakers que solicitarem a remoção do USDC pelo menos `3 dias` (**janela de bloqueio**) antes da epoch atual terminar podem sacar seu USDC no início da próxima epoch.

### Quais parâmetros a governança pode mudar?

A governança da dYdX é responsável por:

* Recompensas por segundo do staking de USDC no pool de staking de liquidez
* Adicionar novos mutuários e/ou remover os mutuários atuais do pool de staking de liquidez
* Alterar as alocações de USDC emprestadas a mutuários aprovados
  * As funções `setBorrowerAllocations` e `setBorrowingRestriction` são chamadas para alterar as alocações de determinados mutuários. Elas podem ser usadas para adicionar e remover os mutuários. Os aumentos entram em vigor na próxima epoch, mas as reduções restringirão empréstimos imediatamente. Essas funções não podem ser chamadas durante a janela de bloqueio.
* O tamanho da epoch e a janela de bloqueio são configurados na criação do contrato, mas podem ser alterados
