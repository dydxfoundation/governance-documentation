---
description: Visão geral dos parâmetros de governança.
---

# Parâmetros

No momento de lançamento de governança, os holders da DYDX têm controle imediato e irrevogável sobre:

* Alocação do tesouro da comunidade
* Novas listagens de token no protocolo
* Parâmetros de risco para o protocolo
* Alocações de capital para os makers de mercado no pool de staking de liquidez
* Adição de novos makers de mercado à pool de staking de liquidez
* Determinação dos pagamentos de pool de staking de segurança em caso de perda
* Alteração de qualquer uma das recompensas e pools existentes no lançamento
* A governança cuida da parte de contratos

A governança da dYdX tem controle sobre os parâmetros dos seguintes contratos:

* [Timelock](https://github.com/dydxfoundation/governance-docs/tree/28153eacbdaafb32078630fafa7ad64f111ac9ab/voting-and-governance-process/parameters.md#timelock-parameters)
* Timelock de prioridade
* Governador
* Token DYDX
* Tesouro
* Distribuidor Merkle
* Staking de liquidez
* Módulo de segurança
* Stark Proxy
* Stark Perpetual

## Parâmetros de timelock

![](../.gitbook/assets/1-initial-timelock-parameters.png)

## Parâmetros de governador

| Parâmetro | Descrição | Valor |
| ----------------- | ----------------------------------------------------------------------------- | -------------- |
| Atraso de votação | Atraso (em blocos) entre a criação de proposta e a votação dela | 6.570 blocos |
| Adicionar função de executor | Endereço que pode adicionar novos executores | Timelock curto |
| Função de proprietário | Pode alterar a estratégia / atraso de votação / não autorizar os executores + possui outras funções | Timelock longo |

## Token DYDX

| Parâmetro | Descrição | Valor |
| --------- | ------------------------------------------- | -------------- |
| Proprietário | Pode fazer mint de tokens DYDX após restrição de mint | Timelock curto |

## Parâmetros do Tesouro de recompensas

| Parâmetro | Descrição | Valor |
| ----------- | ------------------------------------------------------ | -------------- |
| Proprietário | Pode aprovar ou transferir qualquer token mantido pelo tesouro | Timelock curto |
| Administrador de Proxy | Pode atualizar o contrato | Timelock curto |

##

## Parâmetros do Tesouro da Comunidade

| Parâmetro | Descrição | Valor |
| ----------- | ------------------------------------------------------ | -------------- |
| Proprietário | Pode aprovar ou transferir qualquer token mantido pelo tesouro | Timelock curto |
| Administrador de Proxy | Pode atualizar o contrato | Timelock curto |

##

## Distribuidor Merkle

| Parâmetro | Descrição | Valor |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------- |
| Função de proprietário | Pode atualizar o endereço oracle de recompensas, atualizar o nome de IPNS e é administrador de todas as funções | Timelock curto |
| Função de atualizador de configuração | Pode definir parâmetros de recompensas, alterar o horário de epoch ou alterar o período de atualização de IPFS | Timelock curto |
| Função de pausador | Pode pausar atualizações para a raiz merkle | Timelock Merkle-pauser |
| Função de resumidor | Pode resumir atualizações para a raiz merkle | Timelock curto |
| Função de operador de resgate | Pode resgatar recompensas em nome de um usuário | Proxy de resgates |
| Intervalo | Comprimento de uma epoch | 28 dias |
| Offset | Início da epoch zero | 3 de agosto de 2021 15:00 UTC |
| Nome do IPNS | Nome do IPNS onde os dados de recompensas são publicados | rewards-data.dydx.foundation |
| Período de atualização do IPFS | Período depois do final da epoch após o qual novas estatísticas de exchange sobre a epoch devem estar disponíveis em IPFS por meio do nome do IPNS | 3 minutos |
| Administrador de Proxy | Pode atualizar o contrato | Timelock curto |

##

## Staking de liquidez

| Parâmetro | Descrição | Valor |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------- |
| Função de proprietário | Administrador de todas as funções | Timelock curto |
| Função de definidor de parâmetros da epoch | Pode definir parâmetros da epoch como o intervalo, offset e janela de bloqueio | Timelock curto |
| Função de definidor de taxa de recompensas | Pode definir a taxa de emissão de recompensas | Timelock curto |
| Função de administrador de mutuários | Pode definir alocações do mutuário e permitir/restringir estes de emprestarem | Timelock curto |
| Função de operador de resgate | Pode resgatar recompensas em nome de um usuário | Proxy de resgates |
| Função de operador de stake | Pode manipular os fundos em staking do usuário (por exemplo, executar saques) em nome de um usuário | Timelock curto |
| Função de operador de dívida | Pode diminuir a dívida emprestada e diminuir a dívida de staker | Timelock curto |
| Intervalo | Comprimento de uma epoch | 28 dias |
| Offset | Início da epoch zero | 3 de agosto de 2021 15:00 UTC |
| Janela de bloqueio | Comprimento da janela de bloqueio | 3 dias |
| Taxa de emissão de recompensas | Tokens alocados para os stakers como recompensas por segundo | 0 |
| Administrador de Proxy | Pode atualizar o contrato | Timelock curto |

## Módulo de segurança

| Parâmetro | Descrição | Valor |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------- |
| Função de proprietário | Administrador de todas as funções | Timelock curto |
| Função de redutor | Pode reduzir os saldos de token em staking e sacar tais fundos | Timelock curto |
| Função de definidor de parâmetros da epoch | Pode definir parâmetros da epoch como o intervalo, offset e janela de bloqueio | Timelock curto |
| Função de definidor de taxa de recompensas | Pode definir a taxa de emissão de recompensas | Timelock curto |
| Função de operador de resgate | Pode resgatar recompensas em nome de um usuário | Proxy de resgates |
| Função de operador de stake | Pode manipular os fundos em staking do usuário (por exemplo, executar saques) em nome de um usuário | Timelock curto |
| Intervalo | Comprimento de uma epoch | 28 dias |
| Offset | Início da epoch zero | 3 de agosto de 2021 15:00 UTC |
| Janela de bloqueio | Comprimento da janela de bloqueio | 3 dias |
| Taxa de emissão de recompensas | Tokens alocados para os stakers como recompensas por segundo | 0 |
| Administrador de Proxy | Pode atualizar o contrato | Timelock longo |

## Stark Proxy

| Parâmetro | Descrição | Valor |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Função de proprietário | Pode adicionar/remover os destinatários que recebem fundos + chaves STARK, definir licenças ERC20 sobre staking de liquidez e contratos perpétuos da Stark, ações forçadas de chamada, sendo administrador de funções de proprietário + administrador de delegação | Maker de mercado |
| Função de administrador de delegação | É o administrador das funções de operador de saques, operador de exchange e operador de mutuários | Maker de mercado |
| Função de mutuário | Pode chamar funções de empréstimo no contrato de staking de liquidez | Maker de mercado |
| Função de operador de exchange | Pode chamar funções da exchange no contrato perpétuo da Stark | Maker de mercado |
| Função de operador de saques | Pode sacar fundos para além do saldo emprestado para um destinatário permitido | Maker de mercado |
| Função de guardião | Pode executar ações fechadas, executar ações forçadas caso o mutuário tenha uma dívida excedida, restringir ações abertas com fundos emprestados e aprovar um valor de token para ser sacado externamente pela função de operador de saques. | Timelock curto |
| Função de guardião de veto | Pode vetar solicitações de trades forçadas iniciadas pelo proprietário, durante o período de espera | Timelock Merkle-pauser |

## Stark Perpetual

| Parâmetro | Descrição | Executor de timelock curto | Executor Merkle-Pauser | Executor de timelock longo | Executor de Starkware |
| -------------------------------------- | ----------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Adicionar novo ativo |             | N | N | N | S |
| Alterar a configuração do ativo atual |             | N | N | N | S |
| Administrador de Proxy |             | N | N | N | S |
| Adicionar operador |             | N | N | N | S |
| Remover operador |             | N | N | N | S |
| Adicionar verificador |             | N | N | N | S |
| Remover verificador |             | N | N | N | S |
