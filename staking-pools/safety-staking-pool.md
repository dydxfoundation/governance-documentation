---
description: Ein Überblick über den Safety Staking Pool
---

# Sicherheitsmodul

`0.5%` des Tokenangebots (`5.049.079 $DYDX) `wurde an Händler ausgeschüttet, die DYDX an einen Safety Pool zwecks Systemsicherung einsetzen. Anfangs wurden `2,50 %` des Tokenangebots (`25.000.000 DYDX`) an die Benutzer ausgeschüttet, die $DYDX im Sicherheitsmodul einsetzen. Das Sicherheitsmodul ist ab dem 28. November 2022 nicht mehr aktiv. In [DIP 17](https://dydx.community/dashboard/proposal/9) [stimmte](https://dydx.community/dashboard/proposal/7) die dYdX-Community dafür, das Sicherheitsmodul zu schließen, indem die Sicherheitsmodul-Rewards pro Sekunde auf 0 gestellt wurden.\


Zuvor wurde $DYDX an Benutzer verteilt, die $DYDX in das Sicherheitsmodul einsetzten. Das Sicherheitsmodul war ein dezentraler Fonds, der im Falle von Insolvenz oder anderen Problemen mit dem dYdX-Protokoll verwendet werden sollte.

Im Sicherheitsmodul gestakte $DYDX behalten ihre Vorschlags- und Stimmrechte sowie ihre Delegationsrechte bei.

## Überblick

Derzeit verdienen im Sicherheitsmodul gestakte $DYDX keine Prämien.

Die zuvor an $DYDX-Staker ausgeschütteten 383.562 $DYDX werden in der Prämienkasse angelegt und können von der dYdX-Community mit einer [Governance-Abstimmung](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) verwendet werden.

## DYDX-Unstaking und Auszahlungen

Staker müssen die Abhebung von Guthaben mindestens `3 Tage` **(Sperrfenster)**  vor dem Ende der Laufzeit beantragen, damit sie nach dem Ende der Laufzeit $DYDX abheben können. Wenn ein Staker die Auszahlung nicht beantragt, werden seine gestakten U$DYDX in die nächste Laufzeit überführt.

Auszahlungen können während des **Blackout Window** nicht angefordert werden.

In [DIP 17](https://dydx.community/dashboard/proposal/9) [stimmte](https://dydx.community/dashboard/proposal/7) die dYdX-Community dafür, die Länge des Blackout-Fensters von `14 Tagen` auf `3 Tage` zu reduzieren.



## FAQ

### Was ist das Blackout Window?

Ein Sperrfenster bezeichnet eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten DYDX beantragen können. Die Funktion`requestWithdrawal` kann nicht während eines Blackout Window aufgerufen werden, das anfänglich als die letzten `3 Tage`einer Laufzeit konfiguriert ist. Neue Epochen beginnen alle 28 Tage. Mit anderen Worten: Die Nutzer können bis zu `3 Tage `vor Ablauf einer bestimmten Laufzeit eine Abhebung für die nächste Laufzeit beantragen.

### Wie kann ich Gelder aus dem Staking Pool auszahlen lassen? Wie lange dauert es?

Der Epochenplan wird für Auszahlungen eingehalten, um Vorhersehbarkeit und eine reguläre Abfolge der verfügbar gemachten Geldmittel im Pool zu gewährleisten. Ein Staker muss die Auszahlung von Geldern mindestens `3 Tage` vor Ablauf einer Epoche beantragen, um seine Gelder nach Ende dieser Epoche abheben zu können. Wenn ein Staker die Auszahlung nicht beantragt, werden seine gestakten U$DYDX in die nächste Laufzeit überführt.

Um Gelder auszuzahlen, rufen die Benutzer die \`requestWithdrawal\` auf, um die Auszahlung der Gelder in der nächsten Epoche zu beantragen. Die Gelder der Benutzer verbleiben für die laufende Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

In der nächsten Epoche rufen die Benutzer die \`withdrawStake\` Funktion auf, um inaktive Gelder an eine bestimmte Adresse auszuzahlen. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion \`withdrawMaxStake\` aufrufen, um alle inaktiven Gelder abzuheben. Beachten Sie, dass das Aufrufen der \`withdrawMaxStake\` Funktion weniger gaseffizient ist als die der max via eth\_call and calling \`withdrawStake()\`.

Um aus dem Sicherheitsmodul $DYDX abzuheben, ist wie folgt vorzugehen:

* Gehen Sie zu [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Klicken Sie auf “**Beantragen**” und geben Sie die Menge an DYDX ein, die Sie anfordern möchten, um diese aus dem Pool auszahlen zu lassen.
* Klicken Sie auf “**Auszahlung beantragen**”. Sie müssen Gasgebühren zahlen, um Gelder auszuzahlen.
* Staker, die die Abhebung von DYDX mindestens `3 Tage` vor Ablauf der aktuellen Epoche beantragen, können ihre DYDX zu Beginn der nächsten Epoche abheben.

