---
description: Uma visão geral do pool de staking de liquidez
---

# 🔋 Módulo de liquidez

A pool de staking de liquidez não estará mais ativa a partir de 29 de setembro de 2022. Na [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), a comunidade dYdX votou [para](https://dydx.community/dashboard/proposal/7) reduzir efetivamente o pool de staking de liquidez e o pool de empréstimo definindo as recompensas de staking de liquidez por segundo para 0.

Todos os ethDYDX restantes da alocação de recompensas do módulo de liquidez foram migrados para a tesouraria da comunidade da blockchain dYdX.

Mais informações sobre a tesouraria da comunidade da blockchain dYdX estão disponíveis [aqui](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules-and-parameters/community-treasury).

## Visão geral do **staking**

Atualmente, $USDC em staking no pool de staking de liquidez não está distribuindo recompensas.

## Remoção de staking e saques de USDC

Um staker deve solicitar saques de $USDC pelo menos `três dias` (**janela de bloqueio**) antes do final de uma [**epoch**](../start-here/epochs.md) para poder sacar o $USDC do staker após o final daquela epoch. Se os stakers não solicitarem o saque, o $USDC em staking acumulará para a próxima epoch.

Os saques não podem ser solicitados durante a **janela de bloqueio**.

## Perguntas frequentes

<details>

<summary>O que é a janela de bloqueio?</summary>

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques de $USDC em staking. A função `requestWithdrawal` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos `três dias` de uma epoch. Novas epochs começam a cada 28 dias. Desse modo, os usuários podem solicitar um saque para a próxima epoch até `3 dias` antes do final de uma determinada epoch.

</details>

<details>

<summary>Como posso sacar $USDC do pool de staking? Quanto tempo demora?</summary>

Um staker precisa solicitar a retirada de staking de $USDC pelo menos `três dias` antes do final de uma epoch para poder sacar o $USDC do staker ao final da epoch. Se os stakers não solicitarem o saque, o $USDC em staking acumulará para a próxima epoch.

Para sacar o $USDC, os usuários chamam a função `requestWithdrawal` para solicitar o saque de $USDC para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função `withdrawStake` para sacar $USDC inativo para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função \`withdrawMaxStake\` para sacar todos os fundos inativos. A função `withdrawMaxStake` é menos eficiente em termos de gás do que consultar o valor máximo via eth\_call e chamar `withdrawStake()`.

Para remover o $USDC do stake para o pool de liquidez, siga as seguintes etapas:

* Visite [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Clique em “**Solicitar**”
* Digite o valor de $USDC que você deseja solicitar para saque do pool e clique em “**Solicitar saque**”. Você precisará pagar as taxas de "gas" para remover o staking de $USDC.
* Os stakers que solicitarem a remoção de $USDC pelo menos `três dias` (**janela de bloqueio**) antes da epoch atual terminar podem sacar seu $USDC no início da próxima epoch.

</details>

###
