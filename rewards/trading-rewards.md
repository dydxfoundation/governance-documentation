---
description: Visão geral do programa de recompensas de trades.
---

# Recompensas de trades

`20,2`**`%`** (`201.883.560 $DYDX`) do fornecimento de token é alocado para ser distribuído a usuários que fizeram trades no protocolo dYdX Layer 2 com base em taxas pagas. Inicialmente, 25,0% do fornecimento de token (`250.000.000 $DYDX```) foram alocados para recompensas de trades.

* No [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/8) pela redução de recompensas de trades em 25,0%. Como resultado, a alocação para recompensas de trading diminuiu de `25,0%` para `20,2%`.
* No [DIP20](https://dydx.community/dashboard/proposal/11), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/11) pela redução de recompensas de trading em mais 45,0%. Como resultado, a alocação para recompensas de trading diminuiu de `20,2%` para `14,5%`.

As recompensas de trading distribuídas em uma determinada epoch foram reduzidas de 3.835.616 $DYDX para 2.876.712 $DYDX em Epoch 15 e de 2.876.712 $DYDX para 1.582.192 $DYDX em Epoch 21.

**Objetivos**

* Incentivar todos os traders a usar o protocolo dYdX Layer 2.
* Acelerar a liquidez de mercado e o uso geral do produto.

## **Visão geral**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Taxas pagas e recompensas estimadas em uma determinada época</p></figcaption></figure>

Os tokens $DYDX serão distribuídos para os traders com base nas taxas pagas no protocolo da Camada 2 da dYdX. Os tokens $DYDX serão distribuídos dentro de um ciclo de 28 dias ao longo de um período de cinco anos, não estando sujeitos a vesting ou bloqueios. Serão distribuídos 1.582.192 $DYDX por epoch.

Com a votação da comunidade para seguir com uma redução de 25% nas recompensas de trading em 958.904 $DYDX em [DIP16](https://dydx.community/dashboard/proposal/8) e mais 45% em 1.294.520 $DYDX em [DIP20](https://dydx.community/dashboard/proposal/11), os 2.253.424 $DYDX restantes acumulados no Tesouro de Recompensas podem ser usados/direcionados pela comunidade dYdX com um [voto de governança](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

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

Todos os traders no protocolo dYdX Layer 2 são elegíveis para receber $DYDX como recompensas de trading.

O protocolo dYdX Layer 2 não está disponível para traders nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de Uso](https://dydx.exchange/terms) da dYdX Trading Inc.

### Quanto em DYDX ganhei no programa de recompensas de trades?

Na epoch atual, os usuários podem ver as taxas pagas e as recompensas de trades estimadas em [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards), onde estão os dados de trades dos usuários.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Taxas pagas e recompensas estimadas em uma determinada época</p></figcaption></figure>

As recompensas de épocas anteriores podem ser vistas em [**dydx.community/history/rewards**](https://dydx.community/history/rewards)**.**

### Como posso resgatar minhas recompensas de trades? Quando posso sacar e transferir a $DYDX que recebi?

Os tokens $DYDX obtidos por meio de recompensas de trades se tornam transferíveis ao final de cada epoch. Os detentores de tokens $DYDX são obrigados a esperar aproximadamente `7 dias` (**período de espera**) após o final da epoch para reivindicar seus tokens $DYDX.

Após o período de espera de 7 dias, qualquer membro da comunidade pode chamar a função `Gravar` no parâmetro `updateRoot`, no [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) para tornar as recompensas de DYDX reivindicáveis.

Etapas:

1. Na página [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) na Etherscan, clique na guia `Contrato` e selecione `Gravar como proxy.`
2. Clique no botão `Conectar à Web3` e conecte sua carteira da Web3.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Role para baixo até o parâmetro `updateRoot` e clique no botão `Gravar`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Essa transação exigiria algum ETH para cobrir as taxas de gás; a transação falhará se:**

* O período de espera de 7 dias ainda estiver em vigor ou
* Um membro da comunidade já tiver chamado com sucesso o parâmetro `updateRoot` no [Contrato do distribuidor Merkle](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract).

Após a transação ter sido finalizada, os traders podem reivindicar suas recompensas de trades [aqui](https://dydx.community/dashboard). Os usuários precisarão clicar em `Reivindicar`, assinar uma transação e pagar as taxas de gás para reivindicar $DYDX.

![Visão geral de recompensas do portfólio](../.gitbook/assets/1-portfolio-overview-rewards.png)
