---
description: Visão geral do programa de recompensas do provedor de liquidez.
---

# Recompensas de provedores de liquidez

**3,2%** da oferta de token (`31.643.838 $ethDYDX`) será distribuída a provedores de liquidez (LPs) com base em fórmulas que recompensam uma combinação de volume de maker, tempo de atividade, profundidade do par, spreads de compra e venda e a quantidade de mercados suportados. Inicialmente, **7,5%** (`75.000.000 $ethDYDX`) do suprimento de tokens foi alocado para recompensas de LP.

* No [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md), a comunidade da dYdX [votou](https://dydx.community/dashboard/proposal/14) para reduzir as recompensas de provedor de liquidez em 50%, de `1.150.685 $ethDYDX` por época para `575.343 $ethDYDX` por época. Como resultado disso, a alocação para recompensas de LP diminuiu de `7,5%` para 5,`2%`.
*   Na [DIP 29](https://dydx.community/dashboard/proposal/16), a comunidade dYdX [votou](https://dydx.community/dashboard/proposal/16) para reduzir as recompensas de LP em ⅓ da epoch 30-32 na dYdX v3 para os seguintes valores:

    * Epoch 30: 383.562 $ethDYDX
    * Epoch 31: 191.781 $ethDYDX
    * Epoch 32: 0 $ethDYDX

    Após a epoch 31, não haverá recompensas de LP na dYdX v3. Como resultado disso, a alocação para recompensas de LP diminuiu de `5,2%` para `3,2%`.

Como não há distribuição de recompensas de provedor de liquidez na Cadeia dYdX, a comunidade dYdX na DIP 29 votou pela migração da alocação restante para recompensas de provedor de liquidez para o Tesouro da Comunidade dYdX.

**Objetivos**

* Melhorar a liquidez do par e recompensar programaticamente os provedores de liquidez.

## **Visão geral**

Para incentivar a liquidez do mercado, o $ethDYDX será distribuído a provedores de liquidez com base em fórmulas que recompensam a participação nos mercados, volume de maker, profundidade do par, spread (vs. o mercado intermediário) e o tempo de atividade no protocolo de segunda camada (L2) da dYdX v3. Qualquer endereço Ethereum pode ganhar essas recompensas, sujeito a um limite mínimo de volume de maker de 0,25% na época anterior. O $ethDYDX será distribuído em uma época de 28 dias ao longo de cinco anos e não estará sujeito a nenhum tipo de aquisição ou bloqueio.

As funções a seguir são usadas para calcular a quantidade de $ethDYDX que deve ser enviada como recompensa a cada provedor de liquidez por epoch. Durante o [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), a comunidade dYdX votou para que se revisasse a fórmula de recompensas de LP dividindo as funções para mercados de BTC/ETH e mercados não BTC/ETH. No [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md), a comunidade da dYdX votou por realocar o peso de 0,05 stkDYDX para o MakerVolume.

De modo geral, a ponderação de volume nas funções foi aumentada em todos os mercados. A quantia de ethDYDX obtida é determinada pela parte relativa de $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) de cada participante.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Ordens abaixo de uma determinada **profundidade mínima** (tamanho) ($$MinDepth$$) por mercado são excluídas e ordens de um determinado **spread máximo** (spread de mid-market) ($$MaxSpread$$) de mercado também são excluídas.

O desempenho do provedor de liquidez é monitorado e calculado de minuto a minuto (usando amostragem randomizada) e agregado a um $$Q_{SCORE}$$ para um determinado mercado. Dada a amostragem por minuto, cada epoch tem 28 dias \* 24 horas \* 60 minutos de pontos de dados, isto é, 40.320 pontos de dados por epoch no total.

Os provedores de liquidez ganham recompensas mensais com base na sua parte $$Q_{FINAL}$$ relativa por epoch.

A fórmula acima é explicada em detalhes abaixo:

| _Volume de Maker_ | Volume de maker total para a Epoch. |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>Considere que um provedor de liquidez tenha várias ordens abertas (1 BTC em US$ 29.900, 5 BTC em US$ 29.850, 10 BTC em US$ 29.500) no livro de ordens de BTC-USD, e o BTC está atualmente em US$ 30.000 (com base no mercado intermediário). Suponha que a profundidade mínima é de US$ 5.000 e o spread máximo vs. mercado intermediário é de US$ 200, ou 67 pontos base (US$ 200/30000). BP é de cem por cento de um por cento.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/30000}\right))</span><p></p><br><span class="math">Q_{BID}</span> é calculado a cada minuto usando uma amostragem aleatória.<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>Suponha que um provedor de liquidez tenha várias ordens abertas (0,1 BTC em US$ 30.100, 5 BTC em US$ 30.150, 10 BTC em US$ 30.175) no livro de ordens de BTC-USD, e o BTC seja negociado no momento a US$ 30.000 (com base no mercado intermediário). Suponha que a profundidade mínima é de US$ 5.000 e o spread máximo vs. mercado intermediário é de US$ 200, ou 67 pontos base (US$ 200/30000). BP é de cem por cento de um por cento.<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span><p></p><br><span class="math">Q_{ASK}</span> é calculado a cada minuto em um intervalo aleatório. |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p>As recompensas de liquidez do par são calculadas levando em conta o mínimo de <span class="math">Q_{BID}</span> e <span class="math">Q_{ASK}</span>.<br><p></p>Calculado a cada minuto. |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$ é a soma de todo $$Q_{MIN}$$ em uma determinada epoch. |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $$Uptime_{EPOCH}$$ é o momento de uma epoch na qual um determinado maker de mercado estava ativo e negociando, tanto em compra como em venda, com tamanhos de ordem maiores que o tamanho mínimo declarado (marcado abaixo por mercado) e spreads menores do que o spread máximo declarado (marcado abaixo por mercado). |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$ normaliza $$Q_{EPOCH}$$ para a conta por tempo de atividade |

Cada mercado terá seu próprio pool de recompensas que será ponderado de maneira diferente. No [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md), a comunidade dYdX votou por reduzir a alocação de recompensas totais em BTC-USD e ETH-USDC para 10% cada. O conjunto de pesos aplicados a cada mercado é o seguinte:

| Mercado | % Alocação de pool de recompensas totais |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | 10% |
| ETH-USD | 10% |
| Outros mercados perpétuos | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## Perguntas e respostas

### Quem é elegível para recompensas de provedores de liquidez?

Todos os provedores de liquidez que alcançarem um mínimo de 0,25% do volume de maker no protocolo da dYdX v3 na epoch anterior são elegíveis para receber ethDYDX como recompensa em uma determinada época.

A dYdX v3 não está disponível para provedores de liquidez nos Estados Unidos ou em territórios restritos, conforme definido nos [Termos de uso](https://dydx.exchange/terms) da dYdX Trading Inc.

### Quanto $ethDYDX ganhei no programa de recompensas para provedores de liquidez?

Numa determinada epoch, os provedores de liquidez ganham um rendimento com base no seu valor $$Q_{SCORE}$$ em um determinado mercado do par. Cada par tem sua própria quantia de recompensas relativa definida pela governança. A quantidade esperada de ethDYDX obtidos é exibida no [Painel de Recompensas LP](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) e pode ser determinada com base no número de provedores de liquidez envolvidos, no valor de $Q_{SCORE}$$ e no valor da recompensa disponível para um determinado par.

### Como posso resgatar minhas recompensas para provedores de liquidez?

As recompensas para provedores de liquidez são cobertas na [API da dYdX](https://docs.dydx.exchange/). Embora não seja mostrada na interface de usuário da governança, elas ainda são resgatáveis por meio da governança ao final de cada epoch [aqui](https://dydx.community/dashboard).

### Quando posso fazer o saque e transferir minhas recompensas para provedores de liquidez ethDYDX que resgatei?

Os tokens ethDYDX obtidos por meio das recompensas para provedores de liquidez serão resgatados e transferíveis uma vez que o período de restrição de transferência inicial for encerrado.

Começando na epoch 1, os tokens $ethDYDX obtidos por meio das recompensas para provedores de liquidez serão resgatados `após 7 dias` (**período** de espera) a partir do final de cada epoch.

### Como são definidos e medidos a profundidade de dois lados, spread de compra e venda e o tempo de atividade?

**Profundidade de dois lados**

Um provedor de liquidez de dois lados é um indivíduo que ativamente negocia de ambos os lados do mercado no protocolo dYdX v3, fornecendo compras e vendas para um determinado mercado. Eles fornecem liquidez ao protocolo de forma geral.

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
