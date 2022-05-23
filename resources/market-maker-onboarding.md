---
description: >-
  Para facilitar o processo de onboarding de market maker, a equipe da dYdX criou este guia. Leia todo o documento antes de iniciar quaisquer etapas de integração.
---

# Onboarding de market maker

## Fluxo de onboarding de market maker sugerido pela dYdX:

1. Conecte sua carteira Ethereum preferida ao protocolo dYdX L2 Perpetual.
2. Deposite USDC em sua conta Perpétua.
3. Será necessário gerar uma chave STARK que identifica sua conta na Layer 2 e é salva localmente no seu navegador. A chave Key associa os usuários da dYdX a endereços Ethereum, de modo que um usuário deve primeiro solicitar a assinatura da vinculação de uma chave Ethereum a uma chave STARK e registrar a chave STARK no contrato inteligente da dYdX antes da realização de qualquer outra operação. Clique em “Gerar chave Stark” e assine a transação. A assinatura é gratuita e não enviará uma transação. Você pode recuperar sua chave Stark a qualquer momento com a sua carteira.

Alternativamente, traders programáticos podem derivar seu par de chaves STARK usando o seguinte método:

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

Saiba mais sobre as chaves STARK aqui.

4\. Em seguida, você precisará de uma chave de API que exige sua assinatura Ethereum ou via provedor web3. Observação: as assinaturas Eth são necessárias apenas para o processo de onboarding e gerenciamento de chaves de API e não para operar trades. As chaves STARK são necessárias para operar trades. As chaves de API podem ser registradas e obtidas usando as seguintes funções:

_Registro:_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_Obtenção:_

```
api_keys = client.private.get_api_keys()
```

_Alternativamente (3. e 4.)_, se você não quiser que a chave privada fique online, é possível gerar a chave STARK de forma segura com as seguintes etapas a fim de se obterem as credenciais necessárias.

a. A partir da exchange de perpétuos dYdX, clique com o botão direito em qualquer lugar do seu navegador e selecione Inspecionar para abrir as ferramentas de desenvolvedor

b. Acesse Aplicativo > Armazenamento local > https://trade.dydx.exchange

c. Selecione STARK\_KEY\_PAIRS e clique no menu suspenso ao lado de seu endereço de carteira para obter a chave privada stark

d. Selecione API\_KEY\_PAIRS e clique no menu suspenso ao lado do seu endereço de carteira para obter a chave de API, a chave secreta e a senha
