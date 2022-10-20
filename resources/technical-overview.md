---
description: Aperçu de l'architecture de gouvernance et des contrats intelligents.
---

# Aperçu technique

## Aperçu de l'architecture de gouvernance

La gouvernance sur la chaîne dYdX prend en charge les fonctionnalités suivantes :

* Créer et voter sur des propositions
* Prendre des instantanés des portefeuilles de jetons au début d'une proposition
* Déléguer de pouvoirs de vote et de proposition séparés
* Fixer des seuils de gouvernance, y compris des seuils de proposition, de quorum et de vote différentiel
* Remplacer le contrat intelligent « Stratégie de gouvernance », qui détermine le mode de comptage des votes
* Configuration de contrats à plusieurs exécuteurs permettant :
  * mises à niveau rapides du protocole et distribution des fonds via des exécuteurs de courte durée ;
  * mises à niveau de la gouvernance via des exécuteurs à verrouillage de longue durée.

Il existe 6 contrats intelligents qui prennent en charge la gouvernance dYdX :

* **Le contrat `DydxToken`** : conserve des instantanés qui prennent en charge les requêtes pour le pouvoir de vote ou de proposition d'une adresse à n'importe quel numéro de bloc. Prend en charge la délégation séparée des pouvoirs de vote et de proposition.
* **Le contrat `DydxGovernor`** : suit les propositions et peut exécuter des propositions via les contrats intelligents Exécuteur.
* **Les contrats `Exécuteur`** : peut mettre en file d'attente, annuler et exécuter des transactions votées par la gouvernance. Si une proposition est acceptée, les appels de fonctions dans la proposition peuvent être exécutés par le contrat Exécuteur spécifié dans la proposition. Les transactions en file d'attente peuvent être exécutées après un délai, dont la durée est déterminée par le contrat Exécuteur.
* **Le** **contrat** **`Verrouillage prioritaire`** : edentique au contrat de verrouillage, mais permet à un contrôleur prioritaire d'exécuter des transactions dans la **période prioritaire** (7 jours) avant la fin du délai de verrouillage.
* **Le contrat `Stratégie de gouvernance`** : contient la logique pour le comptage des votes. Actuellement, compte les votes du jeton DYDX et du module de sécurité. Peut être mis à niveau via le verrouillage de longue durée.
* **Le contrat `Module de sécurité`** : contient des logiques pour staker des jetons DYDX, tokeniser une position jalonnée et gagner des récompenses, tout en conservant les droits de vote et de proposition et les fonctions de délégation des jetons sous-jacents.

{% tabs %} {% tab title="Mainnet" %} | Contrat                             | Adresse                                    | | ------------------------------------ | ------------------------------------------ | | DydxToken                            | 0x92D6C1e31e14520e676a687F0a93788B716BEff5 | | DydxGovernor                         | 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 | | Exécuteur de longue durée              | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc | | Exécuteur de longue durée               | 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B | | Exécuteur Verrouillage Merkle-Pauser     0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52 | | Exécuteur Verrouillage prioritaire Starkware | 0xa306989BA6BcacdECCf3C0614Ff2B8C668e3CaE | | Trésorerie de récompenses                    | 0x639192D54431F8c816368D3FB4107Bc168d0E871 | | Trésorerie de la communauté                    | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b | | Module de sécurité                         | 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC | | GovernanceStrategy                   | 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 | | Récompenses Treasury Vester              | 0xb9431E19B29B952d9358025f680077C3Fd37292f | | Community Treasury Vester            | 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 | | Distributeur Merkle                          | 0x01d3348601968aB85b4bb028979006eac235a588 | | Adaptateur Chainlink                           | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 | | Staking des liquidités                          | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 | | Proxy de réclamations                         | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e | | Gouverneur assistant StarkEx              | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a | | StarkEx Remover Governor V2          | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 | | Administrateur Proxy de trésorerie des récompenses         | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d | | Administrateur Proxy de trésorerie de la communauté       | 0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 | | Administrateur Proxy de module de sécurité            | 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C | | Administrateur Proxy du distributeur Merkle       | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 | | Administrateur Proxy de staking de liquidité        | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 | | StarkProxy \[0]                      | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 | | StarkProxy \[1]                       | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF | | StarkProxy \[2]                      | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 | | StarkProxy \[3]                      | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 | | StarkProxy \[4]                      | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 | | Administrateur Proxy StarkProxy \[0]          | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 | | Administrateur Proxy StarkProxy \[1]          | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 | | Administrateur Proxy StarkProxy \[2]          | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 | | Administrateur Proxy StarkProxy \[3]          | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA | | Administrateur Proxy StarkProxy \[4]          | 0xfa45DCDbEc82C94082d283B62506320DB8632054 | {% endtab %} {% endtabs %}

## Code open-source et audité

Tous les codes source des contrats intelligents pour les contrats de gouvernance et les pools de staking se trouvent sur [https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts).

Le code source de l'interface de gouvernance hébergée sur dydx.community se trouve [ici](https://github.com/dydxfoundation/pnyx).

Tous les nouveaux contrats intelligents majeurs ont été audités par Peckshield. Aucun problème de sécurité important ou hautement prioritaire n'a été détecté. Les contrats de gouvernance de base et de jetons sont dérivés des contrats de gouvernance Aave qui ont été audités par [CertiK](https://www.certik.io/), [Certora](https://www.certora.com/) et [Peckshield](https://peckshield.com/en) et ont été testés en direct sur le mainnet pendant des mois.

## Contrats de gouvernance de base

![Les lignes pointillées rouges indiquent que le contrat est évolutif](../.gitbook/assets/3-core-governance-contracts-1.png)

### DydxToken

Le contrat DydxToken s'est inspiré d'Aave. Des modifications mineures ont été effectuées par l'équipe dYdX.

DYDX est déployé à [0x92D6C1e31e14520e676a687F0a9378B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5) sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

### DydxGovernor

Le contrat DydxGovernor s'est inspiré d'Aave. Des changements mineurs ont été effectués par dYdX.

Gouverneur est déployé à [0x7E9B1672616FF6D6629Ef2879419aE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2) sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

### GovernanceStrategy

Le contrat GovernanceStrategy s'est inspiré d'Aave.

La stratégie est déployée sur [0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9) sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

### Exécuteurs

Le contrat Exécuter s'est inspiré d'Aave. Des changements mineurs ont été effectués par dYdX.

Le **Verrouillage longue durée** est déployé à [0xEcaE9BF44A21d00E235a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

Le **Short Timelock** est déployé à [0xEcaE9BF44A21d00E235a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) sur le réseau principal Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

Le **verrouillage Merkle** est déployé à [0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52) sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

Le **verrouillage proritaire Starkware** est déployé à [0xa306989BA6BcacdECCf3C0614Ff2B8C668e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae) sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

## Contrats incitatifs DYDX

### Distributeur Merkle

![Les lignes pointillées rouges indiquent que le contrat est évolutif](../.gitbook/assets/3-core-governance-contracts-2.png)

Le contrat intelligent Distributeur Merkle distribue les récompenses de tokens DYDX selon un arbre des soldes Merkle. L'arbre peut être mis à jour périodiquement avec le solde cumulatif des récompenses de chaque utilisateur, ce qui permet de distribuer de nouvelles récompenses aux utilisateurs au fil du temps.

Une mise à jour est effectuée en définissant la racine Merkle proposée sur la dernière valeur renvoyée par le contrat d'oracle. La racine Merkle proposée peut être rendue active après une période d'attente. Pendant la période d'attente, Gouvernance dYdX a la possibilité de geler la racine Merkle, au cas où la racine proposée serait incorrecte ou malveillante. Les mises à jour racine peuvent être rétablies par ShortTimelockExecutor.

Le contrat intelligent Distributeur Merkle s'est inspiré des conceptions Uniswap et Badger. Le contrat intelligent est déployé à 0x01d3348601968aB85b4bb028979006eac235a588 sur le mainnet Ethereum. Il a été construit à partir du commit \[bientôt disponible].

**ABI**

\[bientôt disponible]

### Module de sécurité

![Les lignes pointillées rouges indiquent que le contrat est évolutif](../.gitbook/assets/3-core-governance-contracts-3.png)

Le module de sécurité est un pool de staking qui offre des récompenses DYDX aux utilisateurs qui stakent DYDX pour la sécurité du protocole.

**ABI**

\[bientôt disponible]

### Module de liquidité

![Les lignes pointillées rouges indiquent que le contrat est évolutif](../.gitbook/assets/3-core-governance-contracts-4.png)

Le module de liquidité est une collection de contrats intelligents pour le staking et l'emprunt, qui incitent à l'allocation de fonds USDC pour maintenir le marché sur l'échange de couche 2 dYdX.

Les stakers gagnent des récompenses DYDX pour avoir staké l'USDC. Les fonds stakés peuvent être empruntés par certains partenaires pré-approuvés, sur une base de réputation, sans garantie. Les fonds ne peuvent être utilisés que sur l'échange de couche 2 - ceci est appliqué via le contrat StarkProxy qui interagit avec le contrat StarkEx Perpetual Exchange.

![Un schéma du module Liquidité](../.gitbook/assets/3-core-governance-contracts-5.png)

### StarkProxy

Ce contrat permet au propriétaire d'emprunter des fonds auprès de LiquidityStaking et d'utiliser ces fonds sur StarkPerpetual. Des fonds supplémentaires peuvent être déposés par le propriétaire, et tout fonds excédant le montant emprunté peut être retiré librement. Ce contrat interagit avec le contrat [StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual) qui a été rédigé par Starkware, et précédemment audité et déployé.

### Contrats de trésorerie

![Les lignes pointillées rouges indiquent que le contrat est évolutif](../.gitbook/assets/3-core-governance-contracts-6.png)

Le contrat TreasuryVester s'est inspiré d'[Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol).

Le verrouillage courte durée ne peut exécuter que des actions approuvées par la gouvernance.

Il existe deux vesters de trésorerie et des contrats de trésorerie, l'un pour les récompenses de contrats incitatifs et l'autre pour la détention de fonds de trésorerie « à usage général ».

Étant donné que la gouvernance contrôle chaque trésorerie, elle peut transférer des fonds à n'importe quelle adresse et/ou approuver n'importe quelle adresse pour dépenser des fonds de l'une ou l'autre trésorerie. Par exemple, les programmes de récompenses devront avoir des limites d'approbation de jetons fixées par la gouvernance.

Chaque détenteur de trésorerie investira des jetons de manière linéaire sur \~ 5 ans (3 août 2021 - 3 août 2026) à la trésorerie correspondante.

## Contrats périphériques

### Chainlink Oracle-Powered Rewards (Récompenses des fournisseurs de trading et de liquidité)

L'objectif de ce système est de calculer et de publier, via un réseau décentralisé de signataires d'oracle, les récompenses en jetons DYDX gagnées par les traders utilisant l'échange de couche 2 dYdX. Les récompenses sont stockées dans un arbre Merkle, qui contient les récompenses cumulées gagnées par chaque utilisateur depuis le début du programme de distribution. À chaque époch, la racine Merkle est mise à jour sur le contrat intelligent MerkleDistributorV1 pour refléter les récompenses gagnées au cours de la dernière époch.

Nous nous sommes intégrés au système Chainlink Oracle pour publier les données relatives aux récompenses sur la chaîne. Nous utilisons IPNS pour publier les données de trading que Chainlink utilise pour construire l'arbre Merkle. En utilisant IPNS, nous pouvons publier les données de trading pour la dernière époch sous le même lien IPNS que les épochs précédentes, ce qui signifie que l'emplacement des données ne changera pas.

Après avoir calculé les récompenses appropriées à partir des données de trading brutes, Chainlink publie l'arbre des récompenses Merkle sur IPFS. Le CID IPFS avec les données de l'arbre Merkle est stocké sur le contrat du distributeur Merkle avec la racine Merkle pour les récompenses de cette époch.

L'organigramme suivant montre l'architecture du système Chainlink Oracle-Powered Rewards :

![](../.gitbook/assets/3-core-governance-contracts-merkle-distributor.png)

### Autres actifs

* Les actifs de la marque dYdX Foundation sont disponibles [**ici**](https://dydx.foundation/brand)\*\*\*\*
