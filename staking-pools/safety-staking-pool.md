---
description: Uma visão geral do pool de staking de segurança
---

#

Inicialmente, 2,50% do fornecimento de token (25.`000.00``0 $ethDYDX`) foram alocados para serem distribuídos aos usuários que fazem staking de $USDC para o módulo de segurança. O Módulo de Segurança não está mais ativo desde 28 de novembro de 2022.

Anteriormente, $ethDYDX era distribuída para usuários que fizessem stake da $ethDYDX no Módulo de Segurança. O Módulo de Segurança era um fundo descentralizado que deveria ser usado no caso de insolvência ou outros problemas com o protocolo DYDX.



## Visão geral

Atualmente, o $ethDYDX em staking no Módulo de Segurança não está ganhando recompensas.



## Sem remoção do staking e retiradas da DYDX

Os stakers devem solicitar saques de fundos pelo menos `3 dias` **(janela de bloqueio**) antes do final da epoch, para poderem sacar $ethDYDX após o final daquela epoch. Se os stakers não solicitarem o saque, sua $ethDYDX em staking acumulará para a próxima epoch.

Os saques não podem ser solicitados durante a **janela de bloqueio**.

No [DIP 17](https://dydx.community/dashboard/proposal/9), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/7) para reduzir a duração da janela de bloqueio de `14 dias` para `3 dias`.

## Perguntas e respostas

<details>

<summary>O que é a janela de bloqueio?</summary>

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques de $stkDYDX. A função `requestWithdrawal` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos `3 dias` de uma epoch. Novas epochs começam a cada 28 dias. Desse modo, os usuários podem solicitar um saque para a próxima epoch até `3 dias` antes do final de uma determinada epoch.

</details>

<details>

<summary>Como posso sacar os fundos do pool de staking? Quanto tempo demora?</summary>

Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de fundos no pool. Um staker deve solicitar o saque dos fundos pelo menos `3 dias` antes do final de uma epoch, para poder sacar seus fundos após o final daquela epoch. Se os stakers não solicitarem o saque, sua $ethDYDX em staking acumulará para a próxima epoch.

Para sacar os fundos, os usuários chamam a função ``"requestWithdrawal"`` para solicitar o saque de fundos para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função ``"withdrawStake"`` para sacar os fundos inativos para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função ``"withdrawMaxStake"`` para sacar todos os fundos inativos. Considere que a função ``"withdrawMaxStake"`` é menos eficiente em termos de gás do que a consulta do valor máximo via eth\_call e a chamada ``"withdrawStake()"``.

Para sacar $ethDYDX do Módulo de Segurança, siga estas etapas:

* Visite [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Clique em “**Solicitar**” e digite o valor de $ethDYDX que deseja sacar do pool.
* Clique em “**Solicitar saque**”. Será necessário pagar as taxas para sacar os fundos.
* Os stakers que solicitarem sacar $ethDYDX pelo menos `3 dias` antes que a epoch atual termine poderão sacar seus $ethDYDX no início da próxima epoch.

</details>

