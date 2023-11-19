---
description: Eine Übersicht über den Liquidity Staking Pool
---

# Liquidity-Modul

`0,6 %` des Token-Angebots (`5.753.430 $ethDYDX)` wurden an die Nutzer ausgeschüttet, die $USDC in den Liquidity Staking Pool einsetzen. Zunächst wurden `2,50 %` des Token-Angebots (`25.000.000 $ethDYDX`) für die Verteilung an Benutzer zugewiesen, die $USDC in den Liquidity Staking Pool einbinden. Der Liquidity Staking Pool ist seit dem 29. September 2022 nicht mehr aktiv. In [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) [stimmte](https://dydx.community/dashboard/proposal/7) die dYdX-Gemeinschaft dafür, den Liquidity Staking- und Borrowing-Pool zu verringern, indem sie die Liquidity Staking Pool Prämien pro Sekunde mit 0\\, festsetzten
Bis dahin wurden $ethDYDX an Benutzer ausgeschüttet, die $USDC in den Liquidity Staking Pool einsetzten. Von der Gemeinschaft zugelassene Liquiditätsanbieter nutzten die eingesetzten $USDC, um Märkte auf dYdX v3 aufzubauen, wodurch die auf den Märkten verfügbare Liquidität erhöht wurde. Liquiditätsanbieter konnten keine Fremdmittel außerhalb von dYdX v3 verwenden.

## **Staking**-Übersicht

Für im Liquidity Staking Pool eingesetzte $USDC gibt es derzeit keine Vergütung.

Die 383 562 $ethDYDX, die zuvor an USDC-Staker verteilt wurden, werden in der Rewards Treasury angesammelt und können von der dYdX-Community mit einer [Governance-Abstimmung](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verwendet werden.

## USDC Unstaking & Auszahlungen

Ein Staker muss mindestens `3 Tage` (**Sperrfenster**) vor dem Ende der [**Laufzeit**](../start-here/epochs.md) die Abhebung von $USDC verlangen, um seine $USDC nach dem Ende der Laufzeit abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre eingesetzten $USDC in die nächste Phase überführt.

Auszahlungen können während des **Blackout Window** nicht angefordert werden.

Im Rahmen des [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), hat die dYdX-Community darüber [abgestimmt,](https://dydx.community/dashboard/proposal/7) die Länge des Blackout-Fensters von `14 Tage` auf `3 Tage` zu beschränken.

## Was ist stkUSDC?

USDC-Inhaber, die ihre $USDC in den Liquidity Staking Pool einzahlen und einsetzen, erhalten eine tokenisierte Position ($**stkUSDC**). $stkUSDC wird ausgegeben, wenn ein Benutzer USDC einsetzt, und wird verbrannt, wenn ein Benutzer `withdrawStake` aufruft. In der gleichen Transaktion, in der $USDC aus der Wallet eines Staker abgebucht werden, werden $stkUSDC in die Wallet des Stakers übertragen; oder umgekehrt beim Unstaking.

Ein $stkUSDC-Guthaben kann aktiv oder inaktiv sein. Aktive $stkUSDC können als ERC-20 übertragen, aber nicht ausgeschüttet werden. Inaktive $stkUSDC können abgehoben, aber nicht übertragen werden. Beispielsweise kann ein Benutzer 100 aktive und 100 inaktive $stkUSDC in seinem Wallet haben, und als Guthaben des Benutzers werden 200 $stkUSDC angezeigt. Eine Übertragung wird jedoch rückgängig gemacht, wenn der Benutzer versucht, mehr als 100 $stkUSDC zu übertragen.

Ein gestaktes Guthaben, für das der Staker vor dem Ende des Zeitraums eine Auszahlung beantragt hat, gilt als inaktiv und ist daher nicht übertragbar.

## FAQ

### Was ist ein Blackout Window?

Ein Sperrfenster beschreibt eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten $USDC beantragen können. Die Funktion`requestWithdrawal` kann nicht während eines Blackout Window aufgerufen werden, das anfänglich als die letzten `3 Tage`einer Laufzeit konfiguriert ist. Neue Epochen beginnen alle 28 Tage. Mit anderen Worten: Die Nutzer können bis zu `3 Tage `vor Ablauf einer bestimmten Laufzeit eine Abhebung für die nächste Laufzeit beantragen.

### Wie kann ich $USDC aus dem Staking Pool auszahlen lassen? Wie lange dauert es?

Ein Staker muss mindestens `3 Tage` vor dem Ende einer Laufzeit einen Antrag auf Entnahme von $USDC stellen, um seine $USDC nach dem Ende der Laufzeit abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre eingesetzten $USDC in die nächste Phase überführt.

Um $USDC abzuheben, rufen Benutzer `die Funktion Auszahl`ungsantrag auf, um die Abhebung von $USDC für den nächsten Zeitraum anzufordern. Die Gelder der Benutzer verbleiben für die laufende Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

In der nächsten Phase rufen die Benutzer die `Funktion Stake auszahlen` auf, wodurch inaktive $USDC an eine bestimmte Adresse abgehoben werden. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion \`withdrawMaxStake\` aufrufen, um alle inaktiven Gelder abzuheben. Die Funktion `withdrawMaxStake` ist weniger gaseffizient als die Abfrage des Maximums über eth\_call und das Aufrufen von `withdrawStake()`.

Um $USDC für den Liquiditätspool freizugeben, gehen Sie wie folgt vor:

* Gehen Sie zu [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Klicken Sie auf “**Anfordern**”, um das folgende Modal zu öffnen:

![Auszahlung wird angefordert](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Geben Sie den $USDC-Betrag ein, den Sie zur Auszahlung aus dem Pool anfordern möchten, und klicken Sie auf „**Auszahlung anfordern**“. Sie müssen Gasgebühren zahlen, um $USDC zu entstaken.
* Staker, die mindestens `3 Tage` (**Blackout Window**) vor Ende des aktuellen Zeitraums das Unstake von $USDC beantragen, können ihre $USDC zu Beginn der nächsten Laufzeit abheben.

### Welche Parameter kann die Governance ändern?

Die dYdX-Governance verpflichtet sich:

* Vergütung pro Sekunde für den Einsatz von $USDC im Liquidity Staking Pool
* Hinzufügen neuer Kreditnehmer zum Staking Liquidity Pool und/oder Entfernen bestehender Kreditnehmer aus dem Staking Liquidity Pool
* Ändern der Zuteilungen von geliehenen $USDC an zugelassene Kreditnehmer
  * Die Funktionen `setBorrowerAllocations` und `setBorrowingRestriction` werden aufgerufen, um die Allokationen bestimmter Kreditnehmer zu ändern. Sie können verwendet werden, um Kreditnehmer hinzuzufügen und zu entfernen. Erhöhungen treten in der nächsten Epoche in Kraft, aber Reduzierungen beschränken die Kreditaufnahme sofort. Diese Funktionen können während des Blackout Windows nicht aufgerufen werden.
* Die Laufzeitlänge und Blackout Window werden bei der Vertragsausgestaltung festgesetzt, können aber geändert werden
