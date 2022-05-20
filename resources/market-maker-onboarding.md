---
description: >-
  Afin de faciliter l'intégration des acteurs de marché, l'équipe dYdX a créé ce guide. Veuillez lire le document dans son intégralité avant de commencer toute étape d'intégration.
---

# Intégration des teneurs de marché

## Flux d'intégration pour les teneurs de marché suggéré par dYdX :

1. Connectez votre portefeuille Ethereum préféré au protocole perpétuel dYdX L2.
2. Déposez USDC sur votre compte Perpétuel.
3. Vous devrez générer une clé STARK qui identifie votre compte sur la couche 2 et qui est enregistrée localement sur votre navigateur. Afin d'associer des utilisateurs dydX à des adresses de compte Ethereum, un utilisateur doit d'abord demander à signer la liaison d'une clé Ethereum à une clé Stark, puis enregistrer la clé Stark sur le contrat intelligent de dYdX avant que toute autre opération utilisateur puisse avoir lieu. Cliquez sur « Générer une clé Stark » et signez la transaction. La signature est gratuite et n'enverra pas de transaction. Vous pouvez récupérer votre clé Stark à tout moment avec votre portefeuille.

Sinon, les traders programmatiques peuvent dériver leur paire de clés STARK en utilisant la méthode suivante :

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

En savoir plus sur les clés STARK ici.

4\. Ensuite, vous aurez besoin d'une clé API qui nécessitera votre signature Ethereum, ou via un fournisseur web3. Notez que les signatures Eth ne sont nécessaires que pour l'intégration et la gestion des clés API, mais pas pour le trading. Les signatures de clé STARK sont requises pour le trading. Les clés API peuvent être enregistrées et obtenues à l'aide des fonctions suivantes :

_Enregistrement :_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_Obtention :_

```
api_keys = client.private.get_api_keys()
```

_Alternativement (3. Et 4.)_, Si vous ne voulez pas que la clé privée soit en ligne, vous pouvez générer la clé STARK en toute sécurité avec les étapes suivantes pour obtenir les informations d'identification requises.

a. Depuis l'échange dYdX Perpétuels, faites un clic droit n'importe où dans votre navigateur Web et sélectionnez Inspecter pour ouvrir les outils de développement

b. Accédez à Application > Stockage local > https://trade.dydx.exchange

c. Sélectionnez STARK\_KEY\_PAIRS et cliquez sur le menu déroulant à côté de l'adresse de votre portefeuille pour obtenir la clé privée Stark

d. Sélectionnez API\_KEY\_PAIRS et cliquez sur le menu déroulant à côté de l'adresse de votre portefeuille pour obtenir la clé API, la clé secrète et la phrase secrète
