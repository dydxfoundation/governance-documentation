---
description: Überblick über den Lebenszyklus des dYdX-Verbesserungsvorschlags (DIP).
---

# Vorschlagslebenszyklus

## **Vorschlagsstufen**

Der dYdX-Governance-Prozess wird durch Governance-Foren unter [**forums.dydx.community**](https://forums.dydx.community/) vorangetrieben und durch dYdX-Verbesserungsvorschläge („DIPs“) ratifiziert.

Im Folgenden skizzieren wir einen vorläufigen Entwurf, der erläutert, wie der dYdX-Governance-Prozess ablaufen wird, von der Einführung und Definition des Konzepts bis zur tatsächlichen Implementierung. Diese Prozesse können sich je nach Feedback der DYDX-Gemeinschaft ändern.

Das folgende Flussdiagramm zeigt die ersten vorgeschlagenen Stufen, um einen Vorschlag zu verabschieden:

![Stufen eines DIP](../.gitbook/assets/1-proposal-stage-flow-chart.png)

## 0. Forendiskussion

Jeder kann sich anmelden und einen Thread zu jedem Thema in den Governance-Foren von dYdX erstellen, die unter [**forums.dydx.community**](https://forums.dydx.community/) gehostet werden. Gemeinschafts-Mitglieder müssen sich mit einer E-Mail-Adresse oder einem Ethereum-Wallet registrieren.

## 1. (Off-chain) DRC-Erstellung

Die Off-Chain-Erstellung von **dYdX Request for Comments** (DRCs) ist der erste Schritt im Governance-Verbesserungsprozess. Jeder kann am Governance-Forum teilnehmen, Off-Chain-DRCs erstellen und Verbesserungen diskutieren.

Um eine DRC zu erstellen, verwenden Sie [diese Vorlage](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) (verfügbar auf unserem Github). Die DRC sollte alle Informationen des möglicherweise endgültigen DIP abdecken.

DRCs müssen mindestens Folgendes enthalten:

* Kurze und prägnante Titel der DRC
* Eine kurze und prägnante Beschreibung des Vorschlags
* Die Begründung für die DRC, z. B. warum?
* Der Titel des Forenbeitrags muss DRC: mit dem Kurztitel der DRC enthalten. Z. B. DRC: Neue Marktanfrage
* Eine Gemeinschafts-Umfrage, welche die Gemeinschafts-Mitglieder dazu verwenden können, über Verbesserungen off-chain abzustimmen

## 2. DRC Diskussion & Feedback

Nach der Veröffentlichung im Governance-Forum sollten alle Fragen und Kommentare angesprochen und berücksichtigt werden, um das DRC weiter zu verbessern.

## 3. DRC-Schnappschuss-Umfrage

Snapshot-Umfragen dienen zwei Zwecken: Stimmungssignalisierung für zukünftige On-Chain-DIPs und bindende Stimmen für Variablen, die außerhalb der Kette kontrolliert werden.

Sobald ein Off-Chain-DRC einen sehr groben Konsens hat, kann ein Community-Mitglied mit mehr als `10.000` DYDX-Vorschlagsmacht eine Off-**Chain**-Abstimmung für den DRC auf **Snapshot** erstellen. Wir ermutigen die dYdX-Gemeinschaft, montags Snapshot-Umfragen zu erstellen, um die Sichtbarkeit während der regulären Arbeitswoche zu erhöhen.

Snapshot ist eine einfache Abstimmungsschnittstelle, die es den Benutzern ermöglicht, die Stimmung off-chain zum Ausdruck zu bringen. Stimmen auf Snapshot werden nach Anzahl der Stimmrechte der jeweiligen Adresse gewichtet, von welcher aus abgestimmt wurde.

Für Snapshot-Umfragen im Zusammenhang mit Stimmungssignalen muss der Vorschlagende Folgendes bereitstellen:

* Details der DRC,
* ein Abstimmungssystem,
* eine Abstimmungsperiode – Start- und Enddatum der Abstimmung, sind auf eine Abstimmungsperiode von 4 Tagen ausgelegt, und
* eine Abstimmungsverzögerung - eine Snapshot-Blocknummer, die 6570 Blöcke (ungefähr 1 Tag) in der Zukunft liegt. Die Snapshot-Blocknummer sperrt den Status der Gemeinschafts-Mitglieder, die abstimmen können. Token-Inhaber, die Token vor der Snapshot-Blocknummer halten, sind stimmberechtigt. Vor dem Snapshot der jeweiligen Stimmrechte jeder Adresse gibt die Stimmverzögerung den DYDX/stkDYDY-Inhabern Zeit, Token zu erwerben, Stimmrechte zu delegieren und Token zwischen Wallets zu verschieben (das Verschieben von Token zwischen Wallets gilt nur für DYDX-Inhaber).

Für Entscheidungen, die keinen on-chain Smart Contract-Anruf erfordern, gelten Snapshot-Abstimmungen vor allem für Änderungen der Trading und Liquidity Provider Prämien-Formeln als verbindliche und endgültige Abstimmung. Der Vorschlagende muss die oben genannten Anforderungen erfüllen und Folgendes bereitstellen:

* binäre Abstimmungsoptionen - zur Verdeutlichung stimmt eine Adresse entweder für oder gegen einen Vorschlag.

Die vorgeschlagene(n) Änderung(en) wird/werden von dYdX Trading Inc. implementiert, wenn die Ergebnisse der Snapshot-Umfrage Folgendes erfüllen:

* das Mindestquorum - mindestens 1M DYDX/stkDYDX. Das Mindestquorum trägt zur Dezentralisierung der Entscheidungsfindung bei und schützt vor einseitiger Entscheidungsfindung und
* die Mindeststimmendifferenz - mindestens 67 % der Stimmen müssen für den Vorschlag ausfallen. Die Mindeststimmen-Differenz hilft beim Herausfiltern von Vorschlägen, die äußerst umstritten sind und weiterer Diskussion bedürfen.

dYdX Trading Inc. hat bis zu 1 Epoche (28 Tage), eine Nachfrist für die Ausführung, um Änderungen aus einer erfolgreichen Snapshot-Umfrage zu implementieren.

Beachten Sie, dass Vorschläge und Abstimmungen nur signierte Nachrichten sind, die auf IPFS gespeichert und über das Commonwealth-Portal verfügbar sind.

## 4. (On-chain) DIP-Erstellung

Wenn ein grober Konsens erzielt wird, kann ein On-Chain-DIP von einem Gemeinschafts-Mitglied eingereicht werden, das über genügend Vorschlagskraft für die Art des Vorschlags verfügt. Ein On-Chain-DIP wird über einen Smart-Vertrag-Aufruf initiiert. Der Vorschlag sollte auf dem Siegerergebnis der Off-Chain-DIP-Abstimmung auf Snapshot basieren und kann aus einer oder mehreren Aktionen bestehen, bis zu maximal 10 Aktionen pro Vorschlag.

Eine DIP-Erstellung unterliegt einer Mindestanzahl von Token, die für ein Konto gehalten/delegiert werden müssen. Beim Erstellen eines Vorschlags muss ein Timelock-Executor angegeben werden. Die ursprünglichen Parameter sind wie folgt (und können durch Governance geändert werden:

| Parameter | Beschreibung | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| ------------------ | ------------------------------------------------ | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Vorschlagsschwelle | Mindestens gehaltene/delegierte Token zum Erstellen von Vorschlägen | 0,5 % der Gesamtversorgung | 0,5 % der Gesamtversorgung | 2 % der Gesamtversorgung | 0,5 % der Gesamtversorgung |

## 5. (On-chain) DIP-Abstimmung

Nachdem ein On-Chain-DIP erstellt wurde, wechselt das Angebot für einen Zeitraum, der durch die **Abstimmungsverzögerung** definiert ist, in einen `schwebenden` Zustand, der derzeit auf `6570` Blöcke oder ungefähr 1 Tag (unter der Annahme von 13 Sekunden pro Block) konfiguriert ist. Mit anderen Worten, Benutzer-Snapshots werden 1 Tag nach Erstellung des DIP aufgezeichnet, an welchem Punkt das Angebot in einen `aktiven` Zustand übergeht.

Nach der Abstimmungsverzögerung wird die Abstimmungsperiode aktiviert. Die Länge des Abstimmungszeitraums hängt von der Art des Vorschlags ab.

Das folgende Diagramm zeigt ein DIP-Status-Flussdiagramm:

![Lebenszyklus eines DIP](../.gitbook/assets/1-proposal-state-flowchart.png)

Nachdem ein DIP in der Kette erstellt wurde, unterliegt er einer **Abstimmungsverzögerung**, einem **Abstimmungszeitraum**, einem **Mindestquorum** und einer **Mindeststimmendifferenz**. Die ursprünglichen Parameter sind wie folgt:

| Parameter | Beschreibung | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| ----------------- | ----------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Abstimmungsverzögerung | Anzahl der zu wartenden Ethereum-Blöcke, bevor die Abstimmung über einen Vorschlag beginnen kann, nachdem ein Vorschlag eingereicht wurde | 6.570 Blöcke | 6.570 Blöcke | 6.570 Blöcke | 6.570 Blöcke |
| Abstimmungszeitraum | Zeitraum, für den Vorschläge zur Abstimmung zur Verfügung stehen | 4 Tage | 2 Tage | 10 Tage | 4 Tage |
| Mindestquorum | Minimale Ja-Stimmen für die Annahme eines DIP-Vorschlags | 2 % der Gesamtversorgung | 1 % der Gesamtversorgung | 10 % der Gesamtversorgung | 2 % der Gesamtversorgung |
| Stimmendifferenz | Erforderliche Ja-Nein-Lücke, damit ein DIP-Vorschlag angenommen wird | 0,5 % der Gesamtversorgung | 0,5 % der Gesamtversorgung | 10 % der Gesamtversorgung | 0,5 % der Gesamtversorgung |

Nur die Abstimmungsverzögerung kann durch Governance geändert werden, und sie kann nur auf Werte zwischen (einschließlich) der minimalen und maximalen Verzögerung geändert werden. Der Abstimmungszeitraum, das Mindestquorum und die Stimmendifferenz können nicht geändert werden.

## 6. Vorschlagswarteschlange und -ausführung

Nachdem ein DIP bestanden wurde, kann jede Adresse die Warteschlangen-Methode aufrufen, um den Vorschlag in die Timelock-Warteschlange zu verschieben. Ein DIP kann nur in die Warteschlange gestellt werden, wenn es bestanden wurde.

| Parameter | Beschreibung | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| ---------------------- | ------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Timelock-Verzögerung | Nachdem ein Vorschlag bestanden und in die Warteschlange gestellt wurde, wird die Ausführung des Vorschlags verzögert | 2 Tage | 0 Tage | 7 Tage | 2-9 Tage |
| Ausführungsschonfrist | Die Zeit, nach der ein Vorschlag ausführbar wird, während der er ausgeführt werden muss. | 7 Tage | 7 Tage | 7 Tage | 7 Tage |
| Mindest-Timelock-Verzögerung | Minimale Verzögerung, bevor ein Vorschlag ausgeführt wird (nach der Warteschlange) | 1 Tag | 0 Tage | 5 Tage | 4 Tage |
| Maximale Timelock-Verzögerung | Maximale Verzögerung vor der Ausführung eines Vorschlags (nach der Warteschlange) | 7 Tage | 1 Tag | 21 Tage | 21 Tage |

Sobald der Abstimmungszeitraum endet und ein Vorschlag erfolgreich war, kann jeder die Warteschlange anrufen, um die Zeitsperrverzögerung zu beginnen.

Für den Priority Timelock Executor von Starkware hat er eine Prioritätsperiode von 7 Tagen außerhalb der 9-tägigen Timelock-Verzögerung. Das bedeutet, dass nach 9 Tagen jeder einen Vorschlag ausführen kann, aber innerhalb von 2-9 Tagen (der Prioritätsfrist) hat Starkware die Möglichkeit, den Vorschlag auszuführen.

In der Praxis heißt das:

* Tage 0–2: Niemand kann ausführen
* Tage 2–9: Nur Starkware kann ausführen
* Tage 9: Jeder kann ausführen

## 7. (Optional) Stornierung des Vorschlags

Zu jedem Zeitpunkt in einem DIP-Lebenszyklus kann der Vorschlagende den DIP stornieren. Ein Vorschlag kann von jedem storniert werden, bevor er ausgeführt wird, wenn der Vorschlagende im aktuellen Block nicht über ausreichende Vorschlagskraft verfügt.

## FAQ

### Was ist der Zweck der Abstimmungsverzögerung?

Die **Abstimmungsverzögerung** ist die Anzahl der Ethereum-Blöcke, die gewartet werden muss, bevor die Abstimmung über einen Vorschlag beginnen kann, nachdem ein Vorschlag eingereicht wurde.

Das DYDX-Stimmrecht muss entweder vollständig vor der Einreichung eines Vorschlags oder während der  **Abstimmungsverzögerung**  des Vorschlags an eine Adresse delegiert werden.

Im Moment ist die **Abstimmungsverzögerung** auf `6.570 Blöcke` eingestellt, was etwa 1 Tag entspricht. Dieser Wert wird bei der Erstellung eines Vorschlags zur aktuellen Blocknummer addiert.

In Zukunft kann dYdX Governance über eine Verlängerung oder Verkürzung der **Abstimmungsverzögerung** abstimmen. Eine erhöhte **Abstimmungsverzögerung** hat offensichtliche Vorteile. Es kann zu einigen potenziell nachteiligen Ergebnissen führen, wie z. B. opportunistische Grenzfallausnutzung.

### Was ist der Zweck der Vorschlagsschwelle?

Da DYDX eine frei handelbare Anlage ist, kann jeder eine Governance-Übernahme durch Marktkäufe versuchen. Um eine böswillige Abstimmung zu erzwingen, wären jedoch mindestens 5 Millionen DYDX im Falle einer kurzen Zeitsperre oder 20 Millionen DYDX im Falle einer langen Zeitsperre erforderlich. Wenn nicht gar unmöglich, wäre dieser Betrag unerschwinglich teuer und würde unter Berücksichtigung von Preisschwankungen wahrscheinlich mehr kosten als der Nettogewinn aus dem Angriff.

Wenn eine Gruppe irgendwie eine böswillige Übernahme erreicht, würde die Zeitsperre den betroffenen Agenten Zeit geben, ihre Anlagen aus dem Protokoll zurückzuziehen. Dies wäre auch eine Gelegenheit, das Protokoll zu forken, ein Weg, den wahrscheinlich die verbleibenden gutgläubigen Akteure einschlagen würden.

###
