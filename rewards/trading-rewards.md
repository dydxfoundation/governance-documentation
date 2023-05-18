---
description: Visão geral do programa de recompensas de trades.
---

# Recompensas de trades

`25,00%` da oferta inicial de token (`250.000.000 DYDX`) serão distribuídos para usuários que fizerem trades no protocolo da Camada 2 da dYdX com base nas taxas pagas.

**Objetivos**

* Incentivar todos os traders a usar o protocolo dYdX Layer 2.
* Acelerar a liquidez de mercado e o uso geral do produto.

## **Visão geral**

![Ganhe recompensas ao fazer trades no protocolo da dYdX Camada 2](<../.gitbook/assets/image (14) (2) (1).png>)

Os tokens DYDX serão distribuídos para os traders com base nas taxas pagas no protocolo da Camada 2 da dYdX. Os tokens DYDX serão distribuídos dentro de um ciclo de 28 dias ao longo de um período de cinco anos, não estando sujeitos a vesting ou bloqueios. 3.835.616 DYDX serão distribuídos por epoch.

![](<../.gitbook/assets/Screenshot 2022-08-12 at 17.50.17.png>)

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

Todos os traders no protocolo dYdX Layer 2 são elegíveis para receber DYDX como recompensas.

O protocolo dYdX Layer 2 não está disponível para traders nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de Uso](https://dydx.exchange/terms) da dYdX Trading Inc.

### Quanto em DYDX ganhei no programa de recompensas de trades?

Na epoch atual, os usuários podem ver as taxas pagas e as recompensas de trades estimadas em [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards), onde estão os dados de trades dos usuários.

![Informações de recompensas para a epoch atual](<../.gitbook/assets/image (18).png>)

As recompensas de epochs passadas podem ser vistas em [**dydx.community/history/rewards**](https://dydx.community/history/rewards) \*\*\*\* (em breve).

### Como posso resgatar minhas recompensas de trades? Quando posso sacar e transferir a DYDX que recebi?

Os tokens DYDX obtidos por meio de recompensas de trades se tornam transferíveis ao final de cada epoch. Os holders de tokens DYDX são obrigados a esperar aproximadamente `7 dias` (**período de espera**) após o final da epoch para resgatá-los. Uma vez que os tokens tenham sido resgatados, eles podem ser usados na governança da dYdX.

Os traders — **após o período de espera** — podem resgatar suas recompensas ao final de cada epoch, [aqui](https://dydx.community/dashboard).

Os usuários precisarão clicar em “Claim (Resgatar)”, assinar uma transação e pagar as taxas de gás para o resgate de DYDX.

![Visão geral de recompensas do portfólio](<../.gitbook/assets/image (20).png>)

