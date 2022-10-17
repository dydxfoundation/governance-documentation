---
description: Eine Übersicht über den Liquidity Staking Pool
---

# Liquidity-Modul

`2,50 %` der ursprünglichen Tokenversorgung (`25 000 000 DYDX`) wurden an diejenigen Nutzer ausgeschüttet, die USDC im Liquidity Staking Pool eingelegt haben. Der Liquidity Staking Pool ist seit dem 29. September 2022 nicht mehr aktiv. Im Rahmen des [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md) [stimmte](https://dydx.community/dashboard/proposal/7) die dYdX-Community dafür, den Liquidity Staking Pool und den Borrowing Pool herunterzuschrauben, indem sie die sekündlichen Rewards für den Liquidity Staking Pool auf 0 heruntersetzte.\
\
Früher wurden DYDX an Nutzer ausgeschüttet, die USDC in den Liquidity Staking Pool einzahlten. Von der Gemeinschaft zugelassene Liquiditätsanbieter nutzten die abgesicherten USDC, um über das dYdX Layer 2 Protokoll Märkte zu schaffen und so die verfügbare Liquidität auf den Märkten zu erhöhen. Liquiditätsanbieter durften außerhalb des dYdX Layer 2 Protokolls keinen Gebrauch von geliehenen Mitteln machen.

## **Staking**-Übersicht

Für USDC, die im Liquidity Staking Pool eingesetzt werden, gibt es derzeit keine Vergütung.

Die 383 562 DYDX, die zuvor an USDC-Staker verteilt wurden, werden in der Rewards Treasury angesammelt und können von der dYdX-Community mit einer [Governance-Abstimmung](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verwendet werden.

## USDC Unstaking & Auszahlungen

Ein Staker muss mindestens `3 Tage` (**Blackout Window**) vor dem Zeitraum die Herausnahme der gestakten USDC beantragen,[** **](../start-here/epochs.md)um seine USDC nach Ablauf des gültigen Zeitraums auszahlen zu können. Wenn Staker die Auszahlung nicht beantragen, werden seine gestakten USDC in die nächste Epoche hinübergenommen.

Auszahlungen können während des **Blackout Window** nicht angefordert werden.

Im Rahmen des [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md), hat die dYdX-Community darüber [abgestimmt,](https://dydx.community/dashboard/proposal/7) die Länge des Blackout-Fensters von `14 Tage` auf `3 Tage` zu beschränken.

## Was ist stkUSDC?

USDC-Inhaber, die ihre USDC in den Liquidity Staking Pool einzahlen und einsetzen, erhalten eine tokenisierte Position (**stkUSDC**). stkUSDC wird ausgegeben, wenn ein Benutzer USDC einsetzt, und wird verbrannt, wenn ein Benutzer `drawStake` aufruft. In der gleichen Transaktion, in der USDC aus der Wallet eines Staker abgebucht werden, wird stkUSDC in die Wallet des Stakers übertragen; oder umgekehrt beim Unstaking.

Ein stkUSDC-Guthaben kann aktiv oder inaktiv sein. Aktive stkUSDC können als ERC-20 übertragen, aber nicht abgehoben werden. Inaktive stkUSDC können abgehoben, aber nicht übertragen werden. Beispielsweise kann ein Benutzer 100 aktive und 100 inaktive stkUSDC in seiner Wallet haben und das Guthaben des Benutzers zeigt 200 stkUSDC an, aber eine Übertragung wird rückgängig gemacht, wenn der Benutzer versucht, mehr als 100 stkUSDC zu übertragen.

Ein gestaktes Guthaben, für das der Staker vor dem Ende des Zeitraums eine Auszahlung beantragt hat, gilt als inaktiv und ist daher nicht übertragbar.

## FAQ

### Was ist das Blackout Window?

Ein Blackout Window ist eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten USDC beantragen können. Die Funktion`requestWithdrawal` kann nicht während eines Blackout Window aufgerufen werden, das anfänglich als die letzten `3 Tage`einer Laufzeit konfiguriert ist. Neue Epochen beginnen alle 28 Tage. Mit anderen Worten: Die Nutzer können bis zu `3 Tage `vor Ablauf einer bestimmten Laufzeit eine Abhebung für die nächste Laufzeit beantragen.

### Wie kann ich USDC aus dem Staking Pool auszahlen lassen? Wie lange dauert es?

Ein Staker muss mindestens `3 Tage` vor dem Ende einer Epoche beantragen, dass seine USDC freigegeben werden, damit er sie nach dem Ende der Epoche abheben kann. Wenn Staker die Auszahlung nicht beantragen, werden seine gestakten USDC in die nächste Epoche hinübergenommen.

Um USDC abzuheben, rufen Benutzer die Funktion `requestWithdrawal` auf, um die Abhebung von USDC für den nächsten Zeitraum anzufordern. Die Gelder der Benutzer verbleiben für die laufene Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

Im nächsten Zeitraum rufen Benutzer die Funktion `withdrawStake` auf, um inaktive USDC an eine bestimmte Adresse abzuheben. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion \`withdrawMaxStake\` aufrufen, um alle inaktiven Gelder abzuheben. Die Funktion `withdrawMaxStake` ist weniger gaseffizient als die Abfrage des Maximums über eth\_call und das Aufrufen von `withdrawStake()`.

Um USDC im Liquidity Pool zu entstaken, gehen Sie wie folgt vor:

* Gehen Sie zu [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Klicken Sie auf „**Anfordern**”, um das folgende Modal zu öffnen:

![Auszahlung wird angefordert](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Geben Sie den USDC-Betrag ein, den Sie zur Auszahlung aus dem Pool anfordern möchten, und klicken Sie auf „**Auszahlung anfordern**“. Sie müssen Gasgebühren zahlen, um USDC zu entstaken.
* Staker, die mindestens `3 Tage` (**Blackout Window**) vor Ende des aktuellen Zeitraums das Unstake von USDC beantragen, können ihre USDC zu Beginn der nächsten Laufzeit abheben.

### Welche Parameter kann die Governance ändern?

Die dYdX-Governance verpflichtet sich:

* Vergütung pro Sekunde für den Einsatz von USDC im Liquidity Staking Pool
* Hinzufügen neuer Kreditnehmer zum Staking Liquidity Pool und/oder Entfernen bestehender Kreditnehmer aus dem Staking Liquidity Pool
* Ändern der Zuteilungen von geliehenen USDC an zugelassene Kreditnehmer
  * Die Funktionen `setBorrowerAllocations` und `setBorrowingRestriction` werden aufgerufen, um die Zuteilungen bestimmter Kreditnehmer zu ändern. Sie können verwendet werden, um Kreditnehmer hinzuzufügen und zu entfernen. Erhöhungen treten in der nächsten Epoche in Kraft, aber Reduzierungen beschränken die Kreditaufnahme sofort. Diese Funktionen können während des Blackout Windows nicht aufgerufen werden.
* Die Laufzeitlänge und Blackout Window werden bei der Vertragsausgestaltung festgesetzt, können aber geändert werden
