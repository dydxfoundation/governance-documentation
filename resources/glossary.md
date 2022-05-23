---
description: Visão geral dos principais termos relacionados à governança.
---

# Glossário

**DYDX:** o ativo nativo do ecossistema DYDX, que constitui a base de governança e segurança para o protocolo dYdX. DYDX é um token ERC-20 que designa o peso de voto e o poder de proposta de um usuário.

**Protocolo dYdX:** protocolo de perpétuos da dYdX de Layer 2.

**Fundação dYdX:** uma fundação independente, com sede em Zug, na Suíça, criada para impulsionar o protocolo dYdX em direção ao futuro.

**Contrato do token DYDX**: possui snapshots do poder de voto de cada endereço em diferentes blocos ao longo do tempo.

**DIP:** as propostas de melhorias para a dYdX são apresentadas on-chain.

**DRC**: a solicitação dYdX de comentários são propostas off-chain, trata-se da primeira etapa necessária no processo de melhorias da governança.

**Quórum:** para que um voto seja aprovado, é preciso alcançar um quórum mínimo de tokens DYDX na afirmativa. O objetivo do quórum é garantir que as únicas medidas aprovadas tenham uma participação de votos adequada.

**Epoch:** todos os outros contratos operam em ciclos de 28 dias, referidos como epochs.

**Período de carência de execução:** o período após o voto com uma proposta DIP se torna executável, durante o qual ela deve ser executada.

**Contrato de estratégia de governança**: contém lógica para medir o poder relativo dos usuários para propor e votar.

**Contrato do Governador**: rastreia propostas e pode executá-las por meio de um contrato inteligente timelock.

**Executor de timelock longo:** o executor de timelock longo executa propostas que geralmente mudam partes do protocolo, estas que afetam o consenso da governança.

**Executor Merkle-pauser:** o executor Merkle-pauser é capaz de executar propostas que congelam a raiz Merkle, que é atualizada periodicamente com o saldo de recompensas cumulativa de cada usuário. Isso permite que novas recompensas sejam distribuídas aos usuários ao longo do tempo, caso a raiz proposta esteja incorreta ou seja maliciosa.

**Pool de segurança:** componente responsável por proteger o protocolo de questões de insolvência.

**Contrato dYdX em stake**: contém a lógica para fazer o stake de tokens DYDX, tokenizar posições e obter recompensas.

**Executor de timelock curto:** o executor de timelock curto é capaz de executar propostas que geralmente mudam os contratos de recompensas e incentivo ou quando o Tesouro da Comunidade exige uma intervenção rápida.

**Executor Starkware:** o executor Starkware é capaz de executar propostas que geralmente mudam partes do protocolo que atualmente exijam intervenção da Starkware.

**Contrato de timelock**: pode dispor em filas, cancelar ou executar transações votadas pela Governança. As funções em uma proposta são iniciadas pelo contrato timelock. As transações em fila podem ser executadas após um atraso e até que o período de carência esteja ativo.

**Atraso de timelock:** o atraso que ocorre antes de uma proposta DIP ser executada assim que esta é aprovada e enfileirada.

**Limite da proposta:** para evitar que um sistema no qual inúmeras propostas de spam sejam criadas, existe um limite de propostas, e este define que um endereço deve possuir um determinado número de votos antes que possa fazer uma proposta.

**Poder de proposição:** stake de tokens que concede acesso à criação e sustentação de uma proposta.

**Poder de voto:** poder de voto que é usado para votar a favor ou contra propostas atuais.

**Atraso de voto:** período entre a criação de uma proposta e o início de sua votação. Ao exigir pelo menos um bloco para aprovação, a governança é protegida de ataques de flash loan, estes que são capazes de emprestar um grande número de tokens, propor um voto e votá-lo em um único bloco.

**Período de voto:** uma vez que uma proposta de DIP seja apresentada, os membros da comunidade da DYDX votam até o fim do período de voto. Este é o período no qual as propostas ficam disponíveis para serem votadas, com o tempo em blocos Ethereum.

**Limite de proposta:** mínimo de tokens que é mantido/delegado e necessário para criar uma proposta DIP.

**Diferencial de voto:** intervalo exigido entre votos para que uma proposta DIP possa ser aprovada.
