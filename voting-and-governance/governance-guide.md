---
description: >-
  Eine schrittweise Übersicht über die Governance-processDRC-Erstellung, die Erstellung von Snapshot-Umfragen, die Erstellung von DIPs, die Abstimmungen über Snapshot-Umfragen, die Abstimmung über einen DIP, das in die Warteschlange-Stellen eines DIPs und die Ausführung eines DIPs.
---

# Governance-Leitfaden

Die dYdX Foundation hat diesen Leitfaden erstellt, um der dYdX-Community zu einem besseren Verständnis der dYdX-Governance-Prozesse zu verhelfen. Der Leitfaden bietet eine schrittweise Übersicht über:

* [Forumsdiskussionen (off-chain)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [DRC-Erstellung (off-chain)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Erstellung von Snapshot-Umfragen (off-chain)](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [Abstimmungen über die Snapshot-Umfrage](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [Erstellung eines DIPs (off-chain)](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [Erstellung eines DIPs (on-chain)](governance-guide.md#step-1-on-chain-dip-drafting)
* [Abstimmungen über einen DIP (on-chain)](governance-guide.md#how-to-vote-on-a-dip)
* [In die Warteschlange-Stellen eines DIPs (on-chain)](governance-guide.md#how-to-queue-a-proposal)
* [Durchführung eines DIPs (on-chain)](governance-guide.md#how-to-execute-a-proposal)

Die beiden im Leitfaden aufgeführten Beispiele sind _DIP 2 (off-chain Vorschlag) – zur Senkung des Schwellenwertes für Liquidity Provider Rewards_ und _DIP 3 (on-chain Vorschlag) – zur Wiederherstellung von Sicherheitsmodulen_.

## DIP 2 (Off-Chain Vorschlag) - Senkung des Schwellenwertes für Liquidity Provider Rewards

_**Zusammenfassung:**_

In der Epoche 6 beschloss die dYdX-Community in einer Abstimmung auf [Snapshot](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43), dass der Schwellenwert des LP-Reward-Volumens für Marktmacher von 1 % auf 0,25 % gesenkt werden sollte. Die Senkung des Schwellenwertes für LP-Prämien von 5 % auf 1 % in Epoche 2 folgte demselben Prozess wie bei der Senkung in Epoche 6 (1 % auf 0,25 %). Die schrittweise Übersicht darüber, wie der Schwellenwert für das LP-Prämien Volumen von 5 % auf 1 % gesenkt wurde, ist im Folgenden eingefügt.

Die Mehrheit der Community (399 Wähler und 86 % der DYDX) beschloss bei der Abstimmung auf [Snapshot](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN), die Volumenschwelle abzusenken, um die Liquiditiy Provider Rewards von 5 % auf 1 % zu setzen. Ein [off-chain DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md) zur Senkung des Schwellenwertes des Liquidity Provider Rewards Volumens für Marktmacher von 5 % auf 1 % wurde von Jacob Goh (jteam0x) von DeFiance Capital eingereicht. Marktmacher, die die Schwelle von 1 % in Epoche 2 erfüllten, waren berechtigt, in Epoche 3 Liquidity-Provider-Prämien zu erhalten. Der Vorschlag erforderte keine Änderungen im on-chain Smart Contract.

_**Hintergrund:**_

Im Rahmen des Liquidity Provider [Rewardprogrammes](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards) werden 1.150.685 $ethDYDX pro Epoche (28 Tage) an Liquidity Provider, die als Marktmacher für das Protokoll fungieren, ausgeschüttet. Die Prämien werden auf der Grundlage einer Formel ausgeschüttet, die eine Kombination aus Uptime, Two-sided Depth, Bid-Ask-Spreads und der Anzahl der unterstützten Märkte belohnt. Um für dieses Prämienprogramm infrage zu kommen, müssen Liquiditätsanbieter in der vorhergehenden Epoche einen Mindestprozentsatz des gesamten Marktmacher-Volumens bereitgestellt haben.

Die dYdX-Community hat "sofortige und unwiderrufliche Kontrolle über" den Schwellenwert der Liquidity Provider Rewards. Die vollständige Liste der Parameter, die unter der Kontrolle der Community stehen, ist [hier](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verlinkt.

Die Community beabsichtigte, den Schwellenwert für Liquiditätsanbieter zu senken, weil auf diese Weise neue Marktmacher und kleine bis mittlere Marktmacher Anreize dazu bekommen würden, die Liquidität auf der dYdX-Plattform zu erhöhen. Darüber hinaus trägt eine zunehmende Anzahl von Marktmachern auf der Plattform dazu bei, dass das dYdX-Protokoll dezentraler wird.

Als Nächstes geben wir einen schrittweisen Überblick darüber, wie die dYdX-Governance in der Praxis funktioniert. Weitere Informationen über Prozesse in der dYdX-Governance finden Sie [hier](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

### **STEP 1 - Forumsdiskussionen, DRC-Erstellung (Off-Chain) und DRC Feedback**

_**Beschreibung:**_

Der dYdX Governance-Prozess wird von [Governance-Foren](https://dydx.forum/) angeheizt. Die Community-Mitglieder posten und kommentieren zu Diskussionsthemen, um off-chain einen groben Konsens zu erreichen. Weitere Informationen über Forumsdiskussionen und zur DRC-Erstellung finden [Sie hier](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).\\ Hinweis - Die Operationen hat [**subDAOhathttps://dydx.forum/**](https://dydx.forum/) als neues Forum gestartet, nachdem die [Community für den Übergang von Commonwealth zu Discourse gestimmt](https://snapshot.org/#/dydxgov.eth/proposal/0xa5e77732dd24edd26bd41b089969b3662c29eb41c3bacd35cb2931ca55882a8f) hat. Einige Verweise in diesem Leitfaden auf frühere Diskussionen in der DRC werden immer noch auf Commonwealth verweisen, aber alle neuen Diskussionen sollten im neu gestarteten [**Diskursforum**](https://dydx.forum/) stattfinden. \


_**Bewerbung auf DIP 2:**_

Su Zhu (zhusu) von Three Arrows Capital hat eine [off-chain Forumsdiskussion](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/) erstellt, um den Schwellenwert für Liquidity-Provider-Prämien zu senken. Verschiedene Community-Mitglieder, wie Evgeny aus Wintermute, Ben aus Kronos, Josh aus Sixtant und viele mehr, nahmen an der Diskussion teil und trugen mit wertvollen Anregungen bei.

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives.png)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives-2.png)

#### _Wie man auf Diskurs posten und kommentieren kann:_

* Registrieren Sie sich mit Ihrem E-Mail-Konto auf Discourse und treten Sie [hier](https://dydx.forum/) der dYdX-Community bei.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 10.59.27 AM.png" alt=""><figcaption></figcaption></figure>

* Wählen Sie einen Thread aus, blättern Sie durch die Kommentare und liken oder antworten Sie auf die Kommentare.
* Erstellen Sie einen neuen Diskussionsfaden oder posten Sie einen DRC, indem Sie auf „**Neues Thema**“ klicken und die Themenkategorie auswählen.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.03.33 AM.png" alt=""><figcaption></figcaption></figure>

* Wenn Sie eine DRC erstellen, folgen Sie bitte der [hier](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) verlinkten Vorlage. Wie unter _DRC-Erstellung_ im [Proposal-Lebenszyklus](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) beschrieben, müssen die DRCs mindestens Folgendes enthalten:
  * Einen kurzen und prägnanten Titel der DRC.
  * Eine kurze und prägnante Beschreibung des Vorschlags.
  * Die Begründung für die DRC (z. B. warum?).
  * Der Titel des Forumsbeitrages muss DRC enthalten: \[Kurztitel der DRC einfügen] (z. B. DRC: Neue Marktanfrage).
  * Eine Community-Umfrage, die Community-Mitglieder als Abstimmungen für Verbesserungen off-chain verwenden können.

### **SCHRITT 2 - DRC-Umfragen auf Snapshot (Off-Chain)**

_**Beschreibung:**_

Nachdem die Community einen groben Konsens erreicht hat, kann ein Community-Mitglied mit 10K-Vorschlagsrechten, eine off-chain-Abstimmung für die DRC auf [Snapshot](https://snapshot.org/#/) erstellen. [Das Vorschlagsrecht](https://docs.dydx.community/dydx-governance/voting-and-governance/voting) ermöglicht die Ausgestaltung und Aufrechterhaltung eines Vorschlags. Snapshot ist eine einfache Abstimmungsschnittstelle, die es den Benutzern ermöglicht, die Stimmung off-chain zum Ausdruck zu bringen. Stimmen auf dem Snapshot werden durch die Anzahl der Governance-Token gewichtet, die von der zur Abstimmung verwendeten Adresse gehalten oder an diese delegiert sind. Das Community-Mitglied, das die Snapshot-Umfrage erstellt, muss Details zur DRC, dem Abstimmungssystem, dem Startdatum der Abstimmung, dem Enddatum der Abstimmung sowie der Snapshot-Blocknummer angeben. Der Abstimmungszeitraum sollte 5 Tage betragen und die Abstimmung sollte nach einer 1-tägigen Abstimmungsverzögerung beginnen (b_asierend auf 13,2 Sekunden Blockzeit)._ Die Abstimmungsverzögerung bietet den dYdX-Community-Mitgliedern Zeit, um mehr über die DRC zu erfahren, $ethDYDXDYDX zu kaufen oder die ihre DYDX-Stimmrechte zu delegieren. Community-Mitglieder, die im Besitz von Governance-Token sind oder denen die Stimmrechte vor der Snapshot-Blocknummer delegiert wurden, sind stimmberechtigt. Weitere Informationen über den Snapshot-Umfragen finden Sie [hier](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) verlinkt.

_**Bewerbung auf DIP 2:**_

Die Community-Mitglieder gaben Feedback zu Su Zhus Beitrag. Folgende Reward-Schwellenwerte wurden von der Community vorgeschlagen:

* [0,5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Su Zhu von Three Arrows Capital,
* [1 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) - Sam von BitTrading,
* [2,5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Ben aus Kronos / WOO Network, und
* [5 %](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - Evgeny aus Wintermute.

Als nächstes hat Su Zhu eine Snapshot-Umfrage mit den folgenden Optionen erstellt:

* MM-Schwellenwert auf 1 % senken
* MM-Schwellenwert auf 2,5 % senken
* MM-Schwellenwert von 5 % beibehalten

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-create-snapshot.png)

#### _Wie man auf einer Snapshot-Umfrage abstimmen kann:_

* Registrieren Sie sich auf Snapshot mit Ihrer Ethereum-Wallet und folgen Sie dYdX Proposals [hier](https://snapshot.org/#/dydxgov.eth).

![https://snapshot.org/#/dydxgov.eth](../.gitbook/assets/2-register-snapshot.png)

* Um in aktiven Snapshot-Umfragen abzustimmen, müssen Sie Governance Tokens halten oder vorher Stimmrechte vor der Snapshot-Blocknummer übertragen bekommen haben, wenn die Snapshot-Umfrage aktiv wird.
* Um abzustimmen, klicken Sie auf den Vorschlag und wählen „Ja“ oder „Nein“ aus, anschließend klicken Sie auf „Abstimmen“.

#### _Wie man eine Umfrage auf Snapshot erstellt:_

* Um eine Snapshot-Umfrage zu erstellen, müssen Sie **mindestens 10K Governance Tokens halten** **und/oder Stimmrechte an diejenige Adresse zugewiesen bekommen haben, die Sie** zur Erstellung des Vorschlages verwenden.
* Der Snapshot-Vorschlag kann aus einer oder mehreren Aktionen bestehen, bis zu maximal 10 Aktionen pro Vorschlag. Aktionen sind in einem Vorschlag spezifizierte Änderungen.
* Wenn Sie die Mindestleistung an Vorschlagsrechten von 10K erfüllen, wählen Sie „**Neuer Vorschlag**“ aus und füllen Sie die offenen Felder gemäß den unten aufgeführten Inhaltsbestimmungen aus.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.08.42 AM.png" alt=""><figcaption><p>dYdX-Snapshot-Seite - Schaltfläche "Neuen Vorschlag erstellen"</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.09.33 AM.png" alt=""><figcaption><p>Fügen Sie hier Details zum Snapshot ein und achten Sie darauf, einen Link zur DRC einzufügen</p></figcaption></figure>

Inhaltsbestimmungen für DRC-Snapshot-Umfragen:

* Details der DRC mit einem Link zur Forumsdiskussion,
* ein Abstimmungssystem,
* Start- und Enddatum der Abstimmung mit einer auf 4 Tage beschränkten Gesamtlänge (_basierend auf 13,2 Sekunden Blockzeit)_ und
* Snapshot-Umfrage wird 1 Tag (\~6570 Blöcke) vor Abstimmungsstart veröffentlicht.

Anforderungen für verbindliche Snapshot-Umfragen:

Für die meisten Entscheidungen wirkt eine Snapshot-Umfrage als Signalisierung, während für ein verbindliches Ergebnis, das in den/die Smart Contract(s) eingreift, eine on-chain-Abstimmung erforderlich ist. Für Entscheidungen, die keinen on-chain Smart Contract-Anruf erfordern, gelten Snapshot-Abstimmungen vor allem für Änderungen der Trading und Liquidity Provider Reward-Formeln als verbindliche und endgültige Abstimmung . Neben den oben genannten Inhaltsbestimmungen müssen Snapshot-Umfragen, welche die Abstimmungen für off-chain kontrollierte Variablen verbindlich machen, Folgendes vorweisen:

* Binäre Abstimmungsoptionen Für die nötige Klarheit stimmt eine Adresse entweder für oder gegen einen Vorschlag.

![](../.gitbook/assets/2-snapshot-binary-voting.png)

* Nach der Abstimmung werden die zugehörigen Informationen auf IPFS gespeichert und es wird automatisch ein Bericht generiert und zum Download bereitgestellt.

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-snapshot-ipfs.png)

### **SCHRITT 3 - DIP-Erstellung (Off-Chain-Vorschlag)**

_**Beschreibung**:_

Ein DIP muss erstellt werden, wenn (1) eine Snapshot-Umfrage dazu führt, dass ein off-chain-Parameter (wie Änderungen an den Trading-Prämie- oder LP Reward-Formeln) aktualisiert wird und (2) wenn ein Community-Mitglied einen Vorschlag zur Änderung von on-chain Smart Contracts einreichen möchte. Für Abstimmungen, die keine on-chain Smart Contract Updates erfordern, muss das Ergebnis der Snapshot-Umfrage in einen off-chain DIP umformuliert und über ein Pull Request an den Pending-DIP-Zweig im Github der dYdX Foundation eingereicht werden. Der DIP sollte den Mehrheitsbeschluss auf Snapshot widerspiegeln. Der DIP muss die in der [hier](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) verlinkten Vorlage enthaltenen Informationen spezifisch angeben.

_**Bewerbung auf DIP 2:**_

In diesem Fall wurde der [DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md) von @Jteamdc verfasst.

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](../.gitbook/assets/2-dip-example.png)

Als der Vorschlagsentwurf für den DIP 2 abgeschlossen wurde, hat @Jteamdc eine \*\*\*\* [Pull Request](https://github.com/dydxfoundation/dip/pull/8) aus dem Arbeitszweig gegen den Pending-DIP-Zweig der dYdX Foundation erstellt. Nachdem die dYdX Foundation den Vorschlag überprüft und gegengezeichnet hatte, wurden die Änderungen aus den Pending-DIPs in den Hauptzweig eingearbeitet.

![https://github.com/dydxfoundation/dip/pulls](../.gitbook/assets/2-dip-pending-merge.png)

Da das Herabsenken des Schwellenwertes für Liquidity Provider Rewards keine Änderungen im on-chain Smart Contract erfordert, ist der Prozess nun abgeschlossen und die Änderungen werden in der nächsten Epoche wirksam.

#### _Wie man einen DIP erstellt:_

* Der DIP sollte sich auf einen im Rahmen der off-chain Abstimmung auf Snapshot beschlossenen Mehrheitsbeschluss in der off-chain beziehen und kann aus einer oder mehreren Aktionen bestehen, bis zu maximal 10 Aktionen pro Vorschlag. Aktionen sind in einem Vorschlag spezifizierte Änderungen. Weitere Informationen finden Sie unter [DIP-Erstellung](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution).
* Registrieren Sie sich für einen Github-Account: [https://github.com/signup](https://github.com/signup).
* Gehen Sie auf die [hier](https://github.com/dydxfoundation/dip) verlinkte dYdX Repo-Seite und setzen Sie die Fork bei der Repo unter Ihrem Github-Account ein.

![https://github.com/dydxfoundation/dip](../.gitbook/assets/2-dip-create-1.png)

* In der mit der Fork versehenen DIP-Repo, gehen Sie in das Verzeichnis, das den Inhalt der DIPs enthält: [https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips).

![](../.gitbook/assets/2-dip-create-2.png)

* Wählen Sie den dips folder aus: [https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content).

![](../.gitbook/assets/2-dip-create-3.png)

Der dips folder enthält ein Verzeichnis von früheren Vorschlägen, die der [hier](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) verlinkten DIP-Vorlage folgen.

![https://github.com/dydxfoundation/dip/tree/master/content/dips](../.gitbook/assets/2-dip-create-4.png)

* Bevor Sie einen Vorschlag erstellen, stellen Sie bitte sicher, dass der von Ihnen mit einer Fork versehene Zweig mit der letzten aktualisierten Version des Hauptzweiges übereinstimmt. Wenn Sie eine veraltete Version der DIP-Repo verwenden, bestätigen Sie bitte, dass Ihre mit der Fork versehene Version mit den neuesten Änderungen übereinstimmt. Wenn Sie Unterstützung benötigen, um Ihre mit der Fork versehene Version neu zu erstellen, können Sie diesen Schritten hier folgen: [https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master).
* Bearbeiten Sie die [DIP-Vorlage](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) mit den Informationen für Ihren Vorschlag. Wenn Sie die DIP-Repo nicht mit einer Fork versehen haben, wird die Auswahl des „Bearbeiten"-Symbols die Repo automatisch vom Hauptzweig aus mit einer Fork versehen, weil Sie kein Administrator sind.

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](../.gitbook/assets/2-dip-create-5.png)

* Folgen Sie der [Vorlage](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) und fügen Sie Ihren DIP in Ihre Fork des Repository im `content/dips/`-Verzeichnis hinzu. Bitte folgen Sie den unten aufgeführten Bestimmungen zur Bezeichnung von DIPs-Status.

![](../.gitbook/assets/2-dip-create-6.png)

DIP Status:

* WIP - ein DIP, der noch in der Entwicklung steht.
* Vorgeschlagen - ein DIP, der bereit ist, on-chain vorgeschlagen zu werden.
* Zugelassen - ein DIP, der von der dYdX-Community für die Umsetzung akzeptiert wurde.
* Implementiert - ein DIP, der im Hauptnetz veröffentlicht wurde.
* Abgelehnt - ein DIP, der abgelehnt wurde.
* Nachdem Sie den gesamten Inhalt auf Korrektheit geprüft haben, erstellen Sie einen Pull Request aus Ihrem Arbeitszweig in den Pending-DIPs-Zweig der dYdX Foundation hinein. Bitte reichen Sie diesen Pull Request **nicht** in den Hauptzweig der dYdX Foundation hinein, weil der IPFS-Auftrag fehlschlagen wird, wenn externe Parteien Informationen mit dem Hauptzweig zusammenführen möchten. Bitte verwenden Sie die [hier](https://github.com/dydxfoundation/dip/pull/8) verlinkten Pull Request als Beispiel.

![](../.gitbook/assets/2-dip-status-1.png)

* Nach der Durchsicht wird die dYdX Foundation die Änderungen aus dem Pending-DIPs-Zweig in den Hauptzweig einarbeiten.

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/2-dip-status-2.png)

* Vor **dem Zusammenführen** wird automatisch ein Auftrag zum Hochladen des DIP auf IPFS ausgeführt. Sie können den Upload des DIP auf IPFS hier nachverfolgen: [https://github.com/dydxfoundation/dip/pull/9/checks](https://github.com/dydxfoundation/dip/pull/9/checks).
* Der DIP wird unter [**`dip`**](https://github.com/dydxfoundation/dip)`/`[`content`](https://github.com/dydxfoundation/dip/tree/master/content)`/`**`dips`**`/` hinzugefügt.

![](../.gitbook/assets/2-dip-status-3.png)

Da der Vorschlag keine Änderungen im on-chain Smart Contract erfordert, ist der Prozess jetzt abgeschlossen und die Änderungen werden in der nächsten Epoche wirksam

## DIP 3 (On-Chain Vorschlag) - Wiederherstellung von Sicherheitsmodulen

_**Zusammenfassung:**_

Am 1. November wurde ein on-chain [DIP](https://dydx.community/dashboard/proposal/3) von Dan Robinson von Paradigm erstellt, um die Funktionalität des Safety Module Staking Pools wiederherzustellen. Die Mehrheit der Community (251 Wähler und fast 142 Mio. ethDYDX) stimmte für die Wiederherstellung der Funktionalität des Sicherheitsmoduls. Nach einem 10-tägigen Abstimmungszeitraum dauerte es fast 3 Tage, bis ein Community-Mitglied die Warteschlange aufrufen und den Vorschlag in die 7-Tage-lange Timelock-Verzögerung verschieben konnte. Am 20. November wurde das Sicherheitsmodul wiederhergestellt und in einen sauberen Zustand zurückgesetzt.

_**Hintergrund:**_

Das dYdX Safety Module ist ein Staking Contract um einen dezentralen Pool mit Geldern zu betanken, die dem dYdX Protokoll Rückhalt bieten sollen. Benutzer staken $ethDYDX in den Sicherheitspool und erhalten $stkDYDX (1:1). $stkDYDX ist eine tokenisierte Position, die als ERC-20 übertragen wird, die die gleichen Stimm- und Vorschlagsrechte hat wie $ethDYDX. Im Falle einer Unterdeckung erfordert es eine Governance-Abstimmung, um zum Zwecke der Verlustminderung gestakte $ethDYDX zu beschlagnahmen. Aus der $ethDYDX Token-Versorgung werden 2,5 % (25.000.000 $ethDYDX) der Token-Versorgung an diejenigen Benutzer verteilt, die ethDYDX im Safety Pool ins Staking geben. Weitere Informationen über den Safety Staking Pool finden Sie [hier](https://dydx.foundation/blog/en/safety-staking).

Im Rahmen der [Safety-Staking-Pool-Prämien](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool), werden 383.562 $ethDYDX pro Epoche (28 Tage) an die Staker ausgeschüttet werden. Prämien werden im Sekundentakt anteilsmäßig an die Staker ausgeschüttet.

Die dYdX-Community hat „sofortige und unwiderrufliche Kontrolle über" die Parameter des Sicherheitsmodul-Smart Contracts. Die vollständige Liste der Parameter, die unter der Kontrolle der Community stehen, ist [hier](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verlinkt.

Am 8. September um 15:00 UTC wurde die Transferbeschränkung für $ethDYDX-Token aufgehoben und effektiv das Staking für das dYdX-Sicherheitsmodul eröffnet. Über 50 verschiedene Adressen stakten ungefähr 157K ethDYDX innerhalb fast 1 Stunde. Ein Bug verursachte einen Fehler im Bereitstellungsprozess und keine stkDYDX wurde an die Adressen ausgestellt, die im Sicherheitsmodul gestakt hatten. Als Ergebnis bleiben die Gelder eines jeden Stakers im Vertrag  und das dYdX Team deaktivierte das Staking auf der dYdX-Governance UI.

[DIP 1](https://dydx.community/dashboard/proposal/0) schlug vor, die Funktionalität im Sicherheitsmodul wiederherzustellen und den betroffenen Adressen zu gestatten, ihre Gelder zurückzugewinnen und ihnen zusätzliche 10 % ihrer gestakten Token als Entschädigung zu vergüten. Während die Stimmung in der Community stark zu [DIP 1 Sicherheitsmodul-Wiederherstellung und Staker-Wiedergutmachung](https://dydx.community/dashboard/proposal/0) tendierte, schlug der Vorschlag fehl, weil er nicht das 100M-$ethDYDX-Minimum-Quorum erfüllte, das erforderlich ist, um einen Long Timelock-Beschluss abzusegnen. Infolgedessen erstellte Jacob Goh (jteam0x) von DeFiance Capital [DIP 4 Rückerstattung und Entschädigung von Stakern des Sicherheitsmoduls](https://dydx.community/dashboard/proposal/2), um den betroffenen Adressen ihre verpassten Prämien zurückzuerstatten und die Unannehmlichkeiten wiedergutzumachen. [DIP 4](https://dydx.community/dashboard/proposal/2) umfasste die Anwendung des Wiederherstellungs-Contracts für die von den Benutzern gestakten Token und Ausgleichszahlungen von zusätzlichen 10 % aus der Prämien-Treasury an betroffene Adressen. Der DIP wurde von den weniger strengen Governance-Parametern eines Short Timelocks geregelt.

Der DIP-Lebenszyklus wird im Allgemeinen so lange aufrechterhalten, bis der DIP erstellt ist. Der wesentliche Unterschied zwischen DIP 3 (On-chain) und DIP 2 (Off-chain) bestand darin, dass DIP 3-Vorschläge On-chain Abstimmungen und den Einsatz eines Smart Contracts voraussetzen. Da der Prozess für Forumsdiskussionen, die DRC-Erstellung und die DIP-Entwurfserstellung gleich sind, starten wir unsere schrittweise Erörterung mit den Inhaltsanforderungen für den Entwurf von on-chain DIPs. Für weitere Informationen folgen Sie bitte den folgenden Links:

* dYdX-Governance-Prozess - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
* Sicherheitsmoduls-Vorfallbericht - [https://dydx.foundation/blog/de/outage-1](https://dydx.foundation/blog/en/outage-1).
* Off-Chain Forumsdiskussion **-** [https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause).
* Off-Chain DRC **-** [https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* Off-Chain DRC Snapshot-Umfragen **-** [https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* DIP auf Github vorgeschlagen **-** [https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **SCHRITT 1 - On-Chain DIP-Entwurfserstellung**

_**Beschreibung:**_

Der Entwurf eines on-chain DIPs, der den Governance-Konsens auf dem dYdX-Protokoll betrifft, muss die spezifischen Schritte für die Umsetzung von Änderungen am Smart Contract erläutern. Nachdem die Community von Snapshot zu einem groben Konsens gelangt ist, oder nachdem ein DIP zuvor fehlgeschlagen war, kann ein Community-Mitglied mit ausreichend Vorschlagsrechten den neuen DIP On-chain einreichen. Weitere Informationen über den Schwellenwert für Vorschlagsrechte, den Timelock Executor und andere Governance-Parameter sind [hier](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verlinkt.

_**Bewerbung auf DIP 3:**_

In diesem Fall wurde der [DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md) von Dan Robinson von Paradigm verfasst. Da der Vorschlag Änderungen im on-chain Smart Contract enthielt, verfügte der Vorschlag über einen Link zu den spezifischen Implementierungen im Smart Contract.

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/2-dip3-example-1.png)

Wenn Sie von dem SafetyModuleV2.sol deployment Contract aus zum Safety folder navigieren, wird die README angezeigt, welche die spezifischen Details darüber enthält, wie der Vorschlag umgesetzt wird.

![](../.gitbook/assets/2-dip3-example-1a.png)

Die Schritte zur Umsetzung des in der README enthaltenen Vorschlags sind hier verlinkt: [https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety).

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-2.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-3.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-4.png)

#### _Wie man einen On-Chain DIP (WIP) entwirft:_

* Erstellen Sie eine neue Wallet, um den DIP zu erstellen. Der Bereitstellungsprozess erfordert die Eingabe Ihrer Seed Phrase als eine Umgebungsvariable, weshalb wir empfehlen, eine einmalige Wallet für die on-chain DIP-Erstellung zu verwenden.
* Delegieren Sie für die DIP-Erstellung ausreichend Vorschlagsrechte zu der one-off Wallet. Sie können die Vorschlagsrechte [hier](https://dydx.community/dashboard) delegieren. Die unterschiedlichen Schwellenwerte für Vorschlagsrechte sind unten enthalten und [hier](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verlinkt.
  * Short Timelock: 0,5 % der Gesamtversorgung (5 Mio. in Vorschlagsrechten).
  * Starkware Executor: 0,5 % der Gesamtversorgung (5 Mio. in Vorschlagsrechten).
  * Long Timelock Executor: 2,0 % der Gesamtversorgung (20 Mio. in Vorschlagsrechten).
  * Merkle Pauser Executor: 0,5 % der Gesamtversorgung (5 Mio. in Vorschlagsrechten).
* Erstellen Sie einen Alchemy Key. Mit dem Alchemy Key müssen Sie keinen Ethereum Node laufen lassen, um mit Ethereum zu interagieren und den Smart Contract anzuwenden. Der Leitfaden für die Erstellung eines Alchemy Key ist [hier](https://docs.alchemy.com/alchemy/introduction/getting-started) verlinkt.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-1.png)

Wählen Sie Ethereum und „Starten".

![](../.gitbook/assets/2-draft-dip-example-2.png)

Füllen Sie die erforderlichen Informationen aus, wählen Sie das Goerli Network und wählen Sie "App erstellen".

<figure><img src="../.gitbook/assets/2-draft-dip-example-3.png" alt=""><figcaption></figcaption></figure>

Nachdem Sie Ihr Konto erstellt haben, folgen Sie den [hier](https://docs.alchemy.com/alchemy/introduction/getting-started) verlinkten Setup-Anweisungen.

Unter „4". Starten Sie den Aufbau, wählen Sie „Versuchen, Ihren ersten Smart Contract anzuwenden" und folgen Sie dem Leitfaden.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-4.png)

* Öffnen Sie die Windows-Kommandozeile, die default Terminal App oder laden Sie den iTerm: [https://iterm2.com/](https://iterm2.com/) herunter.
* Laden Sie Node.js und npm herunter und installieren Sie beide, wenn sie dies noch nicht getan haben: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Hardhat ist ein Entwicklungstool, um Ethereum Software zusammenzustellen und zu testen. Installieren Sie Hardhat, wenn Sie dies noch nicht getan haben: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Entwerfen Sie Ihre vorgeschlagene(n) Smart Contract Ausführung(en).
* Der IPFS-Hash wird automatisch generiert und kann [hier](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips) abgerufen werden. Der IPFS-Hash wird im Verzeichnis der dYdX Foundation unter dem Dateinamen `DIP-[New DIP #]-ipfs-hashes.json` stehen.

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](../.gitbook/assets/2-draft-dip-example-5.png)

* Nachdem Sie die neue Datei ausgewählt haben (`DIP-[New DIP #]-ipfs-hashes.jso`), vergewissern Sie sich, dass die den encodedHash verwenden.

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](../.gitbook/assets/2-draft-dip-example-6.png)

### **SCHRITT 2 - Reichen Sie einen On-chain DIP ein**

_**Beschreibung:**_

Nachdem ein Community-Mitglied bestätigt hat, dass die vorgeschlagene(n) Smart Contract-Ausführung(en) korrekt ist/sind, und der DIP abgeschlossen ist, kann der DIP On-Chain eingereicht werden. Wenn ein on-chain DIP erstellt wird, tritt der Vorschlag zugunsten der Abstimmungsverzögerung in einen „Pending"-Zustand, der ungefähr 1 Tag (ungefähr 6570 Blöcke) dauert. Die Snapshots der Benutzer werden nach der Abstimmungsverzögerung aufgezeichnet, um $ethDYDX-Bestände und die delegierten Abstimmungsrechte nachzuweisen. Im nächsten Schritt tritt der Vorschlag in einen „Aktiven" Zustand; die Abstimmungsdauer variiert zwischen 2 und 10 Tagen je nach Vorschlagstyp. Damit ein Vorschlag umgesetzt wird, muss die Abstimmung das Mindestquorum und die minimale Stimmendifferenz überschreiten, die je nach Vorschlagstyp anders ausfällt. Wenn der DIP das Mindestquorum, die minimale Stimmendifferenz und die Mehrheit der abstimmenden Community-Mitglieder zugunsten des DIP erreicht, kann jede beliebige Adresse den Vorschlag aus der Warteschlange abrufen, um in die Timelock-Warteschlange verschoben zu werden. Die Timelock Contracts können Transaktionen, über die von der dYdX Community abgestimmt wurde, in die Warteschlange stellen, sie stornieren oder durchführen. Die Länge der Timelock Warteschlange variiert je nach Vorschlagstyp.

_**Bewerbung auf DIP 3:**_

Das Paradigm-Team hat den Solidity-Code für das `SafetyModuleV2.sol.` fertiggestellt.

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/2-draft-dip-example-7.png)

Das Paradigm-Team simulierte die Updates sowohl in einer lokalen als auch in einer mit einer Forked versehenen Mainnet-Umgebung. Die Testsuite wurde dann abgespielt, um sicherzustellen, dass die volle Funktionalität wiederhergestellt würde und folgte dabei der Ausführung des Governance-Vorschlages auf dem Mainnet.

Das Paradigm-Team wandte die Smart Contract Updates durch das Abspielen der unten aufgeführten Skripte an.

**Sicherheitsmodul-Wiederherstellung**

`export ALCHEMY_KEY=<... >`

`export MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-recovery`\ `--dydx-Token-Adresse 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\ `--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\ `--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**Governance-Vorschlag: Sicherheitsmodul-Reparatur**

`export ALCHEMY_KEY=<... >`

`export MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\ `--proposal-ipfs-hash-hex 0x...`\ `--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\ `--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\ `--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\ `--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\ `--safety-module-new-impl-address 0x...`

**Governance-Vorschlag: Sicherheitsmodul-Entschädigung**

`export ALCHEMY_KEY=<... >`

`export MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\ `--proposal-ipfs-hash-hex 0x...`\ `--dydx-Token-Adresse 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\ `--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\ `--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\ `--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\ `--safety-module-recovery-address 0x...`

Der DIP wurde zeitgleich auf [https://dydx.community/dashboard](https://dydx.community/dashboard) veröffentlicht.

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-8.png)

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-9.png)

Der dYdX-Governance-Contract ist 0x7e9b1672616ff6d6629ef2879419aae79a9018d2: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).

Die DIP-Bereitstellung kann auf Etherscan bestätigt werden: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

Der DIP wurde am 1. November 2021 im Block 13532376 erstellt. Liegt der DIP 6570 Blöcke in der Zukunft, gilt er als „Pending".

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-10.png)

ethDYDX-Inhaber konnten über den DIP abstimmen, als er im Block 13538946 in einen „Aktiven" Zustand überging.

Die erste Abstimmung wurde am 2. November 2021 um 17:51:22 UTC (Block 13538959) abgehalten, 6583 Blöcke nach der Erstellung des On-Chain-DIPs.

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/2-draft-dip-example-11.png)

Nach der 10-tägigen Abstimmungsperiode, die an einen Long Timelock gekoppelt ist, kann eines der Community-Mitglieder die Warteschlange aufrufen und den Vorschlag in die 7-Tage-Timelock-Verzögerung verschieben. Bei DIP 3 dauerte es fast 3 Tage, bis ein Community-Mitglied die Warteschlange aufrief.

![https://etherscan.io/tx/0x3402372aa549d2270a6b5d4f84884ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/2-draft-dip-example-12.png)

Nach der 7-tägigen Timelock-Verzögerung wurde der DIP on-chain ausgeführt.

![https://etherscan.io/tx/0xfd332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/2-draft-dip-example-13.png)

In dem Moment, als der DIP on-chain ausgeführt wurde, wurde der DIP-Status unter [https://dydx.community/dashboard/proposal/3](https://dydx.community/dashboard/proposal/3) auf „Ausgeführt“ aktualisiert.

![](../.gitbook/assets/2-draft-dip-example-14.png)

Beachten Sie, dass (1) Vorschläge innerhalb der 7-tägigen Execution-Karenzzeit, welche unmittelbar nach der Timelock-Verzögerung beginnt, ausgeführt werden müssen und dass (2) die vorschlagende Adresse den Mindestbetrag an Vorschlagsrechten, der durch den jeweiligen Timelock-Vertrag erforderlich ist, beibehalten muss, bis der DIP ausgeführt worden ist (entweder 5 Mio. oder 20 Mio. in Vorschlagsrechten).

#### _Wie man einen DIP On-Chain einreicht:_

* Stellen Sie sicher, dass Sie genügend Vorschlagsrechte haben, um den DIP zu erstellen. Weitere Informationen finden Sie unter [DIP-Erstellung](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
  * Short Timelock Executor: 0,5 % der Gesamtversorgung (5 Mio. in Vorschlagsrechten).
  * Starkware Executor: 0,5 % der Gesamtversorgung (5 Mio. in Vorschlagsrechten).
  * Long Timelock Executor: 2,0 % der Gesamtversorgung (20 Mio. in Vorschlagsrechten).
  * Merkle Pauser Executor: 0,5 % der Gesamtversorgung (5 Mio. in Vorschlagsrechten).
* Stellen Sie sicher, dass Sie ETH in Ihrer Wallet besitzen, um die Gasgebühren zu bezahlen.
* Erstellen Sie eine App auf Alchemy für das Ethereum Mainnet Netzwerk.

![https://dashboard.alchemyapi.io/](../.gitbook/assets/2-draft-dip-example-15.png)

* Nachdem die App erstellt wurde, klicken Sie auf „Key anzeigen", um Ihren Alchemy Key (7LOaQtguSm2kSEcFXQH88B) zu erhalten: [https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul).

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](../.gitbook/assets/2-draft-dip-example-16.png)

* Laden Sie Node.js und npm herunter und installieren Sie sie: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Installieren Sie Hardhat: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Lassen Sie das Skript durchlaufen, welches Sie entworfen haben.
* Überprüfen Sie den Governance Contract, um nachzusehen, ob der Vorschlag On-Chain erstellt wurde: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).
* Auf der Adresse, die den Vorschlag eingereicht hat, müssen Sie den Mindestbetrag an Vorschlagsrechten, die durch den jeweiligen Timelock-Vertrag erforderlich sind, beibehalten, bis der Vorschlag ausgeführt worden ist.

#### _Wie man über einen DIP abstimmt:_

* Stellen Sie sicher, dass Sie ETH in Ihrer Wallet besitzen, um die Gasgebühren zu bezahlen.
* Sie können über einen Active DIP abstimmen, indem Sie den DIP auf [https://dydx.community/dashboard](https://dydx.community/dashboard) auswählen.

![](../.gitbook/assets/2-draft-dip-example-17.png)

Die Abstimmungsdauer hängt von der Art des Vorschlags ab. Weitere Informationen finden Sie unter [DIP-Erstellung](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).

* Short Timelock Executor: 4 Tage.
* Starkware Executor: 4 Tage.
* Long Timelock Executor: 10 Tage.
* Merkle Pauser Executor: 2 Tage.

#### _Wie man einen Vorschlag in die Warteschlange stellt:_

Ein erfolgreicher Vorschlag kann in die Warteschlange gestellt werden, um die Timelock-Verzögerung zu starten.

* Stellen Sie sicher, dass Sie eine kompatible Wallet verwenden, die Eths enthält.
* Gehen Sie zum „Contract"-Symbol auf Etherscan und klicken Sie auf „Write Contract". Der Governance-Contract ist [hier](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract) verknüpft.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-queue-1.png)

* Wählen Sie die Warteschlange aus und reichen Sie die „proposalId" ein.

![](../.gitbook/assets/2-draft-dip-example-queue-2.png)

Die „proposalId“ kann auf Etherscan gefunden werden, wenn der DIP erstellt wurde: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

* Wählen Sie „Click to see more.”.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-3.png)

* Wählen Sie „Decode Input Data" aus.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-4.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-5.png)

#### _Wie man einen Vorschlag ausführt:_

Nach der Timelock-Verzögerung kann ein erfolgreicher Vorschlag ausgeführt werden.

* Gehen Sie zum „Contract"-Symbol auf Etherscan und klicken Sie auf „Write Contract". Der Governance-Contract ist [hier](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract) verknüpft.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-1.png)

* Wählen Sie “Execute“ und reichen Sie die “proposalId“ ein.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-2.png)

* Folgen Sie den obigen Schritten (unter _Wie man einen Vorschlag in die Warteschlange setzt)_, um die „proposalId" zu finden.
* Geben Sie „0" unter „payableAmount (ether)" ein.
