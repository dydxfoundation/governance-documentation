---
description: Ein Überblick über den Safety Staking Pool
---

#

Zunächst wurden `2,50 %` des Token-Angebots (`25.000.000 $ethDYDX`) für die Verteilung an Benutzer zugewiesen, die ethDYDX in das Sicherheitsmodul einbinden. Das Sicherheitsmodul ist ab dem 28. November 2022 nicht mehr aktiv.

Zuvor wurde $ethDYDX an Benutzer verteilt, die $ethDYDX in das Sicherheitsmodul einsetzten. Das Sicherheitsmodul war ein dezentraler Fonds, der im Falle von Insolvenz oder anderen Problemen mit dem dYdX-Protokoll verwendet werden sollte.



## Überblick

Derzeit werden für $ethDYDX, die im Sicherheitsmodul eingesetzt werden, keine Prämien verdient.



## DYDX-Unstaking und Auszahlungen

Staker müssen Kapitalauszahlungen mindestens `3 Tage` **(Blackout Window)** vor Ablauf der Epoche beantragen, um nach Ende der Epoche ethDYDX abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre gestakten $ethDYDX in die nächste Epoche hinübergenommen.

Auszahlungen können während des **Blackout Window** nicht angefordert werden.

In [DIP 17](https://dydx.community/dashboard/proposal/9) [stimmte](https://dydx.community/dashboard/proposal/7) die dYdX-Community dafür, die Länge des Blackout-Fensters von `14 Tagen` auf `3 Tage` zu reduzieren.

## FAQ

<details>

<summary>Was ist das Blackout Window?</summary>

Ein Sperrfenster bezeichnet eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten DYDX beantragen können. Die Funktion`requestWithdrawal` kann nicht während eines Blackout Window aufgerufen werden, das anfänglich als die letzten `3 Tage`einer Laufzeit konfiguriert ist. Neue Epochen beginnen alle 28 Tage. Mit anderen Worten: Die Nutzer können bis zu `3 Tage `vor Ablauf einer bestimmten Laufzeit eine Abhebung für die nächste Laufzeit beantragen.

</details>

<details>

<summary>Wie kann ich Gelder aus dem Staking Pool auszahlen lassen? Wie lange dauert es?</summary>

Der Epochenplan wird für Auszahlungen eingehalten, um Vorhersehbarkeit und eine reguläre Abfolge der verfügbar gemachten Geldmittel im Pool zu gewährleisten. Ein Staker muss die Auszahlung von Geldern mindestens `3 Tage` vor Ablauf einer Epoche beantragen, um seine Gelder nach Ende dieser Epoche abheben zu können. Wenn die Staker die Auszahlung nicht beantragen, werden ihre gestakten $ethDYDX in die nächste Epoche hinübergenommen.

Um Gelder auszuzahlen, rufen die Benutzer die ``\`requestWithdrawal\``` auf, um die Auszahlung der Gelder in der nächsten Epoche zu beantragen. Die Gelder der Benutzer verbleiben für die laufene Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

In der nächsten Epoche rufen die Benutzer die ```withdrawStake``` Funktion auf, um inaktive Gelder an eine bestimmte Adresse auszuzahlen. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion ```withdrawMaxStake``` aufrufen, um alle inaktiven Gelder abzuheben. Beachten Sie, dass die Funktion ```withdrawMaxStake``` weniger gaseffizient ist als die Abfrage des Maximums über eth\_call and das Abrufen von ```withdrawStake()```.

Um $ethDYDX aus dem Sicherheitsmodul abzuheben, führen Sie folgende Schritte aus:

* Gehen Sie zu [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety)\*\*\*\*
* Klicken Sie auf „**Beantragen**“ und geben Sie die Menge an $ethDYDX ein, die Sie anfordern möchten, um diese aus dem Pool auszahlen zu lassen.
* Klicken Sie auf “**Auszahlung beantragen**”. Sie müssen Gasgebühren zahlen, um Gelder auszuzahlen.
* Staker, die die Abhebung von $ethDYDX mindestens `3 Tage` vor Ablauf der aktuellen Epoche beantragen, können ihre $ethDYDX zu Beginn der nächsten Epoche abheben.

</details>

