---
description: Aperçu des principaux termes liés à la gouvernance.
---

# Glossaire

**DYDX :** l'actif natif de l'écosystème DYDX, qui constitue le fondement de la gouvernance et de la sécurité du protocole dYdX. DYDX est un jeton ERC-20 qui désigne le poids du pouvoir de vote ou de proposition d'un utilisateur.

**Protocole dYdX :** protocole perpétuel de couche 2 de dYdX.

**Fondation dYdX :** une fondation indépendante, dont le siège est à Zoug, en Suisse, a été créée pour participer à propulser le protocole dYdX dans le futur.

**Contrat de jeton DYDX** : contient des instantanés du pouvoir de vote de chaque adresse à différents blocs dans le temps.

**DIP :** les propositions d'améliorations dYdX sont des propositions sur la chaîne.

**RDC** : les demandes de commentaires dYdX sont des propositions hors chaîne et la première étape requise dans le processus d'amélioration de la gouvernance.

**Quorum :** pour qu'un vote soit adopté, il doit atteindre un quorum minimum de jetons DYDX dans l'affirmative. Le but du quorum est de s'assurer que les seules mesures qui passent ont une participation électorale adéquate.

**Époch :** tous les autres contrats fonctionnent sur des cycles de 28 jours, appelés épochs.

**Période de grâce d'exécution :** la période après le vote où une proposition DIP devient exécutable, pendant laquelle elle doit être exécutée.

**Contrat de stratégie de gouvernance** : contient une logique pour mesurer le pouvoir relatif des utilisateurs à proposer et à voter.

**Contrat gouverneur** : suit les propositions et peut exécuter des propositions via le contrat intelligent Timelock.

**Exécuteur de longue durée :** l'exécuteur de longue durée peut exécuter des propositions qui modifient généralement des parties du protocole qui affectent le consensus de gouvernance.

**Exécuteur Merkle-pauser :** l'exécuteur Merkle-pauser peut exécuter des propositions qui bloquent la racine Merkle, qui est mise à jour périodiquement avec le solde cumulatif des récompenses de chaque utilisateur, permettant de distribuer de nouvelles récompenses aux utilisateurs au fil du temps, au cas où la racine proposée serait incorrecte ou malveillante.

**Pool de sécurité :** composant chargé de protéger le protocole contre l'insolvabilité.

**Contrat dYdX staké** : contient des logiques pour staker des jetons DYDX, tokeniser la position et obtenir des récompenses.

**Exécuteur de courte durée :** l'exécuteur de courte durée peut exécuter des propositions qui modifient généralement les contrats de récompenses et d'incitation ou la trésorerie de la communauté qui nécessitent une intervention rapide

**Exécuteur Starkware :** l'exécuteur Starkware peut exécuter des propositions qui modifient généralement des parties du protocole qui nécessitent actuellement l'intervention de Starkware.

**Contrat Timelock** : peut mettre en file d'attente, annuler ou exécuter des transactions votées par la gouvernance. Les fonctions d'une proposition sont initiées par le contrat Timelock. Les transactions en file d'attente peuvent être exécutées après un délai et tant que la période de grâce n'est pas terminée.

**Délai de verrouillage :** le délai avant qu'une proposition DIP ne soit exécutée une fois qu'une proposition a été acceptée et mise en file d'attente.

**Seuil de proposition :** pour empêcher un système où d'innombrables propositions de spam sont créées, un seuil de proposition exige qu'une adresse ait un certain nombre de votes avant de pouvoir faire une proposition.

**Pouvoir de proposition :** participation symbolique donnant accès à la création et au maintien d'une proposition.

**Pouvoir de vote :** pouvoir de vote utilisé pour voter pour ou contre les propositions existantes.

**Délai de vote :** il s'agit entre le moment où une proposition peut être créée et celui où elle est disponible pour être votée. En exigeant au moins un bloc pour passer, la gouvernance est protégée contre les attaques Flash Loan qui pourraient emprunter un grand nombre de jetons, proposer un vote et voter sur le tout en un seul bloc.

**Période de vote :** une fois qu'une proposition DIP a été présentée, les membres de la communauté DYDX devront voter avant la fin de la période de vote. Il s'agit de la durée pendant laquelle les propositions sont disponibles pour être votées, avec le temps dans les blocs Ethereum.

**Seuil de proposition :** nombre minimal de jetons détenus/délégués requis pour créer une proposition DIP.

**Différentiel de vote :** écart obligatoire oui-non pour que la proposition DIP soit acceptée.
