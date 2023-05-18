---
description: Ein Überblick über den Safety Staking Pool
---

# Sicherheitsmodul

`2,50 %` der ursprünglichen Tokenversorgung (`25 000 000 DYDX`) werden an diejenigen Benutzer verteilt, welche DYDX in einem Safety Pool staken und somit das System absichern.

**Ziele**

* Ein dezentrales Finanzbündel zu schnüren, das im Falle von Zahlungsunfähigkeit oder anderen Zwischenfällen mit dem Protokoll zum Einsatz kommt.
* Anreize für DYDX-Inhaber zu schaffen, sich korrekt zu verhalten: DYDX-Inhaber tragen das Risiko von Verwässerungsereignissen in Form einer Letztsicherung und agieren als Risikokapitalgeber im System.

Im Sicherheitsmodul gestakte DYDX behalten ihre Vorschlags- und Stimmrechte sowie ihre Delegationsrechte bei.

Starten Sie das Staking auf [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*

## Überblick

Benutzersicherheit und -Schutz liegen seit Launch des Protokolls im zentralen Fokus. Aus diesem Grund werden DYDX an diejenigen Benutzer verteilt werden, welche DYDX im Safety Pool staken und somit eine zusätzliche Netzsicherheit für die Protokollbenutzer herstellen. Staker werden kontinuierlich DYDX erhalten, proportional zu ihrer Einlage in Bezug auf die Gesamtmenge an DYDX im Pool.

Der Safety Pool wird am 8. September 2021 um 15:00 UTC auf DYDX live gehen und damit für Transaktionen freigeschaltet werden.

## Auszahlungen

Staker müssen Kapitalauszahlungen mindestens `14 Tage` **(Blackout Window)** vor Ablauf der Epoche beantragen, um nach Ende der Epoche Gelder abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre gestakten DYDX in die nächste Epoche hinübergenommen.

## Risiken

Gestakte DYDX können im Falle einer Unterdeckung beschlagnahmt werden. Beschlagnahme geschieht im Ermessen der DYDX Governance und erfordert eine Abstimmung durch die Governance, um genehmigt zu werden.

Wie alle Teilnehmer in den unterschiedlichsten DeFi-Protokollen, unterliegen die Staker im Sicherheitsmodul dem Smart Contract-Risiko, wenn eine Schwachstelle im zugrunde liegenden Smart Contract auftreten sollte. Alle DYDX & Governance Smart Contracts wurden geprüft und streng getestet.

## Ereignisse einer Unterdeckung

Ob es sich tatsächlich um Unterdeckung handelt, unterliegt der Interpretation seitens der dYdX Governance, es müssen allerdings folgende Merkmale nachzuweisen sein:

* Exchange Zahlungsfähigkeit (z.B. Exchange wird aufgrund unrentabler Liquidationen unterbesichert)
* Attacken auf die Smart Contracts
* Sonstige Ereignisse, welche die dYdX Governance dafür in Betracht zieht, zu einer Unterdeckung geführt zu haben

Im Falle einer Unterdeckung, können Tokenbilanzen von Inhabern beschlagnahmt und zu einer anderen Adresse oder einem anderen Vertrag (von der dYdX Governance im Einzelfall festgesetzt) transferiert werden. Die dYdX Governance muss ein Short Timelock Proposal absegnen, um gestakte Token einziehen zu können. Nach einer Governance-Abstimmung über die Beschlagnahme gestakter DYDX Token, müssen eingezogene DYDX auf dem Markt versteigert werden, um somit gegen die erforderlichen Vermögenswerte eingetauscht zu werden, welche zur Minderung des entstandenen Defizits notwendig sind.

## FAQ

### Wie verdiene ich Staking Rewards?

Stakers können DYDX jederzeit in den Safety Pool einzahlen und sofort Rewards verdienen. DYDX Rewards werden kontinuierlich im Sekundentakt verdient, je nach Anteil eines jeden Stakers am Gesamtpool. Rewards können jederzeit beansprucht und ausgezahlt werden.

Aktive Gelder verdienen Rewards, solange sie aktiv bleiben. Dies bedeutet, dass diejenigen Gelder, die zur Auszahlung beantragt wurden, weiterhin Rewards verdienen, bis das Ende der Epoche erreicht ist. Dies wird im folgenden Beispiel aus dem [Liquidity Staking Pool](https://docs.dydx.community/dydx-governance/staking-pools/liquidity-staking-pool) demonstriert:

![](<../.gitbook/assets/image (65) (1).png>)

********Im obigen Szenario würde der Benutzer Rewards aus dem Zeitraum von Time0 bis Time2 verdienen, variierend je nach der tatsächlich gestakten Gesamtmenge im besagten Zeitraum. Wenn der Benutzer eine Auszahlung für nur einen Teil seines Guthabens beantragt, würde das verbleibende Guthaben weiterhin Rewards über **Time2** hinaus verdienen.

### Wie zahle ich DYDX in den Safety Pool ein und wie stake ich sie?

Um DYDX im Safety Pool zu staken, gehen Sie folgendermaßen vor:

* Gehen Sie zu [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Klicken Sie auf “**Stake**”
* Sie müssen DYDX aktivieren, wenn Sie zum ersten Mal einzahlen. Sie müssen dies nur einmal tun und die Gasgebühren nur einmal übernehmen.
* Geben Sie die Menge an DYDX ein, die Sie im Pool staken möchten.
* Klicken Sie auf “**Gelder staken**”. Um zu staken und Gelder wieder aus dem Staking herauszunehmen, müssen Sie Gasgebühren zahlen.

Gestakte Gelder sind nun aktiv und beginnen sofort damit, Rewards zu verdienen.

Um Gelder direkt auf dem Smart Contract einzuzahlen und zu staken, rufen die Benutzer die \`stake\` [Funktion](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) auf. Die Benutzer können auch im Namen einer anderen Adresse einzahlen und staken, indem sie die \`stakeFor\` [Funktion](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) aufrufen.

### Was ist stkDYDX?

Um zur Sicherheit des Protokolls beizutragen und Belohnungen zu erhalten, zahlen DYDX- Inhaber ihre Token im Sicherheitsmodul ein. Im Gegenzug erhalten sie eine tokenisierte Position (**stkDYDX**), die als ERC-20 abgehoben oder übertragen werden kann. Der **stkDYDX** Token verfügt über dieselben Vorschlags- und Abstimmungsrechte wie DYDX in der dYdX Governance.

### Was ist das Blackout Window?

Ein Blackout Window ist eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten Geldern beantragen können. Der Epochenplan wird für Auszahlungen eingehalten, um Vorhersehbarkeit und eine reguläre Abfolge der verfügbar gemachten Geldmittel im Pool zu gewährleisten. Ein Staker muss beantragen, wenn er Gelder aus dem Staking nehmen möchte, bevor das Blackout Window öffnet, um sein Guthaben nach Ende dieser Epoche abheben zu können. Wenn ein Staker die Auszahlung nicht beantragt, werden seine gestakten Gelder in die nächste Epoche hinübergenommen.

Das empfohlene Blackout Fenster für den Safety Pool beträgt `14 Tage`.

### Wie funktioniert die Bilanzbuchhaltung für Stakings?

Ein gestakter Saldo befindet sich in einem von zwei Zuständen:

* **Aktiv**: Verfügbar für die Kreditvergabe; Zum Verdienen von Staking Awards; können vom Staker nicht abgehoben werden.
* **Inaktiv**: Nicht zur Darlehenvergabe verfügbar; verdient keine Rewards; kann vom Staker ausgezahlt werden.

Ein Staker kann eine Kombination aus aktiven und inaktiven Salden haben. Die Kontostände werden Epoche für Epoche erfasst, wie im folgenden Beispiel veranschaulicht:

![](<../.gitbook/assets/image (34) (1) (3).png>)

Die folgenden Operationen betreffen die gestakten Salden wie folgt:

* **Einzahlung**: Sie erhöhen den aktiven Saldo
* **Auszahlung** **beantragen**: Verschieben Sie am Ende der laufenden Epoche einige aktive Gelder auf die inaktive Seite.
* **Auszahlung**: Sie verringern den inaktiven Saldo
* **Transfer**: Sie verschieben einige aktive Gelder zu einem anderen Staker.

Um zu aufzuschlüsseln, dass eine Bilanzänderung am Ende einer bestimmten Epoche terminiert werden kann, speichern wir jede Bilanz als eine Dreifelder-Tafel ab: currentEpoch, currentEpochBalance und nextEpochBalance.

### Wie kann ich Gelder aus dem Staking Pool auszahlen lassen? Wie lange dauert es?

Es wir ein Epochenplan für Auszahlungen eingehalten, um Vorhersehbarkeit und eine reguläre Abfolge der verfügbar gemachten Geldmittel im Pool zu gewährleisten. Ein Staker muss die Auszahlung von Geldern mindestens `14 Tage` vor Ablauf einer Epoche beantragen, um sein Gelder nach Ende dieser Epoche auszahlen zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre gestakten DYDX in die nächste Epoche hinübergenommen.

Um Gelder auszuzahlen, rufen die Benutzer die \`requestWithdrawal\` auf, um die Auszahlung der Gelder in der nächsten Epoche zu beantragen. Die Gelder der Benutzer verbleiben für die laufene Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

In der nächsten Epoche rufen die Benutzer die \`withdrawStake\` -Funktion auf, um inaktive Gelder an eine bestimmte Adresse auszuzahlen. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion \`withdrawMaxStake\` aufrufen, um alle inaktiven Gelder abzuheben. Beachten Sie, dass das Aufrufen der \`withdrawMaxStake\` Funktion weniger gaseffizient ist als die der max via eth\_call and calling \`withdrawStake()\`.

Um DYDX aus dem Liquidity Pool auszuzahlen, führen Sie die folgenden Schritte aus:

* Gehen Sie zu [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Klicken Sie auf “**Beantragen**” und geben Sie die Menge an DYDX ein, die Sie anfordern möchten, um diese aus dem Pool auszahlen zu lassen.
* Klicken Sie auf “**Auszahlung beantragen**”. Sie müssen Gasgebühren zahlen, um Gelder auszuzahlen.
* Staker, die die Auszahlung von DYDX mindestens 14 Tage vor dem Ende der laufenden Epoche beantragen, können ihre DYDX zu Beginn der nächsten Epoche auszahlen lassen.

### Welche Risiken bestehen für Staker des Safety Pools? Was passiert im Falle einer Unterdeckung?

Die Entscheidung eines Stakers, DYDX in den Safety Pool einzuschließen, setzt ihn dem Risiko einer Unterdeckung aus, was zur Beschlagnahme seiner gestakten DYDX Anteile nach dem Ermessen der DYDX Governance führen kann.

Alle Gelder im Vertrag, ob aktiv oder inaktiv, können von einer Beschlagnahme betroffen sein. Die Beschlagnahme findet im Contract mittels eines Updates des Wechselkurses zwischen DYDX und stkDYDX statt . Das bedeutet, dass im Falle einer Beschlagnahme, der Wechselkurs zwischen DYDX und stkDYDX von seinem Initialwert 1:1 abweichen wird. Beachten Sie, dass das Verdienen von Staking Rewards von den Beschlagnahmungen nicht betroffen ist.
