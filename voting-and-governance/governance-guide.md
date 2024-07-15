---
description: >-
  Un aperçu étape par étape du processus de gouvernance Création de la DRC, création de sondage Snapchot, création de DIP, vote sur un sondage Snapshot, vote sur une DIP, mise en file d'attente d'une DIP et exécution d'une DIP
---

#

La Fondation dYdX a créé ce guide pour aider la communauté dYdX à comprendre le processus de gouvernance dYdX. Le guide fournit un aperçu étape par étape de :

* [Discussions du forum (hors chaîne)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Création d'une RDC (hors chaîne)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Création de sondage Snapshot (hors chaîne)](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [Voter sur un sondage Snapshot](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [Création d'une DIP (hors chaîne)](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [Création d'une DIP (sur la chaîne)](governance-guide.md#step-1-on-chain-dip-drafting)
* [Voter sur une DIP (sur la chaîne)](governance-guide.md#how-to-vote-on-a-dip)
* [Mettre en file d'attente une DIP (sur la chaîne)](governance-guide.md#how-to-queue-a-proposal)
* [Exécuter une DIP (sur la chaîne)](governance-guide.md#how-to-execute-a-proposal)

Les deux exemples présentés dans le guide sont une _DIP 2 (proposition hors chaîne) - Réduction du seuil de récompense des fournisseurs de liquidité_ et _une DIP 3 (proposition sur la chaîne) - Restauration du module de sécurité_.

## DIP 2 (Proposition hors chaîne) - Réduction du seuil de récompense des fournisseurs de liquidité

_**Résumé :**_

À l'époch 6, la communauté dYdX a voté sur [Snapshot](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43) pour réduire le seuil de volume de récompenses LP pour les teneurs de marché de 1 % à 0,25 %. La réduction du seuil de récompenses LP de 5 % à 1 % à l'epoch 2 a suivi le même processus que la réduction à l'epoch 6 (1 % à 0,25 %). L'aperçu étape par étape pour réduire le seuil de volume des récompenses LP de 5 % à 1 % est inclus ci-dessous.

Un grand nombre de membres de la communauté (399 votants et 86 % de $ethDYDX) a voté sur [Snapshot](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN) pour réduire le seuil de volume pour obtenir des récompenses de fournisseur de liquidité de 5 % à 1 %. Une [DIP hors chaîne](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md) visant à réduire le seuil de volume des récompenses du fournisseur de liquidités pour les teneurs de marché de 5 % à 1 % a été soumis par Jacob Goh (jteam0x) chez DeFiance Capital. Les teneurs de marché qui atteignaient le seuil de 1 % à l'epoch 2 étaient éligibles pour gagner des récompenses de fournisseur de liquidités à l'epoch 3. La proposition ne nécessitait aucune modification des contrats intelligents en chaîne.

_**Contexte :**_

Dans le cadre du [programme de récompenses](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards) des fournisseurs de liquidités, 1 150 685 $ethDYDX sont distribués par epoch (28 jours) aux fournisseurs de liquidités qui commercialisent le protocole. Les récompenses sont distribuées sur la base d'une formule récompensant une combinaison de temps de disponibilité, de profondeur bilatérale, d'écarts acheteur-vendeur et du nombre de marchés pris en charge. Pour être éligibles à ce programme de récompenses, les fournisseurs de liquidités doivent fournir un pourcentage minimum du volume total du fabricant au cours de l'époch précédente.

La communauté dYdX a « un contrôle immédiat et irrévocable sur » le seuil de récompenses des fournisseurs de liquidités. Le lien de la liste complète des paramètres que la communauté contrôle se trouve [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

La communauté était motivée à abaisser le seuil de récompenses des fournisseurs de liquidité, car cela inciterait les nouveaux teneurs de marché et les teneurs de marché de petite et moyenne taille à augmenter la liquidité sur la plate-forme dYdX. De plus, l'augmentation du nombre de teneurs de marché sur la plate-forme aide le protocole dYdX à devenir plus décentralisé.

Ensuite, nous fournissons un aperçu étape par étape du fonctionnement pratique de la gouvernance dYdX. Vous pouvez trouver plus d'informations sur le processus de gouvernance dYdX [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

### **ÉTAPE 1 - Discussions sur le forum, création d'une DRC (hors chaîne) et commentaires sur la DRC**

_**Description :**_

Le processus de gouvernance dYdX est alimenté par [des forums de gouvernance](https://dydx.forum/). Les membres de la communauté publient et commentent les fils de discussion pour parvenir à un consensus approximatif hors chaîne. Plus d'informations sur les discussions de forum et la création d'une DRC sont liées [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle). \

\Note - Le sous-DAO des opérations a lancé le nouveau forum [**https://dydx.forum/**](https://dydx.forum/) sur le [vote de la communauté pour la transition du Commonwealth au Discours](https://snapshot.org/#/dydxgov.eth/proposal/0xa5e77732dd24edd26bd41b089969b3662c29eb41c3bacd35cb2931ca55882a8f). Certaines références dans ce guide aux discussions précédentes de la DRC indiqueront toujours le Commonwealth, mais toute nouvelle discussion devrait être en cours sur le forum de [**Discours**](https://dydx.forum/) nouvellement lancé. \


_**Candidature à la DIP 2 :**_

Su Zhu (zhusu) de Three Arrows Capital a créé un [forum de discussion hors chaîne](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/) pour abaisser le seuil de récompenses des fournisseurs de liquidités. Divers membres de la communauté, tels qu'Evgeny de Wintermute, Ben de Kronos, Josh de Sixtant et bien d'autres, ont participé à la discussion et ont offert de précieux commentaires.

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives.png)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives-2.png)

#### _Comment envoyer un commentaire sur Discours :_

* Inscrivez-vous sur Discours avec votre compte e-mail et rejoignez dYdX [ici](https://dydx.forum/).

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 10.59.27 AM.png" alt=""><figcaption></figcaption></figure>

* Sélectionnez un fil, faites défiler les commentaires et aimez ou répondez aux commentaires.
* Créez un nouveau fil de discussion ou postez une DRC en cliquant sur « **Nouveau sujet** » et en sélectionnant la catégorie de sujet.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.03.33 AM.png" alt=""><figcaption></figcaption></figure>

* Si vous créez une DRC, veuillez suivre le modèle lié [ici](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md). Comme indiqué dans la rubrique _Création de la DRC_ dans le [cycle de vie de la proposition](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle), les DRC doivent au minimum inclure les éléments suivants :
  * Un titre court et concis de la DCR.
  * Une description courte et concise de la proposition.
  * La justification de la DRC (par exemple, pourquoi ?).
  * Le titre du post du forum doit inclure DRC : \[insérer un court titre du DRC] (Ex. DRC : Nouvelle demande de marché).
  * Un sondage communautaire que les membres de la communauté peuvent utiliser pour voter sur les améliorations hors chaîne.

### **ÉTAPE 2 - Sondage Snapshot DRC (hors chaîne)**

_**Description :**_

Une fois que la communauté est parvenue à un consensus approximatif, un membre de la communauté avec un pouvoir de proposition de 10 000 peut créer un vote hors chaîne pour la RDC sur [Snapshot](https://snapshot.org/#/). [Le pouvoir de proposition](https://docs.dydx.community/dydx-governance/voting-and-governance/voting) donne accès à la création et au maintien d'une proposition. Snapshot est une interface de vote simple qui permet aux utilisateurs de signaler une opinion hors chaîne. La pondération des votes sur l'instantané est fonction du nombre de jetons de gouvernance détenus par ou délégués à l'adresse utilisée pour voter. Le membre de la communauté qui crée le sondage Snapshot doit fournir des détails sur la DRC, un système de vote, la date de début du vote, la date de fin du vote et le numéro de bloc Snapshot. La période de vote devrait être de 5 jours et le vote devrait commencer après un délai de vote d'1 jour (_basé sur 13,2 deuxième temps de bloc)_. Le délai de vote donne du temps aux membres de la communauté dYdX d'en savoir plus sur la DRC, d'acheter $ethDYDX ou de déléguer le pouvoir de vote de leurs jetons de gouvernance. Sont éligibles au vote les membres de la communauté qui détiennent des jetons de gouvernance ou qui ont reçu un pouvoir de vote délégué avant le numéro de bloc Snapshot. Vous pouvez trouver plus d'informations sur le sondage Snapshot [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

_**Candidature à la DIP 2 :**_

Les membres de la communauté ont fourni des commentaires sur la publication de Su Zhu. Les seuils de récompenses suivants ont été suggérés par la communauté :

* [0,5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Su Zhu de Three Arrows Capital,
* [1 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) - Sam de BitTrading,
* [2,5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Ben du réseau Kronos / WOO et
* [5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - Evgeny de Wintermute.

Ensuite, Su Zhu a créé un sondage Snapshot avec les options suivantes :

* Abaisser le seuil de MM à 1 %
* Abaisser le seuil de MM à 2,5 %
* Maintenir le seuil de MM à 5 %

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-create-snapshot.png)

#### _Comment voter sur un sondage Snapshot :_

* Inscrivez-vous sur Snapshot avec votre portefeuille Ethereum et suivez les propositions dYdX [ici](https://snapshot.org/#/dydxgov.eth).

![https://snapshot.org/#/dydxgov.eth](../.gitbook/assets/2-register-snapshot.png)

* Pour voter sur des sondages Snapshot actifs, vous devez détenir des jetons de gouvernance ou avoir un pouvoir de vote délégué à votre adresse avant le numéro de bloc Snapshot lorsque le sondage Snapshot devient actif.
* Pour voter, cliquez sur la proposition et sélectionnez « Oui » ou « Non » suivi de « Voter ».

#### _Comment créer un sondage sur Snapshot :_

* Pour créer un sondage Snapshot, vous devrez **détenir un minimum de 10 000 de jetons de gouvernace** **et/ou disposer d'un pouvoir de proposition délégué à l'adresse que vous utilisez** pour créer la proposition.
* La proposition Snapshot peut consister en une ou plusieurs actions, jusqu'à un maximum de 10 actions par proposition. Les actions sont des changements spécifiés dans une proposition.
* Si vous remplissez l'exigence minimale de puissance de proposition de 10 000, sélectionnez « **Nouvelle proposition** » et remplissez les champs ouverts conformément aux exigences de contenu ci-dessous.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.08.42 AM.png" alt=""><figcaption><p>Page Snapshot de dYdX - bouton « Créer une nouvelle proposition »</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.09.33 AM.png" alt=""><figcaption><p>Inclure les détails du Snapshot ici, et assurez-vous d'inclure un lien vers la DRC</p></figcaption></figure>

Exigences de contenu du sondage Snapshot DRC :

* détails de la DRC avec un lien vers le forum de discussion,
* un système de vote,
* la date de début et la date de fin du vote sont fixés à 4 jours de longueur totale (_basé sur 13,2 deuxième temps de bloc)_, et
* le sondage Snapshot est publié à 1 jour (\~6570 blocs) avant le début du vote.

Exigence pour les sondages Snapshot contraignants :

Pour la plupart des décisions, un sondage Snapshot sert de signal, tandis qu'un vote sur la chaîne est requis pour un résultat contraignant qui modifie le ou les contrats intelligents. Pour les décisions qui ne nécessitent pas d'appel de contrat intelligent sur la chaîne, notamment les modifications apportées aux formules de récompenses du fournisseur de trading et de liquidité, les votes Snapshot sont considérés comme le vote contraignant et final. En plus des exigences de contenu ci-dessus, les sondages Snapshot qui sont des votes contraignants pour les variables contrôlées hors chaîne doivent inclure :

* Options de vote binaire. Pour plus de clarté, une adresse signifie voter pour ou contre une proposition.

![](../.gitbook/assets/2-snapshot-binary-voting.png)

* Après le vote, les informations connexes seront stockées sur IPFS et un rapport sera automatiquement généré et disponible au téléchargement.

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-snapshot-ipfs.png)

### **ÉTAPE 3 - Création d'une DIP (proposition hors chaîne)**

_**Description** :_

Une DIP doit être créé lorsque (1) un sondage Snapshot entraîne la mise à jour d'un paramètre hors chaîne (tel que des modifications des formules Trading Rewards ou LP Rewards) et (2) lorsqu'un membre de la communauté souhaite soumettre une proposition de modification de contrats intelligents en chaîne. Pour les votes qui ne nécessitent aucune mise à jour de contrat intelligent sur la chaîne, le résultat du sondage Snapshot doit être formalisé dans une DIP hors chaîne et soumis via une demande d'extraction à la branche Pending-DIP du Github de la Fondation dYdX. La DIP doit refléter le résultat gagnant du Snapshot. La DIP doit spécifier les informations incluses dans le modèle lié [ici](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md).

_**Candidature à la DIP 2 :**_

Dans ce cas, la [DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md) a été rédigée par @Jteamdc.

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](../.gitbook/assets/2-dip-example.png)

Lorsque le projet de proposition pour DIP 2 a été terminé, @Jteamdc a créé une [demande d'extraction](https://github.com/dydxfoundation/dip/pull/8) \*\*\*\* de la branche de travail contre la branche Pending-DIPs de la fondation dYdX. Une fois que la Fondation dYdX a examiné la proposition et l'a approuvée, les modifications apportées aux DIP en attente ont été fusionnées avec la branche principale.

![https://github.com/dydxfoundation/dip/pulls](../.gitbook/assets/2-dip-pending-merge.png)

Étant donné que la réduction du seuil de récompenses des fournisseurs de liquidité ne nécessite aucune modification des contrats intelligents sur la chaîne, le processus est maintenant terminé et les modifications seront effectives au cours de la prochaine epoch.

#### _Comment créer une DIP :_

* La DIP doit être basé sur le résultat gagnant du vote DIP hors chaîne sur Snapshot et peut consister en une ou plusieurs actions, jusqu'à un maximum de 10 actions par proposition. Les actions sont des changements spécifiés dans une proposition. Plus d'informations peuvent être trouvées sous [Création d'une DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution).
* Inscrivez-vous pour un compte Github : [https://github.com/signup](https://github.com/signup).
* Accédez à la page de référentiel dYdX liée [ici](https://github.com/dydxfoundation/dip) et forquez le référentiel sous votre compte Github.

![https://github.com/dydxfoundation/dip](../.gitbook/assets/2-dip-create-1.png)

* Dans le référentiel DIP forké, accédez au répertoire contenant le contenu des DIP : [https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips).

![](../.gitbook/assets/2-dip-create-2.png)

* Sélectionnez le dossier dips : [https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content).

![](../.gitbook/assets/2-dip-create-3.png)

Le dossier dips comprend un répertoire des propositions précédentes qui suivent le modèle de DIP dont [le lien se trouve ici.](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md)

![https://github.com/dydxfoundation/dip/tree/master/content/dips](../.gitbook/assets/2-dip-create-4.png)

* Avant de commencer à rédiger une proposition, veuillez vous assurer que la branche que vous avez faite bifurquer est à jour avec la dernière version de la branche principale. Si vous utilisez une ancienne version du référentiel DIP, veuillez confirmer que votre version forkée est à jour avec les dernières modifications. Pour obtenir de l'aide pour rebaser votre version forkée, vous pouvez suivre les étapes ici : [https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master).
* Modifiez le [modèle de DIP](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) avec les informations pour votre proposition. Si vous n'avez pas forké le référentiel DIP, la sélection de l'icône de modification forkera automatiquement le référentiel principal car vous n'êtes pas un administrateur.

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](../.gitbook/assets/2-dip-create-5.png)

* Suivez le [modèle](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) et ajoutez votre DIP à votre fork du référentiel dans le répertoire `content/dips/`. Veuillez suivre les conventions de dénomination des statuts DIP incluses ci-dessous.

![](../.gitbook/assets/2-dip-create-6.png)

Statuts DIP :

* WIP - une DIP qui est toujours en cours de développement.
* Proposé - une DIP prête à être proposée sur la chaîne.
* Approuvé - une DIP dont la mise en œuvre a été acceptée par la communauté dYdX.
* Implémenté - une DIP qui a été publiée sur le réseau principal.
* Rejeté - une DIP qui a été rejetée.
* Après avoir vérifié que tout le contenu est correct, créez une demande d'extraction à partir de votre branche de travail contre la branche Pending-DIPs de la fondation dYdX. Veuillez **ne pas** soumettre cette demande d'extraction à la branche principale de la fondation dYdX, car la tâche IPFS échouera si des parties externes souhaitent fusionner avec la branche principale. Veuillez utiliser la demande d'extraction sont le lien se trouve [ici](https://github.com/dydxfoundation/dip/pull/8) comme exemple.

![](../.gitbook/assets/2-dip-status-1.png)

* Après examen, la Fondation dYdX fusionnera les modifications de la branche Pending-DIPs vers la branche principale.

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/2-dip-status-2.png)

* Avant **la fusion,** une tâche sera exécutée automatiquement pour télécharger la DIP sur IPFS. Vous pouvez vérifier le téléchargement de la DIP sur IPFS ici : [https://github.com/dydxfoundation/dip/pull/9/checks](https://github.com/dydxfoundation/dip/pull/9/checks).
* La DIP est ajoutée sous [**`dip`**](https://github.com/dydxfoundation/dip)`/`[`content`](https://github.com/dydxfoundation/dip/tree/master/content)/**`dips`**`/``/`.

![](../.gitbook/assets/2-dip-status-3.png)

Étant donné que la proposition ne nécessite aucune modification de contrat intelligent sur la chaîne, le processus est maintenant terminé et les modifications seront effectives au cours de la prochaine époch

## DIP 3 (proposition sur la chaîne) - Restauration du module de sécurité

_**Résumé :**_

Le 1er novembre, une [DIP](https://dydx.community/dashboard/proposal/3) en chaîne a été créé par Dan Robinson de Paradigm pour restaurer la fonctionnalité du pool de staking du module de sécurité. Un grand nombre des membres de la communauté (251 votants et près de 142 millions de ethDYDX) a voté en faveur du rétablissement de la fonctionnalité du module de sécurité. Après une période de vote de 10 jours, il a fallu près de 3 jours à un membre de la communauté pour appeler la file d'attente et déplacer la proposition dans le délai de 7 jours. Le 20 novembre, le module de sécurité a été restauré et remis à un état propre.

_**Contexte :**_

Le module de sécurité dYdX est un contrat de staking conçu pour démarrer un pool de fonds décentralisé qui peut être utilisé pour soutenir le protocole dYdX. Les utilisateurs mettent $ethDYDX dans le pool de sécurité et reçoivent $stkDYDX (1 : 1). $stkDYDX est une position tokenisée transférée en tant que ERC-20 qui a les mêmes droits de vote et de proposition que $ethDYDX. En cas de déficit, un vote de gouvernance est nécessaire pour réduire $ethDYDX staké afin d'atténuer les pertes. À partir de l'approvisionnement en jetons $ethDYDX, 2,5 % (25 000 000 $ethDYDX) de l'approvisionnement en jetons seront distribués aux utilisateurs qui stakent des ethDYDX dans le pool de staking de sécurité. Vous pouvez trouver plus d'informations sur le pool de staking de sécurité [ici](https://dydx.foundation/blog/en/safety-staking).

Dans le cadre des [récompenses du pool de mise de sécurité](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool), 383 562 $ethDYDX seront distribués par époch (28 jours) aux stakers. Les récompenses sont distribuées au prorata toutes les secondes aux stakers.

La communauté dYdX a « un contrôle immédiat et irrévocable sur » les paramètres du contrat intelligent du module de sécurité. Le lien de la liste complète des paramètres que la communauté contrôle se trouve [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

La restriction de transfert sur les jetons $ethDYDX a été levée le 8 septembre à 15:00 UTC, et le staking a effectivement été ouvert au module de sécurité dYdX. Plus de 50 adresses différentes ont misé environ 157 000 DYDX pendant près d'une heure. Un bogue a provoqué une erreur dans le processus de déploiement et aucun stkDYDX n'a été envoyé aux adresses qui se sont implantées dans le module de sécurité. En conséquence, les fonds de chaque participant étaient bloqués dans le contrat et l'équipe dYdX a désactivé le staking sur l'interface utilisateur de gouvernance dYdX.

[DIP 1](https://dydx.community/dashboard/proposal/0) a proposé de restaurer la fonctionnalité du module de sécurité et de permettre aux adresses concernées de récupérer leurs fonds et de recevoir 10 % supplémentaires de leurs jetons stakés à titre de compensation pour les rendre entiers. Alors que le sentiment de la communauté était fortement en faveur du [DIP 1 - Restauration du module de sécurité et récupération des piquets](https://dydx.community/dashboard/proposal/0), la proposition a échoué car elle n'atteignait pas le quorum minimum de 100 millions de $ethDYDX requis pour qu'un vote Long Timelock soit adopté. En conséquence, Jacob Goh (jteam0x) de DeFiance Capital a créé [DIP 4 - Safety Module Staker Reimbursement and Compensation](https://dydx.community/dashboard/proposal/2) pour rembourser et indemniser les adresses concernées pour leurs récompenses et inconvénients manqués. La [DIP 4](https://dydx.community/dashboard/proposal/2) impliquait de déployer le contrat de récupération pour les tokens stakés d'utilisateurs et de compenser les adresses affectées de 10 % supplémentaires par la Trésorerie des récompenses. La DIP était régi par les paramètres de gouvernance moins stricts d'un verrouillage de courte durée.

Le cycle de vie de la proposition d'une DIP est généralement cohérent jusqu'à la création du DIP. La principale différence entre DIP 3 (en chaîne) et DIP 2 (hors chaîne) était que DIP 3 nécessitait le vote en chaîne et le déploiement de contrats intelligents. Étant donné que le processus de discussion sur le forum, la création de la DRC et la création du projet de DIP sont les mêmes, nous commençons notre discussion étape par étape avec les exigences de contenu pour rédiger La DIP sur la chaîne. Pour plus d'informations, veuillez suivre les liens ci-dessous :

* Processus de gouvernance de dYdX - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
* Rapport d'incident du module de sécurité - [https://dydx.foundation/blog/en/outage-1](https://dydx.foundation/blog/en/outage-1).
* Discussion sur forum hors chaîne **-** [https://commonwealth.im/dydx/proposition/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause).
* DRC hors chaîne **-** [https://commonwealth.im/dydx/proposition/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* Vote DRC Snapshot hors chaîne **-** [https://snapshot.org/#/dydxgov.eth/proposition/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* DIP proposé sur Github **-** [https://github.com/dydxfoundation/dip/blob/master/dips/DIP-3.md](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **ÉTAPE 1 - Rédaction DIP sur la chaîne**

_**Description :**_

La rédaction d'une DIP en chaîne qui affecte le consensus de gouvernance sur le protocole dYdX doit décrire les étapes spécifiques de la mise en œuvre des modifications de contrat intelligent. Une fois que la communauté est parvenue à un consensus approximatif à partir de Snapshot ou d'une DIP qui a précédemment échoué, un membre de la communauté disposant d'un pouvoir de proposition suffisant peut soumettre le nouveà la DIP sur la chaîne. Plus d'informations sur le seuil de puissance de proposition, l'exécuteur de verrouillage et d'autres paramètres de gouvernance sont liés [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).

_**Candidature à la DIP 3 :**_

Dans ce cas, la [DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md) a été rédigée par Dan Robinson de Paradigm. Étant donné que la proposition incluait des modifications de contrats intelligents sur la chaîne, la proposition comprenait un lien vers les implémentations spécifiques de contrats intelligents.

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/2-dip3-example-1.png)

La navigation du contrat de déploiement SafetyModuleV2.sol vers le dossier Safety affiche le README qui contient les détails spécifiques de la façon dont la proposition sera mise en œuvre.

![](../.gitbook/assets/2-dip3-example-1a.png)

Les étapes pour mettre en œuvre la proposition incluse dans le README se trouvent ici : [https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety).

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-2.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-3.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-4.png)

#### _Comment rédiger une DIP sur la chaîne (WIP) :_

* Créez un nouveau portefeuille pour créer la DIP. Le processus de déploiement nécessitera la saisie de votre phrase de départ en tant que variable d'environnement. Nous vous recommandons donc d'utiliser un portefeuille unique pour la création d'une DIP sur la chaîne.
* Déléguez suffisamment de pouvoir de proposition au portefeuille unique pour la création d'une DIP. Vous pouvez déléguer le pouvoir de proposition [ici.](https://dydx.community/dashboard) Les différents seuils de pouvoir de proposition sont inclus ci-dessous et liés [ici](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters).
  * Courte période de temps : 0,5 % de l'offre totale (5 M en pouvoir de proposition).
  * Exécuteur Starkware : 0,5 % de l'offre totale (5 M en pouvoir de proposition).
  * Exécuteur de longue durée : 2,0 % de l'offre totale (20 M en pouvoir de proposition).
  * Exécuteur Merkle Pauser : 0,5 % de l'offre totale (5 M en pouvoir de proposition).
* Créez une clé Alchemy. Avec la clé Alchemy, vous n'avez pas besoin d'exécuter un nœud Ethereum pour interagir avec Ethereum et déployer le contrat intelligent. Le lien du guide pour la création d'une clé Alchemy se trouve [ici](https://docs.alchemy.com/alchemy/introduction/getting-started).

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-1.png)

Sélectionnez Ethereum et « Démarrer ».

![](../.gitbook/assets/2-draft-dip-example-2.png)

Fournissez les informations requises, sélectionnez le réseau Goerli et sélectionnez « créer une application ».

<figure><img src="../.gitbook/assets/2-draft-dip-example-3.png" alt=""><figcaption></figcaption></figure>

Après avoir créé votre compte, suivez les instructions de configuration dont le lien se trouve [ici](https://docs.alchemy.com/alchemy/introduction/getting-started).

Sous « 4. Démarrer la construction », sélectionnez « essayez de déployer votre premier contrat intelligent » et suivez le guide.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-4.png)

* Ouvrez la ligne de commande Windows, l'application Terminal par défaut ou téléchargez iTerm : [https://item2.com/](https://iterm2.com/).
* Téléchargez et installez Node.js et npm si vous ne l'avez pas déjà fait : [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Hardhat est un outil de développement pour compiler et tester le logiciel Ethereum. Installez Hardhat si vous ne l'avez pas déjà fait : [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Rédigez votre projet de mise(s) en œuvre de contrat intelligent.
* Le hachage IPFS est généré automatiquement et peut être obtenu [ici](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips). Le hachage IPFS se trouvera dans le référentiel de la fondation dYdX sous le nom de fichier `DIP-[New DIP #]-ipfs-hashes.json`.

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](../.gitbook/assets/2-draft-dip-example-5.png)

* Après avoir sélectionné le nouveau fichier (`DIP-[New DIP #]-ipfs-hashes.jso`), assurez-vous d'utiliser l'encodedHash.

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](../.gitbook/assets/2-draft-dip-example-6.png)

### **ÉTAPE 2 - Soumettre une DIP sur la chaîne**

_**Description :**_

Une fois qu'un membre de la communauté a confirmé que la ou les mises en œuvre de contrats intelligents proposées sont correctes et que la DIP est finalisée, la DIP peut être soumise sur la chaîne. Lorsqu'une DIP sur la chaîne est créée, la proposition entre dans un état « En attente » pendant le délai de vote qui dure environ 1 jour (environ 6570 blocs). Les Snapshots d'utilisateurs sont enregistrés après le délai de vote pour tenir compte des avoirs $ethDYDX et du pouvoir de vote délégué. Ensuite, la proposition passe à l'état « Actif » et la durée du vote varie de 2 à 10 jours selon le type de proposition. Pour qu'une proposition soit mise en œuvre, le vote doit passer le quorum minimum et le différentiel de vote minimum qui change selon le type de proposition. Si la DIP satisfait le quorum minimum, le différentiel de vote minimum et qu'une majorité des membres de la communauté votant votent en faveur du DIP, n'importe quelle adresse peut appeler la file d'attente pour déplacer la proposition dans la file d'attente de verrouillage horaire. Les contrats de verrouillage peuvent mettre en file d'attente, annuler ou exécuter des transactions votées par la communauté dYdX. La longueur de la file d'attente de verrouillage varie en fonction du type de proposition.

_**Candidature à la DIP 3 :**_

L'équipe Paradigm a finalisé le code de solidité pour `SafetyModuleV2.sol.`

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/2-draft-dip-example-7.png)

L'équipe Paradigm a simulé les mises à jour dans un environnement de réseau principal local et bifurqué. La suite de tests a ensuite été exécutée pour s'assurer que toutes les fonctionnalités seraient restaurées, après l'exécution de la proposition de gouvernance sur le réseau principal.

L'équipe Paradigm a déployé les mises à jour du contrat intelligent en exécutant les scripts ci-dessous.

**Déploiement de récupération du module de sécurité**

`exporter ALCHEMY_KEY=<... >`

`exporter MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-recovery`\ `--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\ `--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\ `--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**Proposition de gouvernance : Correction du module de sécurité**

`exporter ALCHEMY_KEY=<... >`

`exporter MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\ `--proposal-ipfs-hash-hex 0x...`\ `--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\ `--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\ `--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\ `--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\ `--safety-module-new-impl-address 0x...`

**Proposition de gouvernance : Compensation du module de sécurité**

`exporter ALCHEMY_KEY=<... >`

`exporter MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\ `--proposal-ipfs-hash-hex 0x...`\ `--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\ `--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\ `--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\ `--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\ `--safety-module-recovery-address 0x...`

La DIP a été publiée simultanément sur [https://dydx.community/dashboard](https://dydx.community/dashboard).

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-8.png)

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-9.png)

Le contrat de gouvernance dYdX est 0x7e9b1672616ff6d6629ef2879419aae79a9018d2: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).

Le déploiement DIP peut être confirmé sur Etherscan : [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

La DIP a été créée le 1er novembre 2021, au bloc 13532376. Pour 6570 blocs dans le futur, le statut DIP est « En attente ».

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-10.png)

les détenteurs de ethDYDX ont pu voter sur la DIP lorsqu'elle est passée à un état « Actif » au bloc 13538946.

Le premier vote a eu lieu le 2 novembre 2021 à 17 h 51 min 22 s UTC (bloc 13538959), à 6583 blocs de la création de la DIP sur la chaîne.

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/2-draft-dip-example-11.png)

Après la période de vote de 10 jours associée à un verrouillage longue durée, tout membre de la communauté peut appeler la file d'attente et déplacer la proposition dans le délai de 7 jours. Pour la DIP 3, il a fallu près de 3 jours à un membre de la communauté pour appeler la file d'attente.

![https://etherscan.io/tx/0x3402372aa549d2270a6b5d4f8484ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/2-draft-dip-example-12.png)

Après le délai de verrouillage de 7 jours, la DIP a été exécutée sur la chaîne.

![https://etherscan.io/tx/0xfd332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/2-draft-dip-example-13.png)

Au moment où la DIP a été exécutée sur la chaîne, le statut des DIP sur [https://dydx.community/dashboard/proposal/3](https://dydx.community/dashboard/proposal/3) a été mis à jour sur « Exécuté ».

![](../.gitbook/assets/2-draft-dip-example-14.png)

Notez que (1) les propositions doivent être exécutées dans le délai de grâce d'exécution de 7 jours qui commence immédiatement après le délai verrouillage et (2) l'adresse de proposition doit maintenir le montant minimum de puissance de proposition requis par le contrat de verrouillage respectif jusqu'à ce que la DIP soit exécuté (soit 5 M ou 20 M en puissance de proposition).

#### _Comment soumettre une DIP sur la chaîne :_

* Assurez-vous que vous avez suffisamment de pouvoir de proposition pour créer la DIP. Vous pouvez trouver plus d'informations sous [Création d'une DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
  * Exécuteur de courte durée : 0,5 % de l'offre totale (5 M en pouvoir de proposition).
  * Exécuteur Starkware : 0,5 % de l'offre totale (5 M en pouvoir de proposition).
  * Exécuteur de longue durée : 2,0 % de l'offre totale (20 M en pouvoir de proposition).
  * Exécuteur Merkle Pauser : 0,5 % de l'offre totale (5 M en pouvoir de proposition).
* Assurez-vous qu'il y a des ETH dans le portefeuille pour payer les frais de gaz.
* Créez une application sur Alchemy pour le réseau principal Ethereum.

![https://dashboard.alchemyapi.io/](../.gitbook/assets/2-draft-dip-example-15.png)

* Une fois l'application créée, cliquez sur « Afficher la clé » pour obtenir votre clé Alchemy (7LOaQtguSm2kSEcFXQH88B) : [https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul).

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](../.gitbook/assets/2-draft-dip-example-16.png)

* Téléchargez et installez Node.js et npm : [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Installez Hardhat : [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Exécutez le script que vous avez rédigé.
* Consultez le contrat de gouvernance pour vérifier que la proposition a été créée sur la chaîne : [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).
* Avec l'adresse qui a soumis la proposition, vous devez maintenir le montant minimum de pouvoir de proposition requis par le contrat timelock respectif jusqu'à ce que la proposition soit exécutée.

#### _Comment voter sur une DIP :_

* Assurez-vous qu'il y a des ETH dans le portefeuille pour payer les frais de gaz.
* Vous pouvez voter pour une DIP active en sélectionnant la DIP à partir de : [https://dydx.community/dashboard](https://dydx.community/dashboard).

![](../.gitbook/assets/2-draft-dip-example-17.png)

La durée du vote dépend du type de proposition. Plus d'informations peuvent être trouvées sous [Création d'une DIP](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

* Exécuteur de courte durée : 4 jours.
* Exécuteur Starkware : 4 jours.
* Exécuteur de longue durée : 10 jours.
* Exécuteur Merkle Pauser : 2 jours.

#### _Comment mettre une proposition en file d'attente :_

Une proposition réussie peut être mise en file d'attente pour démarrer le délai de verrouillage.

* Assurez-vous que vous utilisez un portefeuille compatible contenant Eth.
* Allez dans l'onglet « Contrat » sur Etherscan et cliquez sur « Écrire un contrat" » Le line du contrat de gouvernance se trouve [ici](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-queue-1.png)

* Sélectionnez la file d'attente et soumettez le « proposalId ».

![](../.gitbook/assets/2-draft-dip-example-queue-2.png)

Le « proposalId » se trouve sur Etherscan lors de la création de la DIP : [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

* Sélectionnez « cliquez pour voir plus ».

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-3.png)

* Sélectionnez « Décoder les données d'entrée ».

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-4.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-5.png)

#### _Comment exécuter une proposition :_

Après le délai de verrouillage, une proposition réussie peut être exécutée.

* Allez dans l'onglet "Contrat" sur Etherscan et cliquez sur "Écrire un contrat". Le line du contrat de gouvernance se trouve [ici](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract).

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-1.png)

* Sélectionnez « exécuter » et soumettez le « proposalId ».

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-2.png)

* Suivez les étapes ci-dessus (sous _Comment mettre une proposition en file d'attente)_ pour trouver le « proposalId ».
* Entrez « 0 » sous « payableAmount (ether) ».
