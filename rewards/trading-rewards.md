---
description: Visão geral do programa de recompensas de trades.
---

# Recompensas de trades

`25,00%` do fornecimento de token inicial (`250.000.000 DYDX`) serão distribuídos a usuários que fizerem trades no protocolo dYdX Layer 2, com base em uma combinação de taxas pagas e posições abertas.

**Objetivos**

* Incentivar todos os traders a usar o protocolo dYdX Layer 2.
* Acelerar a liquidez de mercado e o uso geral do produto.

## **Visão geral**

![Ganhe recompensas ao fazer trades no protocolo da dYdX Camada 2](<../.gitbook/assets/image (17).png>)

Os tokens DYDX serão distribuídos a traders com base em uma fórmula que recompensa uma combinação de taxas pagas e posições abertas no protocolo dYdX Layer 2. Os tokens DYDX serão distribuídos dentro de um ciclo de 28 dias ao longo de um período de cinco anos, não estando sujeitos a vesting ou bloqueios. 3.835.616 DYDX serão distribuídos por epoch.

A função Cobb-Douglas é usada para calcular quanto DYDX é concedida a cada trader durante cada epoch:

![](../.gitbook/assets/math-20211221.png)

$$
 r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k
 $$

| Termo | Definição |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| r | Recompensa para um trader específico. |
| R | Total de recompensa a ser dividida entre todos os traders do pool para a epoch. |
| f | Total de taxas pagas por um trader nesta epoch. |
| w | Pontuação individual de traders. |
| $${\sum\limits _{n} w_{n}}$$ | Soma de todas as pontuações de traders. |
| d | A taxa de posições abertas média de um trader (medida a cada minuto) em todos os mercados nesta epoch. |
| k | Número total de traders nesta epoch. |
| g | A stkDYDX média que um trader tem (medida aleatoriamente a cada minuto) ao longo da epoch |
| a | 0,80 |
| b | 0,15 |
| c | 0,05 |

Em [DIP-10](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-10.md), a Comunidade dYdX votou para alterar o peso do parâmetro de taxa de `a=0,67` para `a=0,8` e para diminuir o parâmetro de ordens abertas de `b=0,28` para `b=0,15.`

## Perguntas e respostas

### Quem é elegível para as recompensas de trades?

Todos os traders no protocolo dYdX Layer 2 são elegíveis para receber DYDX como recompensas.

O protocolo dYdX Layer 2 não está disponível para traders nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de Uso](https://dydx.exchange/terms) da dYdX Trading Inc.

### Quanto em DYDX ganhei no programa de recompensas de trades?

Na epoch atual, os usuários podem consultar as taxas pagas, média de posições abertas e recompensas estimadas em [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards), onde os dados de trades dos usuários se encontram.

![Informações de recompensas para a epoch atual](<../.gitbook/assets/image (18).png>)

As recompensas de epoch passadas podem ser exibidas em [**dydx.community/history/rewards**](https://dydx.community/history/rewards) **** (em breve).

### Como posso resgatar minhas recompensas de trades? Quando posso sacar e transferir a DYDX que recebi?

Os tokens DYDX obtidos por meio de recompensas de trades se tornam transferíveis ao final de cada epoch. Os holders de tokens DYDX são obrigados a esperar aproximadamente `7 dias` (**período de espera**) após o final da epoch para resgatá-los. Uma vez que os tokens tenham sido resgatados, eles podem ser usados na governança da dYdX.

Os traders podem resgatar suas recompensas de trades ao final de cada epoch [aqui](https://dydx.community/dashboard), após o **período de espera**.

Os usuários precisarão clicar em “Claim (Resgatar)”, assinar uma transação e pagar as taxas de gás para o resgate de DYDX.

![Visão geral de recompensas do portfólio](<../.gitbook/assets/image (20).png>)

### O que são posições abertas?

O total de posições abertas é o valor em USD de todas as posições de long e short pendentes (as unidades totais de longs sempre igualam o total de unidades de shorts) para um determinado mercado. O aumento de posições abertas representa um dinheiro novo ou adicional que entra no mercado, já a diminuição de posições abertas indica o dinheiro que sai do mercado.

Veja abaixo uma tabela de atividade de negociação dos traders A, B, C, D, e E. As ordens abertas são calculadas em USDC de acordo com a atividade de trades para cada dia:

| Tempo | Atividade de trades | Total líquido de posições abertas (USDC) |
| ------- | -------------------------------------------------------------------------- | ------------------------------ |
| 1º de julho | O **trader A** compra 1 BTC a US$ 30.000 e o **trader B** vende 1 BTC a US$ 30.000 | US$ 30.000 |
| 3 de julho | O **trader C** compra 5 BTC a US$ 30.000 e o **trader D** vende 5 BTC a US$ 30.000 | US$ 180.000 |
| 5 de julho | O **trader A** vende 1 BTC a US$ 30.000 e o **trader D** compra 1 BTC a US$ 30.000 | US$ 150.000 |
| 10 de julho | O **trader E** compra 5 BTC a US$ 30.000 e o **trader C** vende 5 BTC a US$ 30.000 | US$ 150.000 |

No contexto da fórmula de **recompensas de trades**, as posições abertas são medidas a cada minuto (aleatoriamente a cada minuto) em todos os mercados e ponderadas durante uma determinada epoch a fim de calcular as recompensas.

A posição aberta de um trader é o valor em USD de todas as posições abertas desse trader. Para fins de **recompensas de trades**, as posições abertas de um trader são medidas a cada minuto (num momento aleatório a cada minuto) em todos os mercados e ponderadas em uma determinada epoch.
