---
description: Un aperçu de haut niveau de l'architecture de gouvernance.
---

#

## Aperçu

$ethDYDX, $stkDYDX et $wethDYDX (« jetons de gouvernance ») accordent aux détenteurs le droit de proposer et de voter sur les modifications de dYdX v3. La gouvernance dYdX se base sur les accords de gouvernance AAVE et prend en charge le vote basé sur les avoirs des jetons de gouvernance.

Les propositions doivent franchir un seuil donné et un pourcentage de votes favorables en fonction du type de proposition.



Il existe 8 contrats intelligents au cœur de la gouvernance dYdX :

* **Les ``contrats** de jetons $ethDYDX, $stkDYDX et $wethDYDX : ont des instantanés du pouvoir de vote de chaque adresse à différents blocs dans le temps.
* **Le contrat `de stratégie de gouvernance V2`** : contient une logique pour mesurer le pouvoir relatif des utilisateurs à proposer et à voter. lLa Communauté dYdX [a voté](https://dydx.community/dashboard/proposal/15) pour la mise à niveau du contrat de `stratégie de gouvernance` en `stratégie de gouvernance V2` afin de doter $wethDYDX de la même fonctionnalité de gouvernance qu'ethDYDX pour le vote et la proposition de gouvernance dans la gouvernance dYdX v3.
*
* **Le contrat `Gouverneur`** : trace les propositions et peut exécuter des propositions via les contrats intelligents Timelock.
* **Les contrats `Timelock`** : peuvent mettre en file d'attente, annuler ou exécuter des transactions votées par la gouvernance. Les fonctions d'une proposition sont initiées par le contrat Timelock. Les transactions en file d'attente peuvent être exécutées après un délai et avant l'expiration du délai de grâce.
* Le contrat **`Verrouillage prioritaire`** : identique au contrat de verrouillage, mais permet à un contrôleur prioritaire d'exécuter des transactions dans la **période prioritaire** (7 jours) avant la fin du délai de verrouillage.

![Architecture du contrat intelligent](../.gitbook/assets/1-smart-contract-architectue.png)

La gouvernance sur la chaîne dYdX permet de :

* Voter sur les propositions à exécuter par tout contrat d'exécuteur autorisé
* Instantané des portefeuilles de jetons au début d'une proposition
* Délégation séparée des pouvoirs de vote et de proposition
* Fixer des seuils de gouvernance, y compris des propositions, des quorums et des pouvoirs différentiels de vote
* Changer la façon dont les votes sont comptés (en changeant l'adresse du contrat intelligent « Stratégie de gouvernance » sur le contrat Gouverneur)

## Types de propositions

Un exécuteur doit valider chaque type de proposition.

#### **Exécuteur de courte durée**

L'exécuteur de courte durée contrôle les éléments suivants :

* Contrats incitatifs comprenant le module de liquidité, le module de sécurité et le module de distribution Merkle
* fonds dans les récompenses et les Trésoreries de la communauté
* frapper de nouveaux jetons
* tous les contrats proxy sauf le module de sécurité
* rôles de gardien sur les contrats proxy stricts

**Exécuteur de verrouillage prioritaire Starkware**



#### **Exécuteur de longue durée**

L'exécuteur de long timelock peut exécuter des propositions qui changent généralement des parties du dYdX v3 qui affectent le cosensus de gouvernance.

#### **Exécuteur Merkle-pauser**

L'exécuteur Merkle-pauser peut exécuter des propositions qui gèlent la racine Merkle, qui est mise à jour périodiquement avec le solde cumulatif des récompenses de chaque utilisateur, permettant de distribuer de nouvelles récompenses aux utilisateurs au fil du temps, au cas où la racine proposée serait incorrecte ou malveillante. Il peut également opposer son veto aux demandes d'échange forcé par l'un des contrats proxy stricts.

Les paramètres de durée initiaux sont les suivants :

![Paramètres de verrouillage initiaux](../.gitbook/assets/1-initial-timelock-parameters.png)
