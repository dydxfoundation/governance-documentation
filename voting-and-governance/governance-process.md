---
description: Ein grober Überblick über die Governance-Architektur.
---

# Architektur

## Übersicht

$ethDYDX, $stkDYDX und $wethDYDX („Governance-Token“) gewähren Inhabern das Recht, Änderungen an dYdX v3 vorzuschlagen und darüber abzustimmen. dYdX-Governance basiert auf den AAVE-Governance-Verträgen und unterstützt die Abstimmung auf der Grundlage der Bestände an Governance-Token.

Vorschläge müssen ein vorgegebenes Minimum und einen bestimmten Prozentsatz an Ja-Stimmen je nach Art des Vorschlags übertreffen.

Das Stimm- und Vorschlagsrecht der Governance-Token ermöglicht es dem Governance-Token-Inhaber, Vorschläge zu unterbreiten und über Governance-Vorschläge abzustimmen. Beachten Sie, dass der Inhaber von Governance-Token solche Befugnisse an andere Ethereum-Adressen delegieren kann.

Im Kern der dYdX Governance stehen 8 Smart-Verträge:

* **Die `$ethDYDX, $stkDYDX und $wethDYDX-Token`-Verträge**: Verfügen über Momentaufnahmen der Stimmrechte jeder einzelnen Adresse in unterschiedlichen Zeiträumen.
* **Der `Governance-Strategie-V2-Vertrag`**: Enthält die Logik, um die relativen Vorschlags- und Abstimmungsrechte der Benutzer zu messen. Die dYdX-Community [hat für](https://dydx.community/dashboard/proposal/15) ein Upgrade des `Governance-Strategie`-Vertrags auf `Governance-Strategie V2` gestimmt, um $wethDYDX mit der gleichen Governance-Funktionalität wie ethDYDX für die Abstimmung und den Vorschlag in dYdX v3-Governance auszustatten.
* **Der `Sicherheitsmodul`-Vertrag**: Enthält Logiken, um $ethDYDX-Token zu staken, die Position zu tokenisieren and Prämien zu erhalten. Token, die im Sicherheitsmodul gestaket sind, behalten die vollständigen Governance-Rechte bei.
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

Der Starkware Prioritiy Timelock Executor besitzt den StarkEx Perpetual Exchange Contract. Damit können Vorschläge ausgeführt werden, die die Konfiguration von dYdX v3 steuern.

Je nachdem, welche Aktion erforderlich ist, muss gegebenenfalls das Starkware-Team einbezogen werden, um die Änderung an der Exchange-Börse korrekt umzusetzen. Aus diesem Grund wird diesem Executor die Rolle eines "Priority Controllers" zugewiesen, wodurch Starkware ein Zeitraum von 7 Tagen eingeräumt wird (**Priority Periode**), in welchem ausschließlich sie die Möglichkeit haben, die Ausführung eines Vorschlags auszulösen.

Starkware hat keine Kontrolle _darüber, welche_ Protokolländerungen vorgenommen werden. Nur Inhaber von $ethDYDX- und $wethDYDX-Token können über dYdX v3-Governance Änderungen am Austauschprotokoll genehmigen oder verweigern.

#### **Long Timelock Executor**

Der Long-Timelock-Executor kann Vorschläge ausführen, die im Allgemeinen Teile von dYdX v3 ändern, die sich auf den Governance-Konsens auswirken.

#### **Merkle-Pauser Executor**

Der Merkle-Pauser Executor kann Vorschläge zur Einfrierung der Merkle Root ausführen, welche in regelmäßigen Abständen mit der kumulativen Prämie-Bilanz eines jeden Benutzers aktualisiert wird und somit sukzessive neue Prämien zur Verteilung an die Benutzers freisetzt, im Falle, dass die vorgeschlagene Root falsch oder bösartig ist. Es kann auch Einspruch gegen erzwungene Trade-Anfragen durch jedweden der Stark-Proxy-Verträge erheben.

Die Initial Timelock Parameter lauten wie folgt:

![Initial Timelock Parameter](../.gitbook/assets/1-initial-timelock-parameters.png)
