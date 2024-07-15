---
description: Visão geral do programa de recompensas de trades.
---

#

`14,5`**`%`** (`144.693.506 $ethDYDX`) do suprimento de tokens é alocado para ser distribuído a usuários que fizeram trades na dYdX v3 com base em taxas pagas. Inicialmente, 25,0% do fornecimento de token (250.`000.00``0 $ethDYDX`) foram alocados para recompensas de trades.

* No [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/8) pela redução de recompensas de trades em 25,0%. Como resultado, a alocação para recompensas de trading diminuiu de `25,0%` para `20,2%`.
* No [DIP 20](https://dydx.community/dashboard/proposal/11), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/11) pela redução de recompensas de trading em mais 45,0%. Como resultado, a alocação para recompensas de trading diminuiu de `20,2%` para `14,5%`.
*   Na [DIP 29](https://dydx.community/dashboard/proposal/16), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/16) para reduzir as recompensas de trading em ⅓ da epoch 30-32 na dYdX v3 para os seguintes valores:

    * Epoch 30: 1.054.795 $ethDYDX
    * Epoch 31: 527.398 $ethDYDX
    * Epoch 32: 0 $ethDYDX

    Observe que, na DIP 29, a comunidade dYdX votou pela migração da alocação restante de recompensas de trading para a Cadeia dYdX para recompensas de trading.

As recompensas de trading distribuídas em uma determinada epoch foram/serão reduzidas de 3.835.616 $ethDYDX para:

* 2.876.712 $ethDYDX na Epoch 15,
* 1.582.192 $ethDYDX na Epoch 21,
* 1.054.795 $ethDYDX na Epoch 30,
* 527.398 $ethDYDX na Epoch 31,
* 0 $ethDYDX no Epoch 32 em diante.

Após a epoch 31, não haverá recompensas de trading na dYdX v3. Na [DIP 29](https://dydx.community/dashboard/proposal/16) na dYdX v3 e na [Proposal 2](https://www.mintscan.io/dydx/proposals/2) na Cadeia dYdX, a comunidade dYdX votou para creditar o valor restante de $ethDYDX não investido na dYdX v3 [Rewards Treasury Vester](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) para o [dYdX Chain Rewards Treasury Vester `(dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk) e, posteriormente, distribuído como recompensas de trading na Cadeia dYdX, sujeito à aprovação de governança na Cadeia dYdX.

**Objetivos**

* Incentive todos os traders a usar a dYdX v3.
* Acelerar a liquidez de mercado e o uso geral do produto.

## **Visão geral**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Taxas pagas e recompensas estimadas em uma determinada época</p></figcaption></figure>

Anteriormente, $ethDYDX era distribuído aos traders com base nas taxas pagas na dYdX v3. $ethDYDX era distribuído em uma epoch de 28 dias, ao longo de cinco anos, e não estava sujeito à nenhuma aquisição ou bloqueio.

Na [DIP 29](https://dydx.community/dashboard/proposal/16), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/16) para reduzir as recompensas de trading em ⅓ da epoch 30-32 na dYdX v3 para os seguintes valores:

* Epoch 30: 1.054.795 $ethDYDX
* Epoch 31: 527.398 $ethDYDX
* Epoch 32 e todas as epochs restantes: 0 $ethDYDX



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

##

Os tokens $ethDYDX ganhos por meio de recompensas de trading serão transferíveis ao final de cada epoch. Os detentores de token $ethDYDX são obrigados a esperar aproximadamente `7 dias` (**Período de espera**) após o final da epoch para resgatar seus tokens $ethDYDX.

Após o período de espera de 7 dias, qualquer membro da comunidade pode chamar a função `Gravar` no parâmetro `updateRoot`, no [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) para tornar as recompensas de $ethDYDX reivindicáveis.

Etapas:

1. Na página [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) na Etherscan, clique na guia `Contrato` e selecione `Gravar como proxy.`
2. Clique no botão `Conectar à Web3` e conecte sua carteira da Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Role para baixo até o parâmetro `updateRoot` e clique no botão `Gravar`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>



* O período de espera de 7 dias ainda estiver em vigor ou
* Um membro da comunidade já tiver chamado com sucesso o parâmetro `updateRoot` no [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Após a transação ter sido finalizada, os traders podem reivindicar suas recompensas de trades [aqui](https://dydx.community/dashboard). Os usuários precisarão clicar em `Reivindicar`, assinar uma transação e pagar as taxas de gás para reivindicar $ethDYDX.

![Visão geral de recompensas do portfólio](../.gitbook/assets/1-portfolio-overview-rewards.png)

## Perguntas e respostas

<details>

<summary>Quem é elegível para as recompensas de trades?</summary>

Todos os traders na dYdX v3 eram elegíveis para receber $ethDYDX como recompensas de trading.

A dYdX v3 não está disponível para traders nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de uso da](https://dydx.exchange/terms) dYdX Trading Inc.

</details>

<details>

<summary>Quanto $ethDYDX ganhei no programa de recompensas de trading?</summary>

Na epoch atual, os usuários podem ver as taxas pagas e as recompensas de trades estimadas em [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards), onde estão os dados de trades dos usuários.

As recompensas de épocas anteriores podem ser vistas em [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

</details>
