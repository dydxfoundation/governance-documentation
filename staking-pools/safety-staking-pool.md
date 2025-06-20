---
description: Uma visão geral do pool de staking de segurança
hidden: true
---

# 🔐 Módulo de segurança

O módulo de segurança não está mais ativo desde 28 de novembro de 2022. No [DIP 17](https://dydx.community/dashboard/proposal/9), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/7) para reduzir efetivamente o Módulo de Segurança ao definir as recompensas do Módulo de Segurança por segundo para 0.\

Todos os ethDYDX restantes da alocação de recompensas do módulo de liquidez foram migrados para a tesouraria da comunidade da blockchain dYdX.

Mais informações sobre a tesouraria da comunidade da blockchain dYdX estão disponíveis [aqui](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury).



## Sem remoção do staking e retiradas da DYDX

Os stakers devem solicitar saques de fundos pelo menos `3 dias` **(janela de bloqueio**) antes do final da epoch, para poderem sacar $ethDYDX após o final daquela epoch. Se os stakers não solicitarem o saque, seus $ethDYDX em staking acumularão para a próxima epoch.

Os saques não podem ser solicitados durante a **janela de bloqueio**.

Na [DIP 17](https://dydx.community/dashboard/proposal/9), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/7) para reduzir a duração da janela de bloqueio de `14 dias` para `três dias`.

## Perguntas frequentes

<details>

<summary>O que é a janela de bloqueio?</summary>

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques de $stkDYDX. A função `requestWithdrawal` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos `3 dias` de uma epoch. Novas epochs começam a cada 28 dias. Desse modo, os usuários podem solicitar um saque para a próxima epoch até `três dias` antes do final de uma determinada epoch.

</details>

<details>

<summary>Como posso sacar os fundos do pool de staking? Quanto tempo demora?</summary>

Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de fundos no pool. Um staker deve solicitar o saque dos fundos pelo menos `três dias` antes do final de uma epoch, para poder sacar seus fundos após o final daquela epoch. Se os stakers não solicitarem o saque, seus $ethDYDX em staking acumularão para a próxima epoch.

Para sacar os fundos, os usuários chamam a função ``"requestWithdrawal" `` para solicitar o saque de fundos para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função ``"withdrawStake" `` para sacar os fundos inativos para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função ``"withdrawMaxStake"`` para sacar todos os fundos inativos. Considere que a função ``"withdrawMaxStake"`` é menos eficiente em termos de gás do que a consulta do valor máximo via eth\_call e a chamada ``"withdrawStake()"``.

Para sacar $ethDYDX do módulo de segurança, siga estas etapas:

* Acesse [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Clique em “**Solicitar**” e digite o valor de $ethDYDX que você deseja sacar do pool.
* Clique em “**Solicitar saque**”. Será necessário pagar as taxas de gas para sacar os fundos.
* Os stakers que solicitarem sacar $ethDYDX pelo menos `3 dias` antes que a epoch atual termine poderão sacar seus $ethDYDX no início da próxima epoch.

</details>

