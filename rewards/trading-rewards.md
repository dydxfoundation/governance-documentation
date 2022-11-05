---
description: Überblick über das Trading Prämien-Programm.
---

# Trading-Prämien

`25,00 %` der ursprünglichen Tokenversorgung (`250 000 000 DYDX`) wurden der Ausschüttung an die Nutzer zugewiesen, die auf der Grundlage der gezahlten Gebühren mit dem dYdX Layer 2-Protokoll handeln. Im Rahmen des [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md) [stimmte](https://dydx.community/dashboard/proposal/8) die dYdX-Community dafür, die Trading Rewards um 25 % zu reduzieren. Daher wurden in Epoche 15 die in einer Epoche ausgeschütteten Trading Rewards von einst 3 835 616 DYDX nun auf 2 876 712 DYDX reduziert.

**Ziele**

* Anreize zu schaffen, damit alle Trader das dYdX Layer 2-Protokoll verwenden.
* Marktliquidität und die allgemeine Produktnutzung zu beschleunigen.

## **Überblick**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Bezahlte Gebühren und geschätzte Rewards in einer bestimmten Epoche</p></figcaption></figure>

DYDX wird auf der Grundlage der Gebühren, die für das dYdX Layer 2-Protokoll gezahlt wurden, an die Trader ausgeschüttet. DYDX wird über fünf Jahre auf Basis von 28-Tage-Epochen verteilt und unterliegt weder Vesting noch Lockups. Pro Epoche werden 2 876 712 DYDX ausgeschüttet.

Da die Community dafür gestimmt hat, die Trading Rewards um 25 % von 3 835 616 DYDX auf 2 876 712 DYDX zu reduzieren, können die verbleibenden 958904 DYDX, die in der Rewards Treasury anfallen, von der dYdX-Community mit einer [Governance-Abstimmung](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verwendet/ausgerichtet werden.

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

Alle Trader des dYdX Layer 2-Protokolls sind berechtigt, DYDX als Trading-Prämien zu empfangen.

Das dYdX Layer 2-Protokoll ist für Trader in den Vereinigten Staaten oder in beschränkten Gebieten nicht verfügbar, wie in den [Nutzungsbedingungen](https://dydx.exchange/terms) von dYdX Trading Inc. definiert.

### Wie viel DYDX habe ich im Trading Rewards-Programm verdient?

In der aktuellen Epoche können Benutzer gezahlte Gebühren und geschätzte Trading-Rewards unter [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) einsehen, wo die Tradingdaten der Benutzer vorhanden sind.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Bezahlte Gebühren und geschätzte Rewards in einer bestimmten Epoche</p></figcaption></figure>

Rewards aus früheren Epochen können unter [**dydx.community/history/rewards**](https://dydx.community/history/rewards) eingesehen werden**.**

### Wie kann ich meine Trading-Prämien abholen? Wann kann ich meine verdienten DYDX auszahlen lassen und überweisen?

Durch Trading-Prämien verdiente DYDX können am Ende jeder Epoche übertragen werden. Inhaber von DYDX-Token müssen ungefähr `7 Tage` (**Wartezeit**) nach dem Ende der Epoche warten, um ihre DYDX-Token zu beanspruchen.

Nach der 7-tägigen Wartezeit kann jedes Community-Mitglied die `Write`-Funktion für den `updateRoot`-Parameter im [Merkle-Distributor-Vertrag](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) aufrufen, um DYDX-Prämien zu beanspruchen.

Schritte:

1. Klicken Sie auf der Vertragsseite von [Merkle Distributor](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) auf Etherscan auf die Registerkarte `Vertrag` und wählen Sie `Als Proxy schreiben aus.`
2. Klicken Sie auf die Schaltfläche `Connect to Web3` und verbinden Sie Ihr Web3 Wallet.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. Scrollen Sie nach unten zum Parameter `updateRoot` und klicken Sie auf die `Schaltfläche Schreiben`.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Diese Transaktion würde einige wenige ETH für Gasgebühren erfordern. Die Transaktion wird fehlschlagen, wenn:**

* Die 7-tägige Wartefrist gilt weiterhin, oder
* Ein Community-Mitglied hat bereits erfolgreich den `updateRoot`-Parameter im [Merkle-Distributor-Vertrag](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) aufgerufen.

Sobald die Transaktion abgeschlossen ist, können Händler ihre Handelsprämien [hier](https://dydx.community/dashboard) einfordern. Benutzer müssen auf `Claim` klicken, eine Transaktion unterzeichnen und Gasgebühren bezahlen, um DYDX zu beanspruchen.

![Portfolio-Übersicht der Rewards](../.gitbook/assets/1-portfolio-overview-rewards.png)
