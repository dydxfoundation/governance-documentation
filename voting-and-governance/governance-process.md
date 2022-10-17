---
description: Ein grober Überblick über die Governance-Architektur.
---

# Architektur

## Überblick

DYDX räumt den Inhabern das Recht ein, Änderungen des Protokolls vorzuschlagen und über diese abzustimmen. Die DYDX Governance basiert auf der AAVE-Governance und unterstützt Abstimmungen auf Basis von DYDX Token-Beteiligungen.

Vorschläge müssen ein vorgegebenes Minimum und einen bestimmten Prozentsatz an Ja-Stimmen je nach Art des Vorschlags übertreffen.

Diese DYDX Token können dazu verwendet werden, Vorschläge zu machen oder über Governance-Vorschläge abzustimmen oder an andere Ethereum-Adressen delegiert zu werden.

Im Kern der dYdX Governance stehen 6 Smart Contracts:

* **Der `DYDX Token` Contract**: Verfügt über Speicherauszüge der Stimmrechte jeder einzelnen Adresse in unterschiedlichen Zeiträumen.
* **Der `Governance Strategie` Contract**: Enthält die Logik, um die relativen Vorschlags- und Abstimmungsrechte der Benutzer zu messen.
* **Der `Sicherheitsmodul` Contract**: Enthält Logiken, um DYDX Token zu staken, die Position zu tokenisieren and Prämien zu erhalten. Token, die im Sicherheitsmodul gestaket sind, behalten die vollständigen Governance-Rechte bei.
* **Der `Governor` Contract**: Verfolgt Vorschläge und kann über den Timelock Smart Contract Vorschläge durchführen.
* **Die `Timelock` Contracts**: können von der Governance abgestimmte Transaktionen in die Warteschlange stellen, diese stornieren oder ausführen. Die Funktionen in einem Vorschlag werden durch den Timelock Contract initiiert. In die Warteschlange gestellte Transaktionen können nach einer Verzögerung und vor Ablauf der Nachfrist ausgeführt werden.
* **Der `Priority Timelock` Contract**: Derselbe wie der Timelock Contract, jedoch erlaubt er dem Prioritäts-Prüfer die Ausführung von Transaktionen innerhalb der **Priority Periode** (7 Tage) vor Ablauf der Timelock-Verzögerung.

![Smart contract-Architektur](../.gitbook/assets/1-smart-contract-architectue.png)

Die dYdX on-chain Governance ermöglicht:

* Über Vorschläge, die durch jedweden autorisierten Executor Contract ausführbar sind, abzustimmen.
* Speicherauszüge von gehaltenen Token beim Start eines Vorschlages zu erstellen
* Die Delegation von Stimm- und Vorschlagsrechten voneinander zu trennen.
* Die Governance Schwellenwerte festzulegen-,einschließlich Vorschläge, Beschlussfassungen und Differentialstimmrechten
* Zu Ändern, wie Stimmen gewichtet werden (durch Änderung der "Governance-Strategy"-Smart Contract-Adresse im Governor Contract)

## Vorschlagsarten

Es gibt vier Arten von Vorschlägen mit unterschiedlichen Parametern, was die Länge und die Ausführung eines Vorschlags angeht, d.h. kritische Vorschläge, die den Governance Konsens betreffen, erfordern eine längere Abstimmzeit und ein eindeutigeres Abstimmungsergebnis, während Vorschläge, die lediglich Protokollparameter betreffen, weniger Abstimmungszeit erforderlich machen und schnell umgesetzt werden können. Ein Executor muss jede Art des Vorschlags einschätzen.

#### **Short Timelock Executor**

Der Short Timelock Executor steuert die folgenden Punkte:

* Incentive Contracts einschließlich Liquiditätsmodul, Sicherheitsmodul und Merkle Distributor-Modul
* Gelder in den Prämien und Community Treasuries
* Das Minting neuer Token
* Alle Proxy-Verträge außer dem Sicherheitsmodul
* Wächterrollen auf Stark-Proxy-Verträgen

**Starkware Priority Timelock Executor**

Der Starkware Prioritiy Timelock Executor besitzt den StarkEx Perpetual Exchange Contract. Es kann Vorschläge ausführen, die die Konfiguration der dYdX Layer 2-Exchange steuern.

Je nachdem, welche Aktion erforderlich ist, muss gegebenenfalls das Starkware-Team einbezogen werden, um die Änderung an der Exchange-Börse korrekt umzusetzen. Aus diesem Grund wird diesem Executor die Rolle eines "Priority Controllers" zugewiesen, wodurch Starkware ein Zeitraum von 7 Tagen eingeräumt wird (**Priority Periode**), in welchem ausschließlich sie die Möglichkeit haben, die Ausführung eines Vorschlags auszulösen.

Starkware hat keine Kontrolle _darüber, welche_ Protokolländerungen vorgenommen werden. Nur DYDX Token-Inhaber haben über dYdX Governance die Möglichkeit, Änderungen am Exchange-Protokoll zu genehmigen oder zu abzulehnen.

#### **Long Timelock Executor**

Der Long Timelock Executor kann Vorschläge ausführen, die zumeist Teile des Protokolls ändern, welche den Governance Konsens betreffen.

#### **Merkle-Pauser Executor**

Der Merkle-Pauser Executor kann Vorschläge zur Einfrierung der Merkle Root ausführen, welche in regelmäßigen Abständen mit der kumulativen Prämie-Bilanz eines jeden Benutzers aktualisiert wird und somit sukzessive neue Prämien zur Verteilung an die Benutzers freisetzt, im Falle, dass die vorgeschlagene Root falsch oder bösartig ist. Es kann auch Einspruch gegen erzwungene Trade-Anfragen durch jedweden der Stark-Proxy-Verträge erheben.

Die Initial Timelock Parameter lauten wie folgt:

![Initial Timelock Parameter](../.gitbook/assets/1-initial-timelock-parameters.png)
