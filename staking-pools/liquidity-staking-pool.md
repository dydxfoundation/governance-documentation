---
description: Eine Übersicht über den Liquidity Staking Pool
hidden: wahr
---

# 🔋 Liquiditätsmodul

Der Liquidity Staking Pool ist seit dem 29. September 2022 nicht mehr aktiv. In [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) hat die dYdX-Community [dafür](https://dydx.community/dashboard/proposal/7) gestimmt, den Liquidity Staking Pool und den Borrowing Pool effektiv abzubauen, indem die Liquidity Staking Pool Prämien pro Sekunde auf 0 gesetzt werden.

In DIP 17 stimmte die dYdX-Community dafür, das Sicherheitsmodul effektiv abzubauen, indem die Sicherheitsmodul-Belohnungen pro Sekunde auf 0 gesetzt wurden.

Weitere Informationen zur dYdX-Chain-Community-Treasury finden Sie [hier](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury).

## **Staking**-Übersicht

Für im Liquidity Staking Pool eingesetzte $USDC gibt es derzeit keine Prämien.

## USDC Unstaking & Auszahlungen

Ein Staker muss mindestens `3 Tage` (**Sperrfenster**) vor dem Ende der [**Laufzeit**](../start-here/epochs.md) die Abhebung von $USDC verlangen, um seine $USDC nach dem Ende der Laufzeit abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre eingesetzten $USDC in die nächste Phase überführt.

Auszahlungen können während des **Blackout Window** nicht angefordert werden.

## FAQ

<details>

<summary>Was ist ein Blackout Window?</summary>

Ein Sperrfenster beschreibt eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten $USDC beantragen können. Die Funktion`requestWithdrawal` kann nicht während eines Blackout Window aufgerufen werden, das anfänglich als die letzten `3 Tage`einer Laufzeit konfiguriert ist. Neue Epochen beginnen alle 28 Tage. Mit anderen Worten: Die Nutzer können bis zu `3 Tage `vor Ablauf einer bestimmten Laufzeit eine Abhebung für die nächste Laufzeit beantragen.

</details>

<details>

<summary>Wie kann ich $USDC aus dem Staking Pool auszahlen lassen? Wie lange dauert es?</summary>

Ein Staker muss mindestens `3 Tage` vor dem Ende einer Laufzeit einen Antrag auf Entnahme von $USDC stellen, um seine $USDC nach dem Ende der Laufzeit abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre eingesetzten $USDC in die nächste Phase überführt.

Um $USDC abzuheben, rufen Benutzer die `Funktion Auszahlungsantrag` auf, um die Abhebung von $USDC für den nächsten Zeitraum anzufordern. Die Gelder der Benutzer verbleiben für die laufende Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

In der nächsten Phase rufen die Benutzer die Funktion `Stake auszahlen` auf, wodurch inaktive $USDC an eine bestimmte Adresse abgehoben werden. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion \`withdrawMaxStake\` aufrufen, um alle inaktiven Gelder abzuheben. Die Funktion `withdrawMaxStake` ist weniger gaseffizient als die Abfrage des Maximums über eth\_call und das Aufrufen von `withdrawStake()`.

Um $USDC für den Liquiditätspool freizugeben, gehen Sie wie folgt vor:

* Gehen Sie zu [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Klicken Sie auf „**Anfrage**“
* Geben Sie den $USDC-Betrag ein, den Sie zur Auszahlung aus dem Pool anfordern möchten, und klicken Sie auf „**Auszahlung anfordern**“. Sie müssen Gasgebühren zahlen, um $USDC zu entstaken.
* Staker, die mindestens `3 Tage` (**Blackout Window**) vor Ende des aktuellen Zeitraums das Unstake von $USDC beantragen, können ihre $USDC zu Beginn der nächsten Laufzeit abheben.

</details>

###
