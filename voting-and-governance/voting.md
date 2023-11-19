---
description: Ein Überblick über den Abstimmungsprozess.
---

# Abstimmungsprozess

dYdX v3 wird von Inhabern und Delegierten von Governance-Token verwaltet und aktualisiert.

## **Vorschlags- und Stimmrechte**

Mit jedem der Governance-Token sind zwei Rechte verbunden:

* Das **Vorschlagsrecht** ermöglicht die Ausgestaltung und Aufrechterhaltung eines Vorschlags.
* Das **Stimmrecht** wird zur Abstimmung für oder gegen bestehende Vorschläge ausgeübt.

Inhaber von Governance-Token erhalten Governance-Rechte proportional zu ihrer Summe der im Besitz befindlichen und delegierten Token in einem bestimmten Block.

**`Vorschlagsrecht =`**`Vorschlagsrecht aus $ethDYDX-Token +`

`Vorschlagsrecht von $wethDYDX-Token +`

`Vorschlagsrecht von $stkDYDX-Token +`

`Vorschlagsrecht von $ethDYDX-Token, die als Delegierter erhalten werden +`

`Vorschlagsrecht von DYDX Token, empfangen als Delegierter +`

`Vorschlagsrecht von $stkDYDX-Token, empfangen als Delegierter -`

`Vorschlagsrecht von $ethDYDX delegiert -`

`Vorschlagsrecht von $wethDYDX delegiert -`

`Vorschlagsrecht von staked-DYDX delegiert`

\`\`

**`Stimmrecht =`**`Vorschlagsrecht von $ethDYDX-Token +`

`Stimmrecht von $wethDYDX-Token +`

`Stimmrecht von $stkDYDX-Token +`

`Stimmrecht von $ethDYDX-Token, die als Delegierter erhalten werden +`

`Stimmrecht von $wethDYDX-Token, empfangen als Delegierter +`

`Stimmrecht von $stkDYDX-Token, empfangen als Delegierter -`

`Stimmrecht von $ethDYDX delegiert -`

`Stimmrecht von $wethDYDX delegiert -`

`Stimmrecht von $stkDYDX delegiert`

## FAQ

### Wie stimme ich ab?

Um an dYdX-Governance teilzunehmen, müssen Sie über die Governance-Token verfügen oder delegiert werden. Sie benötigen ebenfalls ETH, um Transaktionskosten zu decken.

Wenn Sie Token besitzen oder Ihnen Token delegiert wurden und ein aktiver Vorschlag vorliegt, sind Sie bereit, in der dYdX Governance abzustimmen.

![Geben Sie ihre Stimme ab, indem sie von Ihren Stimmrechten Gebrauch machen](../.gitbook/assets/1-voting-power.png)

Um Ihre Abstimmung einzureichen, navigieren Sie zu der Vorschlagsseite und klicken Sie auf einen aktiven Vorschlag.

### **Wie delegiere ich?**

dYdX-Governance ermöglicht es Inhabern, Stimmrechte an die Adresse ihrer Wahl zu delegieren. Jeder kann sich an der dYdX Governance beteiligen, indem er eine Delegation empfängt, ohne dass er Governance-Token besitzen muss. Benutzer können gleichzeitig nur an eine Adresse delegieren, und die Anzahl der Stimmen, die der Stimmenzählung des Delegierten zugerechnet werden, entspricht der Bilanz von Governance-Token im Konto des Benutzers. Die Stimmen werden vom aktuellen Block aus delegiert, bis der Sender erneut delegiert oder seine Governance-Token überweist.

![Weisen Sie anderen ihre Stimm- und Vorschlagsrechte zu](../.gitbook/assets/1-delegate-power.png)

Token-Inhaber können auswählen, ob sie eine oder beide der Governance-Rechte, die mit einem Token verbunden sind, entweder über das Governance-Portal oder programmgesteuert delegieren wollen.Delegieren Sie Ihr Stimm- und Vorschlagsrecht Ein Benutzer, dem Rechte zugewiesen wurden, kann diese nicht an andere Delegierte weiterleiten.

Token-Inhaber können Vorschlagsrechte und Stimmrechte an verschiedene Adressen delegieren. Allerdings ist keine partielle Delegation möglich (nur 100 % oder 0 % Rechte).

So delegieren Sie Ihre Token an eine Wallet-Adresse:

* Gehen Sie zu [dydx.community/Dashboard](https://dydx.community/dashboard)
* Klicken Sie auf "Delegieren"
* Wählen Sie die Art der Rechte aus, die Sie delegieren möchten.
* Geben Sie eine Wallet-Adresse derjenigen Drittpartei ein, an welche Sie Ihre Stimm- und/oder Vorschlagsrechte delegieren möchten. Das Delegieren von Rechten überträgt nicht Ihre Token

Für die Delegierung und Rückabwicklung von Governance-Token müssen Benutzer Ethereum-Gasgebühren bezahlen.

### Kann ich meine Abstimmung ändern, nachdem ich bereits abgestimmt habe?

Sobald eine Stimme auf der Chain abgegeben wurde, ist es nicht mehr möglich, Ihre Abstimmung zu ändern.

### Kann ich meine Governance-Token übertragen, während die Abstimmung läuft?

Ja.

### Kann ich meiner Abstimmung weitere Token hinzufügen?

Wenn ein DIP auf der Chain eingereicht wird, wird ein Speicherauszug des aktuellen Token-Inhabers erstellt. Benutzer müssen vor dem Startblock Governance-Token besitzen.
