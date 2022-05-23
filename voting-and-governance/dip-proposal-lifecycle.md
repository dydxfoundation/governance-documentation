---
description: Aperçu du cycle de vie de la proposition d'amélioration dYdX (DIP).
---

# Cycle de vie de la proposition

## **Étapes de la proposition**

Le processus de gouvernance dYdX est alimenté par des forums de gouvernance sur [**forums.dydx.community**](https://forums.dydx.community) et ratifié par le biais de propositions d'amélioration dYdX (« DIP »).

Ci-dessous, nous décrivons un avant-projet expliquant comment le processus de gouvernance dYdX se déroulera, de la conception et de la définition du concept à la mise en œuvre effective. Ces processus sont susceptibles d'être modifiés en fonction des commentaires de la communauté DYDX.

L'organigramme suivant représente les étapes initiales proposées pour passer une proposition :

![Stages of a DIP](<.. /.gitbook/assets/image (81).png>)

## 0. Discussion sur le forum

Tout le monde peut s'inscrire et créer un fil de discussion sur n'importe quel sujet sur les forums de gouvernance de dYdX hébergés sur [**forums.dydx.community**](https://forums.dydx.community). Les membres de la communauté doivent s'inscrire en utilisant une adresse e-mail ou un portefeuille Ethereum.

## 1. Création de la DRC (hors chaîne)

La création **de demandes de commentaires (DRC) dYdX** hors chaîne est la première étape du processus d'amélioration de la gouvernance. Tout le monde peut participer au Forum sur la gouvernance, créer des DRC hors chaîne et discuter des améliorations.

Pour créer une DRC, utilisez [ce modèle](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) (disponible sur notre Github). La DRC devrait couvrir toutes les informations du DIP potentiellement final.

Au minimum, les DRC doivent comprendre :

* Des titres courts et concis de la DRC
* Une description courte et concise de la proposition
* La justification de la DRC, par exemple pourquoi ?
* Le titre de la publication du forum doit inclure la DRC : avec le titre abrégé de la DRC. Par exemple : DRC : nouvelle demande de marché
* Un sondage communautaire que les membres de la communauté peuvent utiliser pour voter sur les améliorations hors chaîne

## 2. Discussion et commentaires sur la DRC

Une fois postés sur le forum de gouvernance, toutes les questions et commentaires doivent être traités et pris en considération, pour améliorer encore la RDC.

## 3. Vote Snapshot de la DRC

Les sondages Snapshot ont deux objectifs : la signalisation des sentiments pour les futurs DIP sur la chaîne et les votes contraignants pour les variables contrôlées hors chaîne.

Une fois qu'une RDC hors chaîne a un consensus très approximatif, un membre de la communauté détenant plus de `10 000` DYDX peut créer un **vote hors chaîne** pour la RDC sur **Snapshot**. Nous encourageons la communauté dYdX à créer des sondages Snapshot le lundi pour augmenter la visibilité pendant la semaine de travail normale.

Snapshot est une interface de vote simple qui permet aux utilisateurs de signaler une opinion hors chaîne. Les votes sur Snapshot sont pondérés par le pouvoir de vote de l'adresse utilisée pour voter.

Pour les sondages Snapshot liés à la signalisation de sentiment, le proposant devra fournir :

* détails de la DRC,
* un système de vote,
* une période de vote - la date de début du vote et la date de fin du vote sont définies sur une période de vote de 4 jours, et
* un délai de vote - un numéro de bloc Snapshot qui est de 6570 blocs (environ 1 jour) dans le futur. Le numéro de bloc Snapshot verrouille l'état des membres de la communauté qui peuvent voter. Les détenteurs de jetons qui détiennent des jetons avant le numéro de bloc Snapshot sont éligibles pour voter. Avant le snapshot du pouvoir de vote respectif de chaque adresse, le délai de vote donne aux détenteurs de DYDX/stkDYDY le temps d'acquérir des jetons, de déléguer le pouvoir de vote et de déplacer des jetons entre les portefeuilles (le déplacement de jetons entre les portefeuilles ne s'applique qu'aux détenteurs de DYDX).

Pour les décisions qui ne nécessitent pas d'appel de contrat intelligent sur la chaîne, notamment les modifications apportées aux formules de récompenses du fournisseur de trading et de liquidité, les votes Snapshot sont considérés comme le vote contraignant et final. Le proposant devra inclure les exigences ci-dessus et fournir :

* options de vote binaires - pour plus de clarté, une adresse vote pour ou contre une proposition.

Le ou les changements proposés seront mis en œuvre par dYdX Trading Inc. si les résultats du sondage Snapshot satisfont :

* le quorum minimum - au moins 1 million de DYDX/stkDYDX. Le quorum minimum contribue à la décentralisation de la prise de décision et protège contre la prise de décision unilatérale, et
* le différentiel de vote minimum - au moins 67 % des votes doivent être en faveur de la proposition. Le différentiel de vote minimum aide à filtrer les propositions qui sont très controversées et nécessitent une discussion plus approfondie.

dYdX Trading Inc. aura jusqu'à 1 Époch (28 jours), une période de grâce d'exécution, pour mettre en œuvre les modifications à partir d'un sondage Snapshot réussi.

Notez que les propositions et les votes ne sont que des messages signés, stockés sur IPFS et disponibles via le portail du Commonwealth.

## 4. Création de DIP (sur la chaîne)

Lorsqu'un consensus approximatif est atteint, un DIP sur la chaîne peut être soumis par un membre de la communauté qui détient suffisamment de pouvoir de proposition pour le type de proposition. Un DIP sur la chaîne est lancé via un appel de contrat intelligent. La proposition doit être basée sur le résultat gagnant du vote DIP hors chaîne sur Snapshot et peut consister en une ou plusieurs actions, jusqu'à un maximum de 10 actions par proposition.

Une création de DIP est soumise à un nombre minimum de jetons détenus/délégués requis pour un compte. Un exécuteur Verrouillage doit être spécifié lorsqu'une proposition est créée. Les paramètres initiaux sont les suivants (et peuvent être modifiés par la gouvernance) :

| Paramètre | Description | Exécuteur de courte durée | Exécuteur Merkle-pauser | Exécuteur de longue durée | Exécuteur Starkware |
| ------------------ | ------------------------------------------------ | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Seuil de proposition | Jetons minimaux détenus/délégués pour créer une proposition | 0,5 % de l'offre totale | 0,5 % de l'offre totale | 2 % de l'offre totale | 0,5 % de l'offre totale |

## 5. Voter le DIP (en chaîne)

Après la création d'un DIP sur la chaîne, la proposition entre dans un état `d'attente` pendant une période définie par le **délai de vote**, qui est actuellement configuré sur `6570` blocs ou environ 1 jour (en supposant 13 secondes par bloc). En d'autres termes, les snapshots d'utilisateurs sont enregistrés 1 jour après la création du DIP, moment auquel la proposition passe à un état `actif`.

Après le délai de vote, la période de vote est activée. La durée de la période de vote dépend du type de proposition.

Le graphique suivant montre un diagramme d'état DIP :

![Lifecycle of a DIP](<.. /.gitbook/assets/image (63).png>)

Une fois qu'un DIP est créé sur la chaîne, il est soumis à un **délai de vote**, une **période de vote**, un **quorum minimum** et un **différentiel de vote** minimum. Les paramètres initiaux sont les suivants :

| Paramètre | Description | Exécuteur de courte durée | Exécuteur Merkle-pauser | Exécuteur de longue durée | Exécuteur Starkware |
| ----------------- | ----------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Délai de vote | Nombre de blocs Ethereum à attendre avant que le vote sur une proposition puisse commencer après la soumission d'une proposition | 6570 blocs | 6570 blocs | 6570 blocs | 6570 blocs |
| Période de vote | Durée pendant laquelle les propositions sont disponibles pour être soumises au vote | 4 jours | 2 jours | 10 jours | 4 jours |
| Quorum minimum | Votes positifs minimum pour qu'une proposition DIP soit adoptée | 2 % de l'offre totale | 1 % de l'offre totale | 10 % de l'offre totale | 2 % de l'offre totale |
| Différentiel de vote | Écart obligatoire oui-non pour qu'une proposition DIP soit acceptée | 0,5 % de l'offre totale | 0,5 % de l'offre totale | 10 % de l'offre totale | 0,5 % de l'offre totale |

Seul le délai de vote peut être modifié par la gouvernance, et il ne peut être modifié qu'à des valeurs comprises entre (inclus) le délai minimum et maximum. La période de vote, le quorum minimum et le différentiel de vote ne peuvent pas être modifiés.

## 6. Mise en file d'attente et exécution des propositions

Après l'expiration d'un DIP, n'importe quelle adresse peut appeler la méthode de la file d'attente pour déplacer la proposition dans la file d'attente de verrouillage. Un DIP ne peut être mis en file d'attente que s'il est passé.

| Paramètre | Description | Exécuteur de courte durée | Exécuteur Merkle-pauser | Exécuteur de longue durée | Exécuteur Starkware |
| ---------------------- | ------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Délai de verrouillage | Une fois qu'une proposition a été acceptée et mise en file d'attente, le délai avant l'exécution de la proposition | 2 jours | 0 jour | 7 jours | 2-9 jours |
| Période de grâce d'exécution | Le temps après lequel une proposition devient exécutable, pendant lequel elle doit être exécutée. | 7 jours | 7 jours | 7 jours | 7 jours |
| Délai de durée minimum | Délai minimum avant l'exécution d'une proposition (après mise en file d'attente) | 1 jour | 0 jour | 5 jours | 4 jours |
| Délai de durée maximum | Délai maximum avant l'exécution d'une proposition (après mise en file d'attente) | 7 jours | 1 jour | 21 jours | 21 jours |

Dès que la période de vote se termine et qu'une proposition a réussi, n'importe qui peut appeler la file d'attente pour commencer le délai de verrouillage.

Pour l'exécuteur de verrouillage horaire prioritaire Starkware, il a une période de priorité de 7 jours sur le délai de verrouillage horaire de 9 jours. Cela signifie qu'après 9 jours, n'importe qui peut exécuter une proposition, mais dans les jours 2 à 9 (la période de priorité), Starkware a la possibilité d'exécuter la proposition.

Concrètement c'est :

* Jours 0-2 : personne ne peut exécuter
* Jours 2-9 : seul Starkware peut exécuter
* Jours 9 : n'importe qui peut exécuter

## 7. (Facultatif) Annulation de la proposition

À tout moment du cycle de vie d'un DIP, le proposant peut annuler le DIP. Une proposition peut être annulée par n'importe qui avant d'être exécutée si le proposant n'a pas suffisamment de puissance de proposition au niveau du bloc actuel.



## FAQ

### Quel est le but du délai de vote ?

Le **délai de vote** est le nombre de blocs Ethereum à attendre avant que le vote sur une proposition puisse commencer après la soumission d'une proposition.

Le pouvoir de vote de DYDX doit être délégué à une adresse soit entièrement avant qu'une proposition ne soit soumise, soit pendant le **délai de vote** de la proposition.

Pour l'instant, le **délai de vote** est fixé à `6 570 blocs`, soit environ 1 jour. Cette valeur est ajoutée au numéro de bloc actuel lorsqu'une proposition est créée.

À l'avenir, la gouvernance dYdX pourra voter pour augmenter ou diminuer le **délai de vote**. Bien qu'il y ait des avantages évidents à augmenter le **délai de vote.** Cela peut introduire des effets indésirables potentiels tels que l'exploitation opportuniste des cas périphériques.

### Quel est l'objectif du seuil de proposition ?

Étant donné que DYDX est un actif librement négociable, n'importe qui peut tenter une prise de contrôle de la gouvernance via l'achat sur le marché. Cela dit, forcer un vote de mauvaise foi nécessiterait un minimum de 5 millions de DYDX en cas de durée courte ou 20 millions de DYDX en cas de durée longue. Si ce n'est pas carrément impossible, ce montant serait prohibitif et coûterait probablement plus cher, si l'on tient compte de la fluctuation des prix, que le gain net de l'attaque.

Si un groupe réalisait d'une manière ou d'une autre une prise de contrôle de mauvaise foi, le délai de verrouillage donnerait aux agents concernés le temps de retirer leurs actifs du protocole. Ce serait également l'occasion de bifurquer le protocole, une voie qui serait probablement empruntée par les acteurs de bonne foi restants.

###
