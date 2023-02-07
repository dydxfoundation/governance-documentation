---
description: Uma visão geral do pool de staking de segurança
---

# Módulo de segurança

`0,5%` do fornecimento de token (`5.049.079 $DYDX)` foi distribuído a usuários que fizeram staking de DYDX em um pool de segurança para a proteção do sistema. Inicialmente, `2,50%` do fornecimento de tokens iniciais (`25.000.000 DYDX`), foram alocados para distribuição a usuários que fazem stake de $DYDX no Módulo de Segurança. O Módulo de Segurança não está mais ativo desde 28 de novembro de 2022. No [DIP 17](https://dydx.community/dashboard/proposal/9), a comunidade DYDX [votou](https://dydx.community/dashboard/proposal/7) para reduzir efetivamente o Módulo de Segurança ao definir as recompensas do Módulo de Segurança por segundo a 0.\


Anteriormente, $DYDX era distribuída para usuários que fizessem stake da $DYDX no Módulo de Segurança. O Módulo de Segurança era um fundo descentralizado que deveria ser usado no caso de insolvência ou outros problemas com o protocolo DYDX.

A $DYDX em staking no módulo de segurança mantém os direitos de voto e de proposição, assim como as capacidades de delegação.

## Visão geral

Atualmente, o stake de $DYDX feito no Módulo de Segurança não concede recompensas.

As 383.562 $DYDX distribuídas anteriormente para stakers da $DYDX será acumulada no Tesouro de Recompensas e poderá ser usada pela comunidade DYDX com um [voto de governança](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

## Sem remoção do staking e retiradas da DYDX

Os stakers devem solicitar saques de fundos pelo menos `3 dias` **(janela de bloqueio**) antes do final da epoch, para poderem sacar $DYXD após o final daquela epoch. Se os stakers não solicitarem o saque, $DYDX em staking acumulará para a próxima epoch.

Os saques não podem ser solicitados durante a **janela de bloqueio**.

No [DIP 17](https://dydx.community/dashboard/proposal/9), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/7) para reduzir a duração da janela de bloqueio de `14 dias` para `3 dias`.



## Perguntas e respostas

### O que é a janela de bloqueio?

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques de $stkDYDX. A função `requestWithdrawal` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos `3 dias` de uma epoch. Novas epochs começam a cada 28 dias. Desse modo, os usuários podem solicitar um saque para a próxima epoch até `3 dias` antes do final de uma determinada epoch.

### Como posso sacar os fundos do pool de staking? Quanto tempo demora?

Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de fundos no pool. Um staker deve solicitar o saque dos fundos pelo menos `3 dias` antes do final de uma epoch, para poder sacar seus fundos após o final daquela epoch. Se os stakers não solicitarem o saque, $DYDX em staking acumulará para a próxima epoch.

Para sacar os fundos, os usuários chamam a função \`requestWithdrawal\` para solicitar o saque de fundos para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função \`withdrawStake\` para sacar os fundos inativos para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função \`withdrawMaxStake\` para sacar todos os fundos inativos. Considere que a função \`withdrawMaxStake\` é menos eficiente em termos de gás do que a consulta do valor máximo via eth\_call e a chamada \`withdrawStake\(\)\`.

Para sacar $DYDX do Módulo de Segurança, siga estas etapas:

* Visite [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Clique em “**Solicitar**” e digite o valor de DYDX que deseja sacar do pool.
* Clique em “**Solicitar saque**”. Será necessário pagar as taxas para sacar os fundos.
* Os stakers que solicitarem sacar DYDX pelo menos `3 dias` antes que a epoch atual termine poderão sacar seus DYDX no início da próxima epoch.

