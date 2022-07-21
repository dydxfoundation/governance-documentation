---
description: Visão geral do programa de recompensas do provedor de liquidez.
---

# Recompensas de provedores de liquidez

7,5% da oferta inicial de token (`75.000.000 DYDX`) será distribuída a provedores de liquidez com base em uma fórmula que recompensa uma combinação de tempo de atividade, profundidade do par, spreads de compra e venda e a quantidade de mercados aceitos.

**Objetivos**

* Melhorar a liquidez do par e recompensar programaticamente os provedores de liquidez.

## **Visão geral**

Para incentivar a liquidez do mercado, DYDX será distribuída a provedores de liquidez com base em uma fórmula que recompensa a participação nos mercados, volume de maker, profundidade do par, spread (vs. o mid-market) e o tempo de atividade no protocolo Layer 2 da dYdX. Qualquer endereço de Ethereum pode ganhar essas recompensas, estando sujeito a um limite de volume mínimo de 0,25% do volume de maker na epoch anterior. A DYDX será distribuída numa base de 28 dias ao longo de cinco anos e não está sujeita a vesting ou bloqueios. 1.150.685 DYDX serão distribuídos por epoch.

A função a seguir é usada para calcular quanto de DYDX deve ser enviada como recompensa a cada provedor de liquidez por epoch. A quantia de DYDX obtida é determinada por parte relativa de $$Q_{FINAL}$$ de cada participante

![](<../.gitbook/assets/Screen Shot 2022-05-17 at 1.08.12 PM.png>)

Ordens abaixo de uma determinada **profundidade mínima** (tamanho) ($$MinDepth$$) por mercado são excluídas e ordens de um determinado **spread máximo** (spread de mid-market) ($$MaxSpread$$) de mercado também são excluídas.

O desempenho do provedor de liquidez é monitorado e calculado de minuto a minuto (usando amostragem randomizada) e agregado a um $$Q_{SCORE}$$ ($$Q_{FINAL}$$) para um determinado mercado. Dada a amostragem por minuto, cada epoch tem 28 dias \* 24 horas \* 60 minutos de pontos de dados, isto é, 40.320 pontos de dados por epoch no total.

Os provedores de liquidez ganham recompensas mensais com base na sua parte $$Q_{FINAL}$$ relativa por epoch.

A fórmula acima é explicada em detalhes abaixo:

| _Volume de Maker_ | Volume de maker total para a Epoch. |
| --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/image (96).png" alt="" data-size="original"> | <p></p>Considere que um provedor de liquidez tenha várias ordens abertas (1 BTC em US$ 29.900, 5 BTC em US$ 29.850, 10 BTC em US$ 29.500) no livro de ordens de BTC-USD, e o BTC está atualmente em US$ 30.000 (com base no mid-market). Suponha que o MinDepth é de US$ 5.000 e o MaxSpread vs. mid-market é de US$ 200 ou 6,7 pontos de base (US$ 200/30000). BP é de cem por cento de um por cento.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/30000}\right))</span><p></p><br><span class="math">Q_{BID}</span> é calculado a cada minuto usando uma amostragem aleatória.<br> |
| <img src="../.gitbook/assets/math-20210908 (1) (1).png" alt="" data-size="original"> | <p></p>Suponha que um provedor de liquidez tenha várias ordens abertas (0,1 BTC em US$ 30.100, 5 BTC em US$ 30.150, 10 BTC em US$ 30.175) no livro de ordens de BTC-USD, e o BTC seja negociado no momento a US$ 30.000 (com base no mid-market). Suponha que o MinDepth é de US$ 5.000 e o MaxSpread vs. mid-market é de US$ 200 ou 6,7 pontos de base (US$ 200/30000). BP é de cem por cento de um por cento.<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span><p></p><br><span class="math">Q_{ASK}</span> é calculado a cada minuto em um intervalo aleatório. |
| <img src="../.gitbook/assets/math-20210908 (2) (1).png" alt="" data-size="original"> | <p></p>As recompensas de liquidez do par são calculadas levando em conta o mínimo de <span class="math">Q_{BID}</span> e <span class="math">Q_{ASK}</span>.<br><p></p>Calculado a cada minuto. |
| <img src="../.gitbook/assets/math-20210908 (3) (1).png" alt="" data-size="original"> | $$Q_{EPOCH}$$ é a soma de todo $$Q_{MIN}$$ em uma determinada epoch. |
| <img src="../.gitbook/assets/Screen Shot 2022-05-17 at 1.07.16 PM.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$ é o momento de uma epoch na qual um determinado maker de mercado estava ativo e negociando, tanto em compra como em venda, com tamanhos de ordem maiores que o tamanho mínimo declarado (marcado abaixo por mercado) e spreads menores do que o spread máximo declarado (marcado abaixo por mercado). |
| <img src="../.gitbook/assets/math-20210908 (5) (1).png" alt="" data-size="original"> | $$Q_{FINAL}$$ normaliza $$Q_{EPOCH}$$ para a conta por tempo de atividade |
| _stkDYDX_ | Valor médio de stkDYDX mantido (medido aleatoriamente a cada minuto) dentro da epoch |

Cada mercado terá seu próprio pool de recompensas que será ponderado de maneira diferente. O conjunto inicial de pesos aplicados a cada mercado é o seguinte:

| Mercado | % Alocação de pool de recompensas totais |
| ---------------------- | ---------------------------------------------------------------------- |
| BTC-USD | 20% |
| ETH-USD | 20% |
| Outro mercado perpétuo | ![](<../.gitbook/assets/Screen Shot 2021-07-15 at 1.20.17 PM (1).png>) |

## Perguntas e respostas

### Quem é elegível para recompensas de provedores de liquidez?

Todos os provedores de liquidez que alcançarem um mínimo de 0,25% do volume de maker no protocolo dYdX Layer 2 na epoch anterior são elegíveis para receber DYDX como recompensa em uma determinada epoch.

O protocolo dYdX Layer 2 não está disponível para provedores de liquidez nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de Uso](https://dydx.exchange/terms) da dYdX Trading Inc.

### Quanto DYDX ganhei no programa de recompensas para provedores de liquidez?

Numa determinada epoch, os provedores de liquidez ganham um rendimento com base no seu valor $$Q_{SCORE}$$ em um determinado mercado do par. Cada par tem sua própria quantia de recompensas relativa definida pela governança. A quantidade esperada de DYDX obtida pode ser determinada com base no número de provedores de liquidez envolvidos, no valor $$Q_{SCORE}$$ relativo, e no valor de recompensa disponível para um determinado par.

### Como posso resgatar minhas recompensas para provedores de liquidez?

As recompensas para provedores de liquidez são cobertas na [API da dYdX](https://docs.dydx.exchange/). Embora não seja mostrada na interface de usuário da governança, elas ainda são resgatáveis por meio da governança ao final de cada epoch [aqui](https://dydx.community/dashboard).

### Quando posso fazer o saque e transferir minhas recompensas para provedores de liquidez DYDX que resgatei?

Os tokens DYDX obtidos por meio das recompensas para provedores de liquidez serão resgatados e transferíveis uma vez que o período de restrição de transferência inicial for encerrado.

Começando na epoch 1, os tokens DYDX obtidos por meio das recompensas para provedores de liquidez serão resgatados após `7 dias` (**período de espera**) a partir do final de cada epoch.

### Como são definidos e medidos a profundidade de dois lados, spread de compra e venda e o tempo de atividade?

**Profundidade de dois lados**

Um provedor de liquidez de dois lados é um indivíduo que ativamente negocia de ambos os lados do mercado no protocolo dYdX Layer 2, fornecendo compras e vendas para um determinado mercado. Eles fornecem liquidez ao protocolo de forma geral.

Por exemplo, um provedor de liquidez no mercado de BTC-USD pode fornecer uma cotação de US$ 30.000-US$ 30.100, 10x50. Isso significa que eles ofertam a compra de 10 BTC por US$ 30.000 e também ofertam a venda de 50 BTC a US$ 30.100. Outros participantes de mercado podem então comprar (fazendo ofertas) do provedor de liquidez a US$ 30.100 ou vender a eles a US$ 30.000.

Os provedores de liquidez são avaliados a partir de sua capacidade de fornecer ambas as ofertas a um determinado mercado. Os provedores de liquidez que apenas trabalham de um lado (apenas compras ou apenas vendas) são excluídos de receber recompensas devido à função min().

**Spread de mid-market**

Uma medida comum de liquidez é o spread de compra e venda: o spread entre o maior preço de compra (ordem de compra) e o menor preço de venda (ordem de venda) de um mercado. A diferença entre compra e a venda, isto é, o spread, é o principal custo de transação dos trades (fora das comissões), sendo coletada pelo provedor de liquidez ao processar ordens a preços de compra e de venda. O spread mede o custo de transação imediata a um usuário.

O spread de mid-market considera especificamente o ponto médio do mercado. Com esta fórmula, ordens abaixo do valor de MinDepth para cada mercado também são excluídas.

Por exemplo, se o preço de compra de um provedor de liquidez para BTC-USD for de US$ 30.000 e o preço de venda for de US$ 30.100, o spread de compra será de US$ 100. O preço de mid-market é de US$ 30.050, e o spread de mid-market é de US$ 50.

**Tempo de atividade**

O tempo de atividade para provedores de liquidez é essencial para os mercados, especialmente em períodos de alta volatilidade. Ao aplicar um exponente de 5 a $$Uptime_{epoch}$$ como uma entrada para $$Q_{FINAL}$$, as recompensas tendem aos provedores de liquidez que mantêm a liquidez de dois lados constantemente. Em outras palavras, um provedor de liquidez que fornece 99% de tempo de atividade é exponencialmente mais valioso do que um provedor de liquidez que fornece 90% de tempo de atividade.

O tempo de atividade é definido como a porcentagem de tempo na qual as ordens estão num determinado mercado fornecendo liquidez minuto a minuto (com amostragem randomizada). O tempo de atividade exclui os períodos nos quais ocorrem interrupções no protocolo dYdX Layer 2. Pode haver casos extremos nos quais a exchange esteja lenta ou não aceite ordens (mas não se trata de uma interrupção), nos quais a situação acima não seria aplicável. No entanto, isso seria considerado um bug e todos os provedores de liquidez seriam igualmente afetados, como em interrupções.

### Como são definidos os spreads máximos por mercado?

Nenhum $$Q_{BID}$$ ou $$Q_{ASK}$$ será gerado quando o spread estiver acima de $$MaxSpread$$ de um determinado mercado.

Os spreads máximos iniciais são os seguintes:

| Mercado | Spread máximo vs Mid-Market (compra e venda) |
| ----------------------- | -------------------------------------- |
| BTC-USD | 20 bps |
| ETH-USD | 20 bps |
| Outros mercados perpétuos | 40 bps |

### Como é definida a profundidade mínima (tamanho) por mercado?

Nenhum $$Q_{BID}$$ ou $$Q_{ASK}$$ será gerado quando o tamanho estiver abaixo de $$MinDepth$$ de um determinado mercado.

As profundidades mínimas iniciais são as seguintes:

| **Mercado** | **Profundidade mínima (compra e venda)** |
| ----------------------- | --------------------------- |
| BTC-USD | $5000 |
| ETH-USD | $5000 |
| Outros mercados perpétuos | $1000 |
