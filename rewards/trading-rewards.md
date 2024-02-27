---
description: Überblick über das Trading Prämien-Programm.
---

# Trading-Prämien

`14,5` **`%`** (`144.693.506 $ethDYDX`) des Tokenangebots werden auf der Grundlage der gezahlten Gebühren an Benutzer verteilt, die auf dYdX v3 handeln. Anfangs wurden `25,0 %` des Token-Angebots (`250.000.000 $ethDYDX`) für die Handelsprämien zugewiesen.

* In [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md) hat die dYdX-Community [vereinbart](https://dydx.community/dashboard/proposal/8), die Handelsprämien um 25,0 % zu verringern. Infolgedessen sank die Zuteilung für Handelsprämien von `25,0 %` auf `20,2 %`.
* In [DIP 20](https://dydx.community/dashboard/proposal/11)hat die dYdX-Community [vereinbart](https://dydx.community/dashboard/proposal/11), die Handelsprämien um weitere 45,0 % zu verringern. In der Folge sank die Zuordnung als Handelsprämien von `20,2 %` auf `14,5 %`.
*   In [DIP 29](https://dydx.community/dashboard/proposal/16)hat die dYdX-Community [vereinbart](https://dydx.community/dashboard/proposal/16), die Handelsprämien von Epoche 30-32 auf dYdX v3 um ⅓ auf die folgenden Werte zu reduzieren:

    * Epoch 30: 1.054.795 $ethDYDX
    * Epoch 31: 527.398 $ethDYDX
    * Epoche 32: 0 $ethDYDX

    Beachten Sie bitte, dass die dYdX-Community in DIP 29 dafür gestimmt hat, die verbleibende Zuteilung von Handelsprämien in die dYdX Chain for Trading Rewards zu migrieren.

Die in einer bestimmten Epoche verteilten Handelsprämien wurden/werden von 3.835.616 $ethDYDX reduziert auf:

* 2.876.712 $ethDYDX in Epoche 15,
* 1.582.192 $ethDYDX in Epoche 21,
* 1.054.795 $ethDYDX in Epoche 30,
* 527.398 $ethDYDX in Epoche 31,
* 0 $ethDYDX in Epoche 32 und weiter.

Nach Epoche 31 wird es keine Handelsprämien auf dYdX v3 mehr geben. In [DIP 29](https://dydx.community/dashboard/proposal/16) auf dYdX v3 und [Proposal 2](https://www.mintscan.io/dydx/proposals/2) auf dYdX Chain stimmte die dYdX-Community dafür, den verbleibenden Betrag an nicht übertragenem $ethDYDX in dYdX v3 [Rewards Treasury Vester](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f) dem [dYdX Chain Rewards Treasury Vester `(dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk)`](https://www.mintscan.io/dydx/address/dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk) gutzuschreiben und anschließend als Trading-Prämien auf der dYdX Chain zu verteilen, vorbehaltlich der Governance-Genehmigung auf dYdX Chain.

**Ziele**

* Anreize für alle Händler, dYdX v3 zu verwenden.
* Marktliquidität und die allgemeine Produktnutzung zu beschleunigen.

## **Überblick**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Bezahlte Gebühren und geschätzte Rewards in einer bestimmten Epoche</p></figcaption></figure>

$ethDYDX wurde an Händler basierend auf den auf dYdX v3 gezahlten Gebühren verteilt. $ethDYDX wurde auf einer 28-tägigen Epochenbasis über fünf Jahre verteilt und unterlag keinen Sperrfristen oder Sperrvermerken.

In [DIP 29](https://dydx.community/dashboard/proposal/16)hat die dYdX-Community [vereinbart](https://dydx.community/dashboard/proposal/16), die Handelsprämien von Epoche 30-32 auf dYdX v3 um ⅓ auf die folgenden Werte zu reduzieren:

* Epoch 30: 1.054.795 $ethDYDX
* Epoch 31: 527.398 $ethDYDX
* Epoche 32 und alle verbleibenden Epochen: 0 $ethDYDX



<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k $$

| Begriff | Definition |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Prämie für einen bestimmten Trader. |
| R | Gesamtmenge der Rewards, die zwischen allen Tradern im Pool für die Epoche aufgeteilt werden müssen. |
| f | Gesamtgebühren, die von einem Trader in dieser Epoche gezahlt wurden. |
| w | Individueller Trader Score |
| $${\sum\limits {n} ${\sum\limits _{n} w_{n}} | Summer aller Trader Scores. |
| k | Gesamtzahl der Trader in dieser Epoche. |

Im Rahmen des [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), stimmte die dYdX-Community dafür, die Formel zu vereinfachen, sodass sie auf den Gesamtgebühren basiere, die von einem Trader in einem bestimmten Zeitraum gezahlt wurden.

## FAQ

### Wer ist für Trading-Prämien berechtigt?

Alle Trader auf dYdX v3 waren berechtigt, $ethDYDX als Trading-Prämien zu erhalten.

dYdX v3 ist nicht für Anbieter in den Vereinigten Staaten oder in den eingeschränkten Gebieten verfügbar, wie in den [Nutzungsbedingungen](https://dydx.exchange/terms) von dYdX Trading Inc. definiert.

### Wie viel $ethDYDX habe ich im Rahmen des Bonusprogramms verdient?

In der aktuellen Epoche können Benutzer gezahlte Gebühren und geschätzte Trading-Rewards unter [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) einsehen, wo die Tradingdaten der Benutzer vorhanden sind.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Bezahlte Gebühren und geschätzte Rewards in einer bestimmten Epoche</p></figcaption></figure>

Rewards aus früheren Epochen können unter [**dydx.community/history/rewards**](https://dydx.community/history/rewards) eingesehen werden**.**

### Wie kann ich meine Trading-Prämien abholen? Wann kann ich meine verdienten ethDYDX auszahlen lassen und überweisen?

Verdiente $ethDYDX-Token über Handelsprämien sind am Ende jeder Epoche übertragbar. Inhaber von $ethDYDX-Token müssen ungefähr `7 Tage` (**Wartezeit**) nach dem Ende der Epoche warten, um ihre $ethDYDX-Token zu beanspruchen.

Nach der 7-tägigen Wartezeit kann jedes Community-Mitglied die `Write`-Funktion für den `updateRoot`-Parameter im [Merkle-Distributor-Vertrag](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) aufrufen, um $ethDYDX-Prämien zu beanspruchen.

Schritte:

1. Klicken Sie auf der Seite des [Merkle Distributor Contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) auf Etherscan auf die Registerkarte `Contract` und wählen Sie `Write as Proxy` aus.
2. Klicken Sie auf die Schaltfläche `Connect to Web3` und verbinden Sie Ihr Web3-Wallet.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Scrollen Sie nach unten zum Parameter `updateRoot` und klicken Sie auf die Schaltfläche `Write`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Diese Transaktion würde einige wenige ETH für Gasgebühren erfordern. Die Transaktion wird fehlschlagen, wenn:**

* Die 7-tägige Wartefrist noch nicht abgelaufen ist oder
* Ein Community-Mitglied bereits erfolgreich den `updateRoot`-Parameter im [Merkle-Distributor-Vertrag](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) aufgerufen hat.

Sobald die Transaktion abgeschlossen ist, können Händler ihre Handelsprämien [hier](https://dydx.community/dashboard) einfordern. Zur Inanspruchnahme von $ethDYDX müssen die Benutzer auf `Anfordern` klicken, eine Transaktion unterzeichnen und Gasgebühren entrichten.

![Portfolio-Übersicht der Rewards](../.gitbook/assets/1-portfolio-overview-rewards.png)
