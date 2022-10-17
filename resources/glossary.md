---
description: Überblick über die wichtigsten Governance-Begriffe.
---

# Glossar

**DYDX:** Die native Anlage des DYDX-Ökosystems, das die Grundlage für Governance und Sicherheit für das dUdX-Protokoll darstellt. DYDX ist ein ERC-20-Token, das das Gewicht der Abstimmungs- oder Vorschlagsbefugnis eines Benutzers angibt.

**dYdX-Protokoll: **Das Ebene-2-Perpetuals-Protokoll von dYdX.

**dYdX Foundation:** Eine unabhängige Stiftung mit Hauptsitz in Zug, Schweiz, wurde gegründet, um sich an der Weiterentwicklung des dYdX-Protokolls in Zukunft zu beteiligen.

**Der DYDX Token Contract**: verfügt über Speicherauszüge der Stimmrechte jeder einzelnen Adresse in unterschiedlichen Zeiträumen.

**DIP:** dYdX-Verbesserungsvorschläge sind On-Chain-Vorschläge.

**DRC**: dYdX Request for Comments sind Off-Chain-Vorschläge und der erste erforderliche Schritt im Governance-Verbesserungsprozess.

**Quorum:** Damit eine Abstimmung angenommen wird, muss sie ein Mindestquorum von DYDX-Tokens zustimmend erreichen. Der Zweck des Quorums besteht darin, sicherzustellen, dass die einzigen Maßnahmen, die angenommen werden, eine angemessene Stimmbeteiligung haben.

**Epoche:** Alle anderen Verträge arbeiten in 28-Tage-Zyklen, die als Epochen bezeichnet werden.

**Ausführungsfrist:** Der Zeitraum nach der Abstimmung, wenn ein DIP-Vorschlag ausführbar wird, während dessen er ausgeführt werden muss.

**Der Governance-Strategie-Vertrag**: enthält die Logik, um die relativen Vorschlags- und Abstimmungsrechte der Benutzer zu messen.

**Gouverneursvertrag**: verfolgt Vorschläge und kann Vorschläge über den Timelock Smart-Vertrag ausführen.

**Long Timelock Executor:** Der Long Timelock Executor kann Vorschläge ausführen, die im allgemeinen Teile des Protokolls ändern, die den Governance-Konsens beeinflussen.

**Der Merkle-Pauser Executor:** kann Vorschläge zur Einfrierung der Merkle Root ausführen, welche in regelmäßigen Abständen mit der kumulativen Prämienbilanz eines jeden Benutzers aktualisiert wird und somit sukzessive neue Prämien zur Verteilung an die Benutzers freisetzt, im Falle, dass die vorgeschlagene Root falsch oder bösartig ist.

**Sicherheitspool:** Komponente, die dafür zuständig ist, das Protokoll vor Insolvenz zu schützen.

**Staked dYdX-Vertrag**: enthält Logiken, um DYDX Token zu staken, die Position zu tokenisieren and Prämien zu erhalten.

**Short Timelock Executor:** Der Short Timelock Executor kann Vorschläge ausführen, die im allgemeinen Prämien- und Incentive-Verträge oder die Gemeinschaftskasse ändern, die ein schnelles Eingreifen erfordern.

**Starkware-Executor:** Der Starkware-Executor kann Vorschläge ausführen, die im allgemeinen Teile des Protokolls ändern, die derzeit ein Eingreifen von Starkware erfordern.

**Timelock-Vertrag**: kann von Governance gewählte Transaktionen in die Warteschlange stellen, abbrechen oder ausführen. Die Funktionen in einem Vorschlag werden durch den Timelock Contract initiiert. Transaktionen in der Warteschlange können nach einer Verzögerung und bis zum Ablauf der Nachfrist ausgeführt werden.

**Timelock-Verzögerung:** Die Verzögerung, bevor ein DIP-Vorschlag ausgeführt wird, nachdem ein Vorschlag bestanden und in die Warteschlange gestellt wurde.

**Vorschlagsschwelle:** Um zu verhindern, dass unzählige Spam-Vorschläge erstellt werden, erfordert eine Vorschlagsschwelle, dass eine Adresse eine bestimmte Anzahl von Stimmen hat, bevor sie einen Vorschlag machen kann.

**Vorschlagsmacht:** Token Stake, der den Zugang zum Erstellen und Unterstützen eines Vorschlags ermöglicht.

**Stimmrecht:** Stimmrecht, das verwendet wird, um für oder gegen bestehende Vorschläge zu stimmen.

**Abstimmungsverzögerung**: Dies ist die Zeitspanne, zwischen der ein Vorschlag erstellt werden kann und zur Abstimmung verfügbar ist. Indem mindestens ein Block bestanden werden muss, ist die Governance vor Flash-Loan-Angriffen geschützt, die möglicherweise eine große Anzahl von Token ausleihen, eine Abstimmung vorschlagen und über alles in einem Block abstimmen.

**Abstimmungszeitraum:** Sobald ein DIP-Vorschlag eingereicht wurde, müssen die Mitglieder der DYDX-Community ihre Stimme vor dem Ende des Abstimmungszeitraums abgeben. Dies ist die Zeitdauer, für die Vorschläge zur Abstimmung zur Verfügung stehen, mit Zeit in Ethereum-Blöcken.

**Vorschlagsschwelle:** Mindestens gehaltene/delegierte Token, die zum Erstellen eines DIP-Vorschlags erforderlich sind.

**Abstimmungsdifferenz:** Erforderliche Ja-Nein-Lücke, damit der DIP-Vorschlag angenommen wird.
