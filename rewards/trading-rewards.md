---
description: Überblick über das Trading Prämien-Programm.
---

# Trading-Prämien

`20,2`**`%` ** (`201.883.560 $DYDX`) des Tokenangebots werden an Benutzer verteilt, die auf der Grundlage der gezahlten Gebühren das dYdX-Layer-2-Protokoll handeln. Anfangs wurden `25,0 %` des Tokenangebots (`250.000.000 $DYDX`) als Handelsprämien zugewiesen.

* In [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md) hat die dYdX-Community [vereinbart](https://dydx.community/dashboard/proposal/8), die Handelsprämien um 25,0 % zu verringern. Infolgedessen sank die Zuteilung für Handelsprämien von `25,0 %` auf `20,2 %`.
* In [DIP20](https://dydx.community/dashboard/proposal/11) hat die dYdX-Community [vereinbart](https://dydx.community/dashboard/proposal/11), die Handelsprämien um weitere 45,.0 % zu verringern. In der Folge sank die Zuordnung als Handelsprämien von `20,2 %` auf `14,5 %`.

Die in einer bestimmten Epoche verteilten Handelsprämien wurden von 3.835.616 $DYDX auf 2.876.712 $DYDX in Epoche 15 und von 2.876.712 $DYDX auf 1.582.192 $DYDX in Epoche 21 reduziert.

**Ziele**

* Anreize zu schaffen, damit alle Trader das dYdX Layer 2-Protokoll verwenden.
* Marktliquidität und die allgemeine Produktnutzung zu beschleunigen.

## **Überblick**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Bezahlte Gebühren und geschätzte Rewards in einer bestimmten Epoche</p></figcaption></figure>

$DYDX werden an Händler verteilt, basierend auf den Gebühren, die im dYdX Layer 2 Protokoll gezahlt werden. $DYDX wird über einen Zeitraum von fünf Jahren auf einer 28 Tage umfassenden Zeitbasis ausgeschüttet und unterliegt keinen Sperrfristen oder Sperrvermerken. Pro Epoche werden 1.582.192 $DYDX verteilt.

Nachdem die Community dafür gestimmt hat, die Handelsprämien erneut um 25 % 958.904 $DYDX in [DIP16](https://dydx.community/dashboard/proposal/8) und um weitere 45 % 1.294.520 $DYDX in [DIP20](https://dydx.community/dashboard/proposal/11) zu verringern, können die verbleibenden 2.253.424 $DYDX, die im Handelsprämienkonto anfallen, von der dYdX-Community mit einer [Governance-Abstimmung](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verwendet/angewiesen werden.

<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k $$

| Begriff | Definition |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Prämie für einen bestimmten Trader. |
| R | Gesamtmenge der Prämien, die zwischen allen Tradern im Pool für die Epoche aufgeteilt werden müssen. |
| f | Gesamtgebühren, die von einem Trader in dieser Epoche gezahlt wurden. |
| w | Individueller Trader Score |
| $${\sum\limits {n} ${\sum\limits _{n} w_{n}} | Summer aller Trader Scores. |
| k | Gesamtzahl der Trader in dieser Epoche. |

Im Rahmen des [DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md), stimmte die dYdX-Community dafür, die Formel zu vereinfachen, sodass sie auf den Gesamtgebühren basiere, die von einem Trader in einem bestimmten Zeitraum gezahlt wurden.

## FAQ

### Wer ist für Trading-Prämien berechtigt?

Alle Händler im dYdX Layer 2 Protokoll sind zum Bezug von $DYDX als Handelsprämien berechtigt.

Das dYdX Layer 2-Protokoll ist für Trader in den Vereinigten Staaten oder in beschränkten Gebieten nicht verfügbar, wie in den [Nutzungsbedingungen](https://dydx.exchange/terms) von dYdX Trading Inc. definiert.

### Wie viel DYDX habe ich im Trading Rewards-Programm verdient?

In der aktuellen Epoche können Benutzer gezahlte Gebühren und geschätzte Trading-Rewards unter [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) einsehen, wo die Tradingdaten der Benutzer vorhanden sind.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Bezahlte Gebühren und geschätzte Rewards in einer bestimmten Epoche</p></figcaption></figure>

Rewards aus früheren Epochen können unter [**dydx.community/history/rewards**](https://dydx.community/history/rewards) eingesehen werden**.**

### Wie kann ich meine Trading-Prämien abholen? Wann kann ich meine verdienten $DYDX auszahlen lassen und überweisen?

Durch Handelsprämien verdiente $DYDX können am Ende eines jeden Zeitraums übertragen werden. Inhaber von $DYDX-Token müssen ungefähr `7 Tage` (**Wartezeit**) nach dem Ablauf der Zeitspanne warten, ehe sie ihre DYDX-Token beanspruchen können.

Nach der 7-tägigen Wartezeit kann jedes Community-Mitglied die `Write`-Funktion für den `updateRoot`-Parameter im [Merkle-Distributor-Vertrag](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) aufrufen, um DYDX-Prämien zu beanspruchen.

Schritte:

1. Klicken Sie auf der Seite des [Merkle Distributor Contract](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) auf Etherscan auf die Registerkarte `Contract` und wählen Sie `Write as Proxy` aus.
2. Klicken Sie auf die Schaltfläche `Connect to Web3` und verbinden Sie Ihr Web3-Wallet.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Scrollen Sie nach unten zum Parameter `updateRoot` und klicken Sie auf die Schaltfläche `Write`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Diese Transaktion würde einige wenige ETH für Gasgebühren erfordern. Die Transaktion wird fehlschlagen, wenn:**

* Die 7-tägige Wartefrist noch nicht abgelaufen ist oder
* Ein Community-Mitglied bereits erfolgreich den `updateRoot`-Parameter im [Merkle-Distributor-Vertrag](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) aufgerufen hat.

Sobald die Transaktion abgeschlossen ist, können Händler ihre Handelsprämien [hier](https://dydx.community/dashboard) einfordern. Zur Inanspruchnahme von $DYDX müssen die Benutzer auf `Anfordern` klicken, eine Transaktion unterzeichnen und Gasgebühren entrichten.

![Portfolio-Übersicht der Rewards](../.gitbook/assets/1-portfolio-overview-rewards.png)
