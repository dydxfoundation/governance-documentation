---
description: Aperçu des paramètres de gouvernance.
---

# Paramètres

**\[LA PAGE DES PARAMÈTRES EST EN COURS DE DÉVELOPPEMENT ET SERA BIENTÔT MIS À JOUR]**

Au moment du lancement de la gouvernance, les détenteurs de DYDX ont un contrôle immédiat et irrévocable sur :

* Allocation de la trésorerie de la communauté
* Nouvelles listes de jetons sur le protocole
* Paramètres de risque pour le protocole
* Allocations de capital aux teneurs de marché dans le pool de staking de liquidité
* Ajout de nouveaux teneurs de marché au pool de staking de liquidité
* Détermination des paiements du pool de mise de sécurité en cas de perte
* Modification de l'une des récompenses et des pools existants au lancement
* La gouvernance se contracte

La gouvernance dYdX a le contrôle des paramètres des contrats suivants :

* [Verrouillage](https://github.com/dydxfoundation/governance-docs/tree/28153eacbdaafb32078630fafa7ad64f111ac9ab/voting-and-governance-process/parameters.md#timelock-parameters)
* Verrouillage prioritaire
* Gouverneur
* Jeton DYDX
* Trésorerie
* Distributeur Merkle
* Staking de liquidité
* Module de sécurité
* Proxy Stark
* Stark Perpetual

## Paramètres de verrouillage

![](<.. /.gitbook/assets/image (77).png>)

## Paramètres du gouverneur

| Paramètre | Description | Valeur |
| ----------------- | ----------------------------------------------------------------------------- | -------------- |
| Délai de vote | Délai (en blocs) entre la création de la proposition et le vote sur la proposition | 6570 blocs |
| Ajouter le rôle d'exécuteur | Adresse pouvant ajouter de nouveaux exécuteurs | Courte durée |
| Rôle du propriétaire | Peut changer de stratégie / retarder le vote / annuler l'autorisation des exécuteurs + détient d'autres rôles | Longue durée |



## Jeton DYDX

| Paramètre | Description | Valeur |
| --------- | ------------------------------------------- | -------------- |
| Propriétaire | Peut frapper des jetons DYDX après la restriction de frappe | Courte durée |



## Paramètres Trésorerie des récompenses

| Paramètre | Description | Valeur |
| ----------- | ------------------------------------------------------ | -------------- |
| Propriétaire | Peut approuver ou transférer tout jeton détenu par la trésorerie | Courte durée |
| Admin Proxy | Peut mettre à niveau le contrat | Courte durée |

##

## Paramètres Trésorerie de la communauté

| Paramètre | Description | Valeur |
| ----------- | ------------------------------------------------------ | -------------- |
| Propriétaire | Peut approuver ou transférer tout jeton détenu par la trésorerie | Courte durée |
| Admin Proxy | Peut mettre à niveau le contrat | Courte durée |

##

## Distributeur Merkle

| Paramètre | Description | Valeur |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------- |
| Rôle du propriétaire | Peut mettre à jour l'adresse d'oracle des récompenses, mettre à jour le nom IPNS et est administrateur de tous les rôles | Courte durée |
| Rôle de mise à jour de la configuration | Peut définir des paramètres de récompenses, modifier le calendrier de l'époch ou modifier la période de mise à jour IPFS | Courte durée |
| Rôle de pauser | Peut suspendre les mises à jour de la racine merkle | Timelock Merkle-pauser |
| Rôle de repreneur | Peut reprendre les mises à jour de la racine merkle | Courte durée |
| Rôle d'opérateur de réclamation | Peut réclamer des récompenses au nom d'un utilisateur | Proxy de réclamations |
| Intervalle | Longueur d'une époch | 28 jours |
| Décalage | Début de l'époch zéro | 3 août 15 h 00 UTC 2021 |
| Nom IPNS | Nom IPNS où les données de récompenses sont publiées | rewards-data.dydx.foundation |
| Période de mise à jour IPFS | Période de temps après la fin de l'époch après laquelle les nouvelles statistiques d'échange d'époch devraient être disponibles sur IPFS via le nom IPNS | 3 minutes |
| Admin Proxy | Peut mettre à niveau le contrat | Courte durée |

##

## Staking de liquidité

| Paramètre | Description | Valeur |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Rôle du propriétaire | Administrateur de tous les rôles | Courte durée |
| Rôle des paramètres Époch | Peut définir des paramètres d'époch tels que l'intervalle, le décalage et la fenêtre de blocage | Courte durée |
| Rôle du taux de récompenses | Peut fixer le taux d'émission des récompenses | Courte durée |
| Rôle d'administrateur de l'emprunteur | Peut définir les allocations des emprunteurs et autoriser/empêcher les emprunteurs d'emprunter | Courte durée |
| Rôle d'opérateur de réclamation | Peut réclamer des récompenses au nom d'un utilisateur | Proxy de réclamations |
| Rôle d'opérateur de stake | Peut manipuler les fonds stakés de l'utilisateur (par exemple, effectuer des retraits) au nom d'un utilisateur | Courte durée |
| Rôle d'opérateur de dette | Peut réduire la dette d'emprunt et la dette des stakers | Courte durée |
| Intervalle | Longueur d'une époch | 28 jours |
| Décalage | Début de l'époch zéro | 3 août 15 h 00 UTC 2021 |
| Fenêtre de blocage | Longueur de la fenêtre de blocage | 14 jours |
| Taux d'émission des récompenses | Jetons alloués aux stakers sous forme de récompenses par seconde | 0,1585489619 \* 10^18 (en wei) |
| Allocations d'emprunt | Pourcentage des fonds alloués à chaque emprunteur | Wintermute 25 %, Amber 25 %, Sixtant 20 %, Kronos 20 %, DAT Trading 10 % |
| Admin Proxy | Peut mettre à niveau le contrat | Courte durée |

## Module de sécurité

| Paramètre | Description | Valeur |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------------ |
| Rôle du propriétaire | Administrateur de tous les rôles | Courte durée |
| Rôle de réducteur | Peut réduire les soldes de jetons stakés et retirer ces fonds | Courte durée |
| Rôle des paramètres Époch | Peut définir des paramètres d'époch tels que l'intervalle, le décalage et la fenêtre de blocage | Courte durée |
| Rôle du taux de récompenses | Peut fixer le taux d'émission des récompenses | Courte durée |
| Rôle d'opérateur de réclamation | Peut réclamer des récompenses au nom d'un utilisateur | Proxy de réclamations |
| Rôle d'opérateur de stake | Peut manipuler les fonds stakés de l'utilisateur (par exemple, effectuer des retraits) au nom d'un utilisateur | Courte durée |
| Intervalle | Longueur d'une époch | 28 jours |
| Décalage | Début de l'époch zéro | 3 août 15 h 00 UTC 2021 |
| Fenêtre de blocage | Longueur de la fenêtre de blocage | 14 jours |
| Taux d'émission des récompenses | Jetons alloués aux stakers sous forme de récompenses par seconde | 0,1585489619 \* 10^18 (en wei) |
| Admin Proxy | Peut mettre à niveau le contrat | Longue durée |

## Proxy Stark

| Paramètre | Description | Valeur |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Rôle du propriétaire | Peut ajouter/supprimer des destinataires qui reçoivent des fonds + des clés STARK, définir des allocations ERC20 sur le staking de liquidités et des contrats perpétuels stark, appeler des actions forcées et est administrateur des rôles d'administrateur propriétaire + délégation | Teneur de marché |
| Rôle d'administrateur de la délégation | Est administrateur des rôles d'emprunteur, d'opérateur d'échange et d'opérateur de retrait | Teneur de marché |
| Rôle d'emprunteur | Peut appeler des fonctions d'emprunt sur le contrat de staking de liquidité | Teneur de marché |
| Rôle d'opérateur d'échange | Peut appeler des fonctions d'échange sur le contrat perpétuel stark | Teneur de marché |
| Rôle d'opérateur de retrait | Peut retirer des fonds dépassant le solde emprunté à un destinataire autorisé | Teneur de marché |
| Rôle de gardien | Peut effectuer des actions de fermeture, effectuer des actions de force si l'emprunteur a un impayé, restreindre les actions ouvertes avec des fonds empruntés et approuver un montant symbolique à retirer en externe par le rôle d'opérateur de retrait. | Courte durée |
| Rôle de gardien de veto | Peut opposer son veto aux demandes d'échange forcé initiées par le propriétaire, pendant la période d'attente | Timelock Merkle-pauser |

## Stark Perpetual

| Paramètre | Description | Exécuteur de courte durée | Exécuteur Merkle-pauser | Exécuteur de longue durée | Exécuteur Starkware |
| -------------------------------------- | ----------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Ajouter un nouvel actif |             | N | N | N | Y |
| Modifier la configuration de l'actif existant |             | N | N | N | Y |
| Admin Proxy |             | N | N | N | Y |
| Ajouter un opérateur |             | N | N | N | Y |
| Supprimer l'opérateur |             | N | N | N | Y |
| Ajouter un vérificateur |             | N | N | N | Y |
| Supprimer le vérificateur |             | N | N | N | Y |
