---
description: Ein Überblick über die Gemeinschaftskasse.
---

# Gemeinschaftskasse

`16,2`**`%` ** (`162.004.734 $DYDX`) des Tokenangebots werden der **** Gemeinschaftskasse für die dYdX-Community zugewiesen, die fortlaufend für Beitragszuschüsse, Gemeinschaftsinitiativen, Liquiditäts-Mining und andere Programme fortlaufend verwendet werden sollen. Zu Beginn wurden `5,0 %` des Tokenangebots ( `50.000.000 $DYDX` ) der Gemeinschaftskasse zugewiesen und 766.703 $DYDX gingen in jedem Durchgang in die Gemeinschaftskasse ein. Aktuell befinden sich 2.492.731 $DYDX in der Gemeinschaftskasse, da drei Governance-Vorschläge zu einer Erhöhung von 1.726.028 $DYDX führten, die der dYdX-Gemeinschaft pro Laufzeit zur Verfügung stehen:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - wurden die Staking-Prämien für USDC auf 0 gesetzt (383.562 $DYDX pro Laufzeit)
* [DIP 16](https://dydx.community/dashboard/proposal/8) - wurden die Handelsprämien um 25 % (958.904 $DYDX pro Laufzeit) reduziert, und
* [DIP 17](https://dydx.community/dashboard/proposal/9) - wurden die Prämien für $DYDX-Staking auf 0 gesetzt (383.562 $DYDX pro Laufzeit).



**Ziele**

* Finanzierungsprogramme und Initiativen, die das Wachstum von dYdX vorantreiben.
* Entwickeln Sie Zuschussprogramme, um Community-NFTs, Hackathons, Analyse-Dashboards, Memes, Swag, Tools von Drittanbietern, Übersetzungen und andere Projekte zu finanzieren.
* Entwickeln Sie ein erstklassiges Governance-System und schaffen Sie Anreize für eine robuste Governance.

## Überblick

Die Gemeinschaftskasse behält $DYDX, um damit nach Belieben der $DYDX-Inhaber zu verfahren, sei es für Zuschüsse, neue Liquiditäts-Mining-Pools oder andere Programme. $DYDX wird über einen Zeitraum von fünf Jahren kontinuierlich an die Gemeinschaftskasse übertragen. Eine Governance-Abstimmung ist erforderlich, um $DYDX aus der Gemeinschaftskasse auszugeben.

Wenn nach fünf Jahren die Governance eine dauerhafte Inflation (bei einer maximalen jährlichen Inflation von `2 %`) verordnet, werden die neu ausgestellten $DYDX der Gemeinschaftskasse zur Verfügung stehen.

## FAQ

### Wie geht $DYDX in die Gemeinschaftskasse ein?

Jede Sekunde überweist der Gemeinschaftsschatzmeister (siehe Details [hier](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview)) [`0,3169242627`](tel:03169242627) $DYDX an die Gemeinschaftskasse. Sobald $DYDX unverfallbar geworden ist, wird der unverfallbare SDYDX-Betrag durch den Aufruf der `Anspruchsfunktion` auf dem Gemeinschaftschatzmeister an die Gemeinschaftskasse übertragen. Jedes Mitglied der dYdX-Community kann [hier](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) die `Beanspruchungsfunktion` auf Etherscan aufrufen (erfordert einige ETH für Gasgebühren), um die einbehaltenen DYDX vom Gemeinschaftsschatzmeister in die Gemeinschaftskasse zu verschieben.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### Wie hoch ist das tatsächliche Guthaben der Community-Treasury?

Mitglieder der dYdX-Community können [hier](https://dydx.shippooor.xyz/) den Rücklagen-Kontostand der Community Treasury einsehen. \
\
Darüber hinaus veröffentlicht die dYdX Foundation den Rücklagen-Kontostand der Community Treasury in der [Epochen-Rückschau](https://dydx.foundation/blog) am Ende jeder Epoche. Zusätzlich zu den im Gemeinschaftskasse eingetragenen $DYDX kann die dYdX-Community auch auf die $DYDX, die in der Prämienkasse anfallen, zugreifen, weil die Abstimmungen (1) die Handelsprämien um 25 % (958.904 $DYDX) reduzieren, (2) die Prämien für USDC auf 0 (383.562 $DYDX) und (3) die Prämien für $DYDX auf 0 (383.562 $DYDX) setzen. [](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters)Ab Periode 17 werden pro Laufzeit 1.726.028 $DYDX in der Prämienkasse angelegt und können von der dYdX-Gemeinschaft mit einer Governance-Abstimmung verwendet werden

### Wer kann Vorschläge zur Ausgabe von $DYDX aus der Gemeinschaftskasse einreichen?

Jeder Benutzer mit ausreichender Vorschlagsbefugnis kann Vorschläge einreichen. Eine Governance-Abstimmung ist erforderlich, um $DYDX aus der Gemeinschaftskasse auszugeben. Um einen Vorschlag einzureichen, reichen Sie bitte einen dYdX-Verbesserungsvorschlag (DIP) ein, wie im [Lebenszyklus des DIP-Vorschlags](../voting-and-governance/dip-proposal-lifecycle.md) beschrieben.

### Wie erstellen Sie einen Vorschlag zur Verwendung von Mitteln der Community?

Reverie hat eine umfassende, technische und schrittweise Anleitung zusammengestellt, wie jedes dYdX-Community-Mitglied mit mehr als 5 Mio. $DYDX ([Vorschlagsschwelle](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) für eine [kurzfristige Abstimmung](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) einen Vorschlag erstellen kann, um $DYDX aus der Gemeinschaftskasse an eine Zieladresse zu übertragen. Klicken Sie bitte [hier](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal), um auf den technischen Leitfaden zuzugreifen.

### Welche Arten von Vorschlägen können bei der Gemeinschaftskasse eingereicht werden?

Eine von der Gemeinschaft verwaltete Kasse eröffnet eine Welt voller Möglichkeiten. Wir hoffen auf verschiedene Experimente und Initiativen, einschließlich Ökosystemzuschüsse, die das Wachstum des Ökosystems des dYdX-Ebene-2-Protokolls fördern können.
