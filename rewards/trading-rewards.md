---
description: Visão geral do programa de recompensas de trades.
---

# Recompensas de trades

`20,2`**`%`** (`201.883.560 $ethDYDX`) do fornecimento de token é alocado para ser distribuído a usuários que fizeram trades na dYdX v3 com base em taxas pagas. Inicialmente, 25,0% do fornecimento de token (250.`000.00``0 $ethDYDX`) foram alocados para recompensas de trades.

* No [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/8) pela redução de recompensas de trades em 25,0%. Como resultado, a alocação para recompensas de trading diminuiu de `25,0%` para `20,2%`.
* No [DIP20](https://dydx.community/dashboard/proposal/11), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/11) pela redução de recompensas de trading em mais 45,0%. Como resultado, a alocação para recompensas de trading diminuiu de `20,2%` para `14,5%`.

As recompensas de trading distribuídas em uma determinada época foram reduzidas de 3.835.616 $ethDYDX para 2.876.712 $ethDYDX na Epoch 15 e de 2.876.712 $ethDYDX para 1.582.192 $ethDYDX na Epoch 21.

**Objetivos**

* Incentive todos os traders a usar a dYdX v3.
* Acelerar a liquidez de mercado e o uso geral do produto.

## **Visão geral**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Taxas pagas e recompensas estimadas em uma determinada época</p></figcaption></figure>

O $ethDYDX será distribuído aos traders com base nas taxas pagas na dYdX v3. O $ethDYDX será distribuído em uma epoch de 28 dias ao longo de cinco anos e não está sujeito a nenhuma aquisição ou bloqueio. 1.582.192 ethDYDX serão distribuídos por epoch.

Com a votação da comunidade para seguir com uma redução de 25% nas recompensas de trading em 958.904 $ethDYDX em [DIP16](https://dydx.community/dashboard/proposal/8) e mais 45% em 1.294.520 $ethDYDX em [DIP20](https://dydx.community/dashboard/proposal/11), os 2.253.424 $ethDYDX restantes acumulados no Tesouro de Recompensas podem ser usados/direcionados pela comunidade dYdX com um [voto de governança](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$
r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1.2...k
$$

| Termo | Definição |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Recompensa para um trader específico. |
| R | Total de recompensa a ser dividida entre todos os traders do pool para a epoch. |
| f | Total de taxas pagas por um trader nesta epoch. |
| w | Pontuação individual de traders. |
| $${\sum\limits _{n} w_{n}}$$ | Soma de todas as pontuações de traders. |
| k | Número total de traders nesta epoch. |

Na [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), a Comunidade da dYdX votou pela simplificação da fórmula, que terá como base o total das taxas pagas por um trader em uma determinada epoch.

## Perguntas e respostas

### Quem é elegível para as recompensas de trades?

Todos os traders na dYdX v3 são elegíveis para receber $ethDYDX como recompensas de trading.

A dYdX v3 não está disponível para traders nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de uso da](https://dydx.exchange/terms) dYdX Trading Inc.

### Quanto $ethDYDX ganhei no programa de recompensas de trading?

Na epoch atual, os usuários podem ver as taxas pagas e as recompensas de trades estimadas em [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards), onde estão os dados de trades dos usuários.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Taxas pagas e recompensas estimadas em uma determinada época</p></figcaption></figure>

As recompensas de épocas anteriores podem ser vistas em [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### Como posso resgatar minhas recompensas de trades? Quando posso sacar e transferir o $ethDYDX que recebi?

Os tokens $ethDYDX ganhos por meio de recompensas de trading serão transferíveis ao final de cada epoch. Os detentores de token $ethDYDX são obrigados a esperar aproximadamente `7 dias` (**Período de espera**) após o final da epoch para resgatar seus tokens $ethDYDX.

Após o período de espera de 7 dias, qualquer membro da comunidade pode chamar a função `Gravar` no parâmetro `updateRoot`, no [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) para tornar as recompensas de $ethDYDX reivindicáveis.

Etapas:

1. Na página [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) na Etherscan, clique na guia `Contrato` e selecione `Gravar como proxy.`
2. Clique no botão `Conectar à Web3` e conecte sua carteira da Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Role para baixo até o parâmetro `updateRoot` e clique no botão `Gravar`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Essa transação exigiria algum ETH para cobrir as taxas de gás; a transação falhará se:**

* O período de espera de 7 dias ainda estiver em vigor ou
* Um membro da comunidade já tiver chamado com sucesso o parâmetro `updateRoot` no [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Após a transação ter sido finalizada, os traders podem reivindicar suas recompensas de trades [aqui](https://dydx.community/dashboard). Os usuários precisarão clicar em `Reivindicar`, assinar uma transação e pagar as taxas de gás para reivindicar $ethDYDX.

![Visão geral de recompensas do portfólio](../.gitbook/assets/1-portfolio-overview-rewards.png)
