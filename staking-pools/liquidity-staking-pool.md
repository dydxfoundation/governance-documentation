---
description: Uma visão geral do pool de staking de liquidez
---

# Módulo de liquidez

`2,50%` do fornecimento de token inicial (`25.000.000 DYDX`) será distribuído a usuários que fizerem staking de USDC no pool de staking de liquidez.

### Objetivos

* Incentivar a alocação de USDC para fins de making de mercado no protocolo dYdX Layer 2.
* Alocar capital aos melhores provedores de liquidez para aumentar o spread, profundidade e tempo de atividade na dYdX.

Comece a fazer staking em [**dydx.community/dashboard/pools/liquidez**](https://dydx.community/dashboard/pools/liquidity)**.**

## Visão geral do **staking**

A liquidez é um componente essencial de qualquer exchange bem-sucedida. Para promover os efeitos de rede de liquidez e incentivar os provedores de liquidez profissionais, a DYDX será distribuída a usuários que fizerem stake de USDC no pool de staking de liquidez. Os provedores de liquidez aprovados pela comunidade usarão o USDC em staking para movimentar os mercados do protocolo dYdX Layer 2, aumentando a liquidez disponível nos mercados. Os provedores de liquidez ficam restritos de usar fundos emprestados fora do protocolo dYdX Layer 2.

Os stakers ganham recompensas DYDX quando fazem staking de USDC. As recompensas DYDX serão distribuídas continuamente de acordo com a parte de USDC total de cada staker no pool.

Cada staker e provedor de liquidez precisam tomar parte do contrato de crédito de resgate (link [aqui](https://dydx.foundation/revolving-credit-agreement)). O contrato coloca em linguagem natural os termos do pool de staking de liquidez, que concede a cada staker um direito obrigatório sobre qualquer provedor de liquidez que não cubra o USDC emprestado. O contrato é apenas entre cada staker e cada provedor de liquidez. A dYdX Foundation não é uma parte do contrato e não tem direitos ou obrigações atribuídas por ele.

## Remoção do USDC de stake e saques

Um staker deve solicitar saques de USDC pelo menos `14 dias` (**janela de bloqueio**) antes do final de uma [**epoch**](../start-here/epochs.md) para poder sacar o USDC do staker após o final da epoch. Se os stakers não solicitarem o saque, o USDC em staking acumulará para a próxima epoch.

Os saques não podem ser solicitados durante a **janela de bloqueio**.

## Riscos do staking

Mutuários do pool não são obrigados a trancar garantias. Todos os mutuários são provedores de liquidez profissionais e de renome. A lista de mutuários autorizados e suas alocações no pool podem ser atualizadas pela governança.

Quando os usuários solicitam saques de USDC, o saldo alocado de um mutuário para a próxima epoch pode ficar abaixo do valor de empréstimo atual do mutuário. Nesta situação, o mutuário fica responsável por devolver a diferença entre seus saldos emprestados e alocados antes do final da epoch.

Se um mutuário não devolver o saldo de volta à pool até o final da epoch, ele será considerado inadimplente e não será permitido que ele empreste mais USDC até que o valor seja reembolsado. Os stakers podem perder USDC caso um mutuário nunca reembolse uma dívida. Os stakers podem perder uma parte do USDC em staking se um maker de mercado acabar perdendo USDC e não conseguir repor o valor no pool de staking de liquidez.

Os stakers também ficam expostos ao risco do contrato inteligente, caso haja alguma vulnerabilidade no código deste contrato inteligente. Todos os contratos inteligentes DYDX e de governança foram auditados e rigorosamente testados.

Para reduzir o risco aos stakers, cada staker e provedor de liquidez serão obrigados a tornar-se parte do contrato de crédito em resgate (link [aqui](https://dydx.foundation/revolving-credit-agreement)), mas o contrato não garante que um provedor de liquidez reembolsará todos os valores emprestados, mesmo que os direitos de um staker sob o contrato sejam executados.

## Mutuários aprovados

O contrato do pool de staking de liquidez funciona como um sistema de liquidez sem juros, sob garantias de dois lados.

O valor que pode ser sacado depende da porcentagem de alocação de um mutuário e do total disponível em USDC no pool de staking. Tanto a porcentagem de alocação quanto o total disponível de USDC podem variar, em momentos predefinidos especificados pela `LS1EpochSchedule`. O USDC emprestado só pode ser usado no protocolo da dYdX Layer 2. Isso é executado por meio do contrato `StarkProxy`, que interage com o contrato da `StarkEx Perpetual Exchange`.

Os provedores de liquidez aprovados inicialmente incluem `Wintermute`, `Amber Group`, `Wootrade (Kronos)`, `Sixtant` e `DAT Trading`, que fazem parte ativamente do market-making no protocolo dYdX Layer 2.

| Mutuários pré-aprovados | Porcentagem de alocação inicial | Endereço Ethereum | StarkProxy | Detalhes sobre os provedores de liquidez |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wintermute | 25% | [0x4f3a120E72C76c22ae802D129F599BFDbc31cb81](https://etherscan.io/address/0x4f3a120E72C76c22ae802D129F599BFDbc31cb81) | [0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6](https://etherscan.io/address/0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6) | [https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/](https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/) |
| Amber Group | 25% | [0x39Ad99E33ab7Ee85818741dD6076112188bc2611](https://etherscan.io/address/0x39Ad99E33ab7Ee85818741dD6076112188bc2611) | [0x3e6E9EFb0A677a24F47093a22044dc5451A028cF](https://etherscan.io/address/0x3e6E9EFb0A677a24F47093a22044dc5451A028cF) | [https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/](https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/) |
| WOO Network (Kronos) | 20% | [0x38d981c3c42b2ec8e9572f560552407d0f1279fb](https://etherscan.io/address/0x38d981c3c42b2ec8e9572f560552407d0f1279fb) | [0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06](https://etherscan.io/address/0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06) | [https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/](https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/) |
| Sixtant | 20% | [0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c](https://etherscan.io/address/0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c) | [0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2](https://etherscan.io/address/0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2) | [https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/](https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/) |
| DAT Trading | 10% | [0x83E8fb8f4DAE0f42d68FdbBf85d4191a5e6f92F8](https://etherscan.io/address/0x83e8fb8f4dae0f42d68fdbbf85d4191a5e6f92f8) | [0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874](https://etherscan.io/address/0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874) | [https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/](https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/) |

## Contabilização do saldo em stake

Um saldo em staking está em um dos dois estados:

* **Ativo**: disponível para empréstimos, recebe recompensas de staking; não pode ser sacado pelo staker.
* **Inativo**: não disponível para empréstimos; não recebe recompensas; pode ser sacado pelo staker.

Um staker pode ter uma combinação de saldos ativos ativos e inativos. O USDC é contabilizado epoch a epoch, conforme mostrado no seguinte exemplo:

![Contabilidade do saldo em stake](<../.gitbook/assets/image (34) (1).png>)

As operações seguintes afetam os saldos em staking da seguinte forma:

* **Depósito**: aumenta o saldo ativo.
* **Solicitar saque**: ao final da epoch atual, movimente alguns USDC ativos para o estado inativo.
* **Saque**: diminui o saldo inativo.
* **Transferência**: movimenta alguns USDC ativos para outro staker.

Para codificar o fato de que um saldo pode ser alterado conforme um agendamento ao final de uma determinada epoch, cada saldo é armazenado como uma estrutura de três campos: currentEpoch, currentEpochBalance e nextEpochBalance. Os saldos inativos de um usuário também fazem uso do campo shortfallCounter.

### O que é o stkUSDC?

Os titulares do USDC que depositam e fazem stake de seu USDC no pool de staking de liquidez receberão uma posição tokenizada (**stkUSDC**). O mint de stkUSDC é feito quando um usuário faz o stake USDC. O stkUSDC é queimado quando um usuário faz chamadas da função `withdrawStake`. Na mesma transação na qual o USDC deixa a carteira de um staker, o stkUSDC entra na carteira do staker ou vice-versa, quando o valor é retirado do staking.

Um saldo da stkUSDC pode ser ativo ou inativo. O stkUSDC ativo pode ser transferido como ERC-20, mas não pode ser sacado. O stkUSDC inativo pode ser sacado, mas não pode ser transferido. Por exemplo, um usuário pode ter 100 stkUSDC ativos e 100 stkUSDC inativos na sua carteira e o saldo do usuário será exibido como 200 stkUSDC. No entanto, uma transferência será revertida se o usuário tentar transferir mais de 100 stkUSDC.

Um saldo em staking para o qual o staker solicitou um saque antes do final da epoch seria considerado inativo e, portanto, não transferível.

## Perguntas frequentes de **stakers**

### Como posso ganhar recompensas de staking?

Os stakers podem depositar USDC a qualquer momento no pool de staking de liquidez e começar a ganhar recompensas imediatamente. As recompensas DYDX são obtidas de forma contínua de acordo com a parte de cada staker do pool total, segundo a segundo. As recompensas podem ser resgatadas e sacadas a qualquer momento.

O USDC em stake recebe recompensas pelo período no qual permanece ativo. Isso significa que após solicitar um saque de alguns USDC, este USDC continuará a ganhar recompensas até o final da epoch. Por exemplo:

![Contabilidade de recompensas](<../.gitbook/assets/image (65) (1).png>)

No cenário acima, o usuário ganharia recompensas pelo período de **Time0** a **Time2**, havendo variações no saldo em staking total nesse período. Se o usuário solicitar apenas um saque para uma parte do saldo do usuário, o saldo restante continuará a receber recompensas além do **tempo 2**.

### Como posso depositar e fazer stake de USDC no pool de liquidez?

Para fazer stake de USDC no pool de liquidez, siga estes passos:

* Acesse [https://dydx.community/dashboard/pools/liquidity](https://dydx.community/dashboard/pools/liquidity)
* Clique em “Stake (Fazer stake)”
* É preciso habilitar o USDC na primeira vez que fizer o depósito. Você só terá de fazer isso e pagar a taxa de gás uma vez.
* Digite o valor de USDC que deseja fazer o stake no pool.
* Clique em “Stake Funds (Fazer stake dos fundos)”. Você precisará pagar as taxas de gás de stake, solicitação de saque e saque de USDC.

![](<../.gitbook/assets/image (57).png>)

O USDC em staking está ativo agora e começara a receber recompensas imediatamente.

Para depositar e fazer stake de USDC diretamente no contrato inteligente, será necessário que os usuários chamem a função `stake`. Os usuários também podem depositar e fazer stake de USDC em nome de outro endereço. Basta chamar a função `stakeFor`. Mesmo que você faça stake de USDC diretamente no contrato inteligente, será considerado que você leu e concordou com o contrato de crédito em resgate (link [aqui](https://dydx.foundation/revolving-credit-agreement)).

### O que é a janela de bloqueio?

Uma janela de bloqueio é um período durante o qual os usuários não podem solicitar saques de USDC em staking. A função `requestWithdrawal` não pode ser chamada durante uma janela de bloqueio, que é configurada inicialmente como os últimos `14 dias` de uma epoch. Novas epochs começam a cada 28 dias. Desse modo, os usuários podem solicitar um saque para a próxima epoch até `14 dias` antes do final de uma determinada epoch.

### Como posso sacar o USDC do pool de staking? Quanto tempo demora?

Uma agenda de epoch é executada para saques a fim de fornecer previsibilidade e um ritmo regular para a disponibilidade de USDC no pool. Um staker deve solicitar a retirada do USDC do stake pelo menos `14 dias` antes do final de uma epoch para poder sacar o USDC após o final da epoch. Se os stakers não solicitarem o saque, o USDC em staking acumulará para a próxima epoch.

Para sacar o USDC, os usuários chamam a função `requestWithdrawal` para solicitar o saque de USDC para a próxima epoch. Os fundos de usuário permanecerão em staking e não poderão ser sacados na epoch atual. A partir da próxima epoch, os fundos ficarão como “inativos” e disponíveis para saque.

Na próxima epoch, os usuários chamam a função `withdrawStake` para sacar o USDC inativo para um endereço específico. Os usuários podem selecionar o valor de fundos inativos que desejam sacar ou chamar a função \`withdrawMaxStake\` para sacar todos os fundos inativos. A função `withdrawMaxStake` é menos eficiente em termos de gás em vez de consultar o valor máximo via eth\_call e chamar `withdrawStake()`.

Para remover o USDC do stake no pool de liquidez, siga as seguintes etapas:

* Visite [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Clique em “**Request (Solicitação)**”, para abrir o seguinte modal:

![Solicitando saque](<../.gitbook/assets/image (68).png>)

* Digite o valor de USDC que deseja solicitar para saque do pool e clique em “**Request withdraw (Solicitar saque)**”. Você precisará pagar as taxas de gás para remover o USDC do stake.
* Os stakers que solicitarem a remoção do USDC pelo menos 14 dias (**janela de bloqueio**) antes da epoch atual terminar podem sacar seu USDC no início da próxima epoch.

### Quais parâmetros a governança pode mudar?

A governança da dYdX é responsável por:

* Fazer a auditoria legal sobre os mutuários existentes
* Adicionar novos mutuários e/ou remover os mutuários atuais do pool de staking de liquidez
* Alterar as alocações de USDC emprestadas a mutuários aprovados
   * As funções `setBorrowerAllocations` e `setBorrowingRestriction` são chamadas para alterar as alocações de determinados mutuários. Elas podem ser usadas para adicionar e remover os mutuários. Os aumentos entram em vigor na próxima epoch, mas as reduções restringirão empréstimos imediatamente. Essas funções não podem ser chamadas durante a janela de bloqueio.
* O tamanho da epoch e a janela de bloqueio são configurados na criação do contrato, mas podem ser alterados

## **Perguntas e respostas sobre mutuários**

### **Empréstimo**

O USDC em stake entra em um pool que é alocado para os mutuários aprovados. Cada mutuário tem uma porcentagem de alocação controlada pela governança e pode emprestar até o limite desta alocação. A remoção do staking está sujeita a uma “agenda de epoch”. O USDC em staking só pode ser sacado (isto é, tornar-se “inativo”) no início de uma epoch.

O USDC solicitado para saque deve ser devolvido pelos mutuários antes do final da epoch. No caso de falta de pagamento, o valor torna-se um “saldo em dívida” e o contrato de staking é reestabilizado. O mutuário inadimplente deve devolver o saldo da dívida e ficará impedido de realizar empréstimos até que isso seja restabelecido pela governança.

Os mutuários estão sujeitos a todos os termos do contrato de crédito em resgate (link [aqui](https://dydx.foundation/revolving-credit-agreement)).

### **Características do StarkProxy**

#### **Pagamento automático**

Os mutuários podem usar o `autoPayOrBorrow()` para garantir o uso máximo do USDC alocado e o reembolso dentro do prazo dos saques solicitados. A função só precisa ser chamada com sucesso uma vez por epoch para que um mutuário possa garantir que esteja cumprindo suas responsabilidades.

A função será revertida se for chamada na primeira metade da epoch, pois esta fica fora da janela de bloqueio. Será revertida se o contrato da `StarkProxy` não tiver USDC suficiente para o reembolso. Neste caso, o USDC deve ser adicionado ou sacado da exchange antes da função `autoPayOrBorrow()` ser chamada.

#### **USDC pertencente a mutuários**

Um mutuário pode depositar seu próprio USDC na `StarkProxy` e usar o protocolo dYdX Layer 2 na mesma conta na qual tem seu USDC emprestado. O USDC pode ser sacado da `StarkProxy` em qualquer uma das seguintes situações:

* O USDC mantido dentro do contrato da `StarkProxy` maior que o saldo emprestado pode ser sacado a qualquer momento.
* A governança pode aprovar um saque de um determinado valor.
   * Observação: isso pode ser usado para permitir que o mutuário saque os lucros sem ter de movimentar externamente a maioria do USDC do protocolo dYdX Layer 2.

#### **Funções do mutuário**

O contrato da `StarkProxy` fornece as seguintes funções controladas pelo mutuário. Estas podem ser mantidas por um único endereço ou endereços separados, dependendo das necessidades de segurança do mutuário. Cada função pode ser mantida por qualquer quantidade de endereços.

Proprietário

* Conceder ou revogar a função de administrador da delegação.
* Adicionar ou remover os destinatários permitidos para saques de USDC da `StarkProxy`.
* Adicionar ou remover as chaves STARK permitidas para uso no protocolo dYdX Layer 2.
* Definir permissões ERC20 nos contratos `LiquidityStakingV1` e `StarkPerpetual`.
* Chamar as funções `forcedWithdrawalRequest()` ou `forcedTradeRequest()` no contrato `StarkEx Perpetual Exchange`.

Administrador da delegação

* Conceder ou revogar as funções de operador de saques, operador de exchange do mutuário.

Mutuário

* Chamar as funções `autoPayOrBorrow()`, `borrow()`, `repay()` e `repayDebt()` no contrato de staking de liquidez.

Operador de Exchange

* Chamar as funções `registerUserOnExchange()`, `depositToExchange()` e `withdrawFromExchange()` no contrato `StarkEx Perpetual Exchange`.

Operador de saques

* Movimentar um saque externo válido (ver acima) do contrato `StarkProxy` a um destinatário permitido.

#### **Limitações**

As transferências da Layer 2 no protocolo dYdX Layer 2 são desativadas para contas controladas por um `StarkProxy`.

#### **Poderes de guardião**

A função de guardião será controlada pela governança da dYdX. Sua função é garantir a segurança do USDC emprestado e permitir que seja devolvido aos stakers caso a chave privada de um mutuário seja perdida ou usada indevidamente.

O guardião pode tomar as seguintes ações a qualquer momento (sujeito a time-lock):

* Restringir o empréstimo e o depósito de USDC emprestado à exchange.
* Repagar um saldo emprestado usando o USDC no contrato `StarkProxy`.
* Repagar um saldo de dívida usando o USDC no contrato `StarkProxy`.
* Sacar do contrato StarkEx para o contrato `StarkProxy` (por exemplo, como no segundo passo de um saque lento da exchange).
* Cancelar uma solicitação de trades forçada iniciada pelo mutuário.
* Aprovar que o mutuário saque um valor do contrato `StarkProxy` enquanto contorna uma verificação de saldo.
* Atualizar o contrato inteligente.

**O guardião pode tomar as seguintes ações se o mutuário tiver um saldo de dívida pendente (sujeito a time-lock):**

* Fazer um saque forçado do protocolo dYdX Layer 2.
* Fazer um trade forçado (somente redução) no protocolo dYdX Layer 2.

## Perguntas e respostas sobre os riscos do staking

### Quais são os riscos de fazer staking no pool de staking de liquidez? O que acontece se um mutuário não pagar fundos emprestados?

Um sistema para empréstimos não garantidos requer um padrão de confiança muito mais alto que deve ser atendido por um mutuário. Os provedores de liquidez que tomam empréstimos do pool de staking de liquidez não podem movimentar fundos emprestado para fora do sistema de staking de liquidez e do protocolo dYdX Layer 2. Ainda assim, o USDC em staking poderia ser perdido se um provedor de liquidez perdesse fundos e não fosse capaz de restituir suas alocações emprestadas por meio de fontes de financiamento externas.

Neste caso, os fundos inativos podem estar sujeitos a perdas socializadas, conforme estabelecido abaixo no caso de um déficit no qual um mutuário está atrasado para pagar os fundos solicitados para saque. No caso de inadimplência relativa aos fundos emprestados, um mutuário em atraso enfrentará danos de reputação consideráveis.

Embora cada staker e mutuário sejam parte do contrato de crédito em resgate (link [aqui](https://dydx.foundation/revolving-credit-agreement)), este contrato não fornece uma garantia de que os mutuários reembolsarão suas obrigações.

### Como o contrato mantém a solvência?

A qualquer momento o contrato estará em um dos seguintes estados com base na relação entre os saldos de staking e os emprestados:

![Solvência do contrato](<../.gitbook/assets/image (41).png>)

O contrato se encontrará em **estado de insolvência**:

* se o saldo em empréstimo total for maior do que o saldo ativo total;
* ou, de forma equivalente, se o saldo inativo total for maior do que o saldo total não emprestado;
* ou, de modo equivalente, se o saldo total que pode ser sacado for maior do que o saldo de USDC do contrato.

Caso contrário, o contrato estará em **solvência**.

Como o empréstimo está limitado à proporção de USDC ativo alocado de um mutuário e o saldo inativo só pode aumentar entre as epochs, o contrato só pode mudar de um estado de solvência para um estado de insolvência durante as transições entre as epochs.

Se, no início de uma nova epoch, o contrato estiver em insolvência, será importante reestabilizá-lo o mais rapidamente possível. A solvência é restaurada por um mecanismo chamado “contabilidade de dívidas”. Sempre que o contrato estiver em insolvência, a função `markDebt()` poderá ser chamada por qualquer pessoa, especificando uma lista de mutuários que excederam suas alocações. O valor pelo qual o saldo do empréstimo de um mutuário excede sua alocação é chamado de valor de déficit do mutuário.

Quando `markDebt()` é chamado, o valor de déficit de cada mutuário é removido de seu saldo emprestado para um saldo chamado o saldo da dívida. Ao mesmo tempo, o agregado destes valores de déficit é retirado de saldos inativos do staker e distribuído como recibos de dívida do staker. O saldo inativo de cada staker sofrerá um desconto no valor da dívida e cada staker receberá um valor equivalente na forma de dívida. Desta forma, a perda de insolvência é socializada (proporcional ao dia) em todos os stakers que detêm saldos inativos.

Este processo é mostrado abaixo:

![Inadimplência](<../.gitbook/assets/image (46).png>)

### O que a dívida representa?

No caso de um valor de déficit de um mutuário, o valor de déficit (até 100% de saldos inativos) é convertido de um saldo inativo para um saldo de dívida (perda socializada entre os detentores de saldo inativo). O saldo de dívida de um staker não permite que ele faça saques do pool de USDC em staking. É preciso fazer o pagamento especificamente na forma de pagamentos de dívida.

A dívida representa um recibo de USDC que pode ser resgatado por USDC, seja quando o mutuário faz um pagamento de dívida ou por meio de outros meios de recuperação conforme determinado pela governança.

### Quais recursos estão disponíveis para os stakers se um mutuário entrar em inadimplência?

Os staker e os mutuários são partes do contrato de crédito em resgate (link [aqui](https://dydx.foundation/revolving-credit-agreement)) que se destina a criar um contrato de execução entre cada staker e mutuário. Além disso, o contrato inteligente de pool de staking de liquidez foi elaborado para conceder aos stakers um recurso contra os mutuários, embora não possa garantir o reembolso.

Quando a função `markDebt()` é chamada em um mutuário, esse mutuário perde o direito de emprestar quaisquer outros fundos do contrato. Este direito pode ser reintegrado pela governança.

Uma vez que a dívida tenha sido “marcada”, ela é removida do sistema principal de contabilidade e pode ser recuperada pelos stakers de várias maneiras. Se o mutuário em dívida pagar a dívida (ou se outra parte, como a governança, reembolsá-la em seu nome), os stakers cuja dívida era devida poderão recuperar os fundos por ordem de chegada. As soluções mais flexíveis podem ser implementadas por meio da interface “operador de dívidas” no contrato inteligente.

O que acontece na prática após os stakers receberem a dívida dependerá do contexto. Se se tratar de um erro honesto por parte de um mutuário aprovado, os stakers poderão esperar ser pagos de volta rapidamente e na íntegra. Se os fundos de USDC forem perdidos, a governança poderá emitir um pagamento parcial aos stakers afetados. Se a resolução for incerta, a governança poderá optar por emitir um recibo ERC20 aos stakers afetados, concedendo-lhes liquidez instantânea enquanto aguardam uma resolução. Se for considerado apropriado, a governança poderá optar por emitir pagamentos de juros aos titulares de recibos até que uma resolução seja alcançada.

Todos estes casos são fundamentalmente apoiados pelo contrato de staking, mas a resposta apropriada deve ser decidida e executada pela governança da dYdX. Dependendo da situação, isso pode exigir que um contrato inteligente periférico seja escrito e implantado.
