---
description: Eine Übersicht über den Liquidity Staking Pool
---

# Liquidity-Modul

`2,50 %` des anfänglichen Token-Angebots (`25.000.000 DYDX`) werden an Benutzer verteilt, die USDC in den Liquiditäts-Staking-Pool einsetzen.

### Ziele

* Fördern Sie die Zuteilung von USDC für das Market-Making auf dem dYdX Layer 2 Protokoll.
* Weisen Sie erstklassigen Liquiditätsanbietern Kapital zu, um Spread, Tiefe und die Verfügbarkeit auf dYdX zu erhöhen.

Beginnen Sie mit dem Staken unter [**dydx.community/dashboard/pools/liquidity**](https://dydx.community/dashboard/pools/liquidity)**.**

## **Staking**-Übersicht

Liquidität ist eine Kernkomponente jeder erfolgreichen Börse. Zur Förderung von Netzeffekten und als Anreiz für professionelle Liquiditätsgeber wird DYDX an Nutzer verteilt, die USDC in den Liquiditätspool einzahlen. Von der Community zugelassene Liquiditätsgeber setzen die eingezahlten USDC ein, um auf den Märkten des dYdX Layer 2 Protokolls zu handeln und so die verfügbare Liquidität auf den Märkten zu erhöhen. Liquiditätsanbieter dürfen keine Fremdmittel außerhalb des dYdX-Ebene-2-Protokolls verwenden.

Staker erhalten DYDX-Belohnungen für das Staking von USDC. DYDX-Prämien werden kontinuierlich gemäß dem Anteil jedes Stakers am gesamten USDC im Pool verteilt.

[](https://dydx.foundation/revolving-credit-agreement)Jeder Staker und Liquiditätsgeber muss der Umlaufkreditvereinbarung zustimmen (Link hier). In der Vereinbarung werden die Bedingungen des Liquiditätspools im Klartext formuliert, so dass jeder Staker ein einklagbares Recht gegen jeden Liquiditätsgeber hat, der die geliehenen USDC nicht zurückzahlt. Die Vereinbarung besteht nur zwischen jedem Staker und jedem Liquiditätsanbieter. Die dYdX Foundation ist keine Vertragspartei und ihr erwachsen aus diesem Vertrag keine Rechte oder Pflichten.

## USDC Unstaking & Auszahlungen

Ein Staker muss mindestens `14 Tage` (**Blackout Window**\) vor dem [**Zeitraum**](../start-here/epochs.md) die Herausnahme der gestakten USDC beantragen, um seine USDC nach Ablauf des gültigen Zeitraums auszahlen zu können. Wenn Staker die Auszahlung nicht beantragen, werden seine gestakten USDC in die nächste Epoche hinübergenommen.

Auszahlungen können während des **Blackout Window** nicht angefordert werden.

## Staking-Risiken

Kreditnehmer aus dem Pool sind nicht verpflichtet, Sicherheiten zu stellen. Alle Kreditnehmer sind professionelle und seriöse Liquiditätsanbieter. Die Liste der zugelassenen Kreditnehmer und ihre Poolzuweisungen können von der Governance aktualisiert werden.

Wenn Nutzer USDC abheben wollen, kann das dem Kreditnehmer zugewiesene Guthaben für den nächsten Zeitraum unter den aktuell geliehenen Betrag fallen. In dieser Situation ist der Kreditnehmer dazu verpflichtet, die Differenz zwischen seinem geliehenen und zugeteilten Guthaben vor Ablauf des Zeitraums zurückzuzahlen.

Wenn ein Kreditnehmer es versäumt, einen offenen Saldo bis zum Ende des Zeitraums an den Pool zurückzuzahlen, gilt er als in Verzug und darf keine weiteren USDC leihen, bis die Schuld zurückgezahlt ist. Staker können USDC verlieren, falls ein Kreditnehmer eine Schuld nie zurückzahlt. Staker können einen Teil des eingesetzten USDC verlieren, wenn ein Marktmacher USDC verlieren würde und  den Liquidity Staking Pool nicht wieder auffüllen kann.

Staker tragen ein Smart-Vertrags-Risiko, wenn es eine Schwachstelle im zugrunde liegenden Smart-Vertrags-Code gibt. Alle DYDX & Governance Smart Contracts wurden geprüft und streng getestet.

Um das Risiko für Staker zu verringern, muss jeder Staker und Liquiditätsanbieter Vertragspartei des Umlaufkreditvertrags werden (Link [hier](https://dydx.foundation/revolving-credit-agreement)). Der Vertragsabschluss garantiert allerdings nicht, dass ein Liquiditätsanbieter alle geliehenen Beträge zurückzahlt, selbst dann nicht, wenn die Rechte des Kreditnehmers aus der Vereinbarung geltend gemacht werden.

## Zugelassene Kreditnehmer

Der Liquidity Staking Pool-Vertrag fungiert als zweiseitiges, unterbesichertes, zinsloses Liquiditätssystem.

Der Betrag, der entnommen werden kann, hängt von der prozentualen Zuteilung eines Kreditnehmers und der Gesamtzahl der im Pool eingesetzten USDC ab. Sowohl die prozentuale Zuteilung als auch der insgesamt verfügbare USDC können sich zu vordefinierten Zeiten ändern, die von `LS1EpochSchedule` angegeben werden. Der geliehene USDC darf nur auf dem Ebene-2-Protokoll von dYdX verwendet werden – dies wird über den `StarkProxy`-Vertrag durchgesetzt, der mit dem `StarkEx Perpetual Exchange`-Vertrag interagiert.

Zu den ursprünglich zugelassenen Liquiditätsanbietern gehören `Wintermute`, `Amber Group`, `Wootrade (Kronos)`, `Sixtant` und `DAT Trading`, die aktiv Market-Making auf dem dYdX-Ebene-2-Protokoll betrieben haben.

| Vorbewilligte Kreditnehmer | Anteil an Erstallokationen | Ethereum-Adresse | StarkProxy | Details zu Liquidity Providern |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wintermute | 25 % | [0x4f3a120E72C76c22ae802D129F599BFDbc31cb81](https://etherscan.io/address/0x4f3a120E72C76c22ae802D129F599BFDbc31cb81) | [0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6](https://etherscan.io/address/0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6) | [https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/](https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/) |
| Amber Group | 25 % | [0x39Ad99E33ab7Ee85818741dD6076112188bc2611](https://etherscan.io/address/0x39Ad99E33ab7Ee85818741dD6076112188bc2611) | [0x3e6E9EFb0A677a24F47093a22044dc5451A028cF](https://etherscan.io/address/0x3e6E9EFb0A677a24F47093a22044dc5451A028cF) | [https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/](https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/) |
| WOO Network (Kronos) | 20 % | [0x38d981c3c42b2ec8e9572f560552407d0f1279fb](https://etherscan.io/address/0x38d981c3c42b2ec8e9572f560552407d0f1279fb) | [0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06](https://etherscan.io/address/0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06) | [https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/](https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/) |
| Sixtant | 20 % | [0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c](https://etherscan.io/address/0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c) | [0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2](https://etherscan.io/address/0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2) | [https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/](https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/) |
| DAT Trading | 10 % | [0x83E8fb8f4DAE0f42d68FdbBf85d4191a5e6f92F8](https://etherscan.io/address/0x83e8fb8f4dae0f42d68fdbbf85d4191a5e6f92f8) | [0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874](https://etherscan.io/address/0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874) | [https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/](https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/) |

## Erfassung von gestakten Salden

Ein gestakter Saldo befindet sich in einem von zwei Zuständen:

* **Aktiv**: Verfügbar für die Kreditvergabe; zum Verdienen von Staking-Prämien; können vom Staker nicht abgehoben werden.
* **Inaktiv**: Nicht zur Darlehenvergabe verfügbar; verdient keine Rewards; kann vom Staker ausgezahlt werden.

Ein Staker kann eine Kombination aus aktiven und inaktiven Salden haben. USDC wird wie in dem folgenden Beispiel gezeigt, Schritt für Schritt berücksichtigt:

![Bilanzierung des Staked-Guthabens](<../.gitbook/assets/image (34) (1) (2).png>)

Die folgenden Operationen betreffen die gestakten Salden wie folgt:

* **Einzahlung**: Sie erhöhen den aktiven Saldo
* **Auszahlung anfordern**: Bringen Sie am Ende des aktuellen Zeitraums einige aktive USDC in einen inaktiven Status.
* **Auszahlung**: Sie verringern den inaktiven Saldo
* **Transfer**: Verschieben Sie einige aktive USDC auf einen anderen Staker.

Um die Tatsache zu verschlüsseln, dass sich ein Saldo am Ende eines bestimmten Zeitraums ändern kann, wird in einer Struktur aus drei Feldern gespeichert: Inaktive Benutzersalden bedienen sich auch des shortfallCounter-Feldes

### Was ist stkUSDC?

USDC-Inhaber, die ihre USDC in den Liquidity Staking Pool einzahlen und einsetzen, erhalten eine tokenisierte Position (**stkUSDC**). stkUSDC wird ausgegeben, wenn ein Benutzer USDC einsetzt, und wird verbrannt, wenn ein Benutzer `drawStake` aufruft. In der gleichen Transaktion, in der USDC aus der Wallet eines Staker abgebucht werden, wird stkUSDC in die Wallet des Stakers übertragen; oder umgekehrt beim Unstaking.

Ein stkUSDC-Guthaben kann aktiv oder inaktiv sein. Aktive stkUSDC können als ERC-20 übertragen, aber nicht abgehoben werden. Inaktive stkUSDC können abgehoben, aber nicht übertragen werden. Beispielsweise kann ein Benutzer 100 aktive und 100 inaktive stkUSDC in seiner Wallet haben und das Guthaben des Benutzers zeigt 200 stkUSDC an, aber eine Übertragung wird rückgängig gemacht, wenn der Benutzer versucht, mehr als 100 stkUSDC zu übertragen.

Ein gestaktes Guthaben, für das der Staker vor dem Ende des Zeitraums eine Auszahlung beantragt hat, gilt als inaktiv und ist daher nicht übertragbar.

## **Staker** FAQ

### Wie verdiene ich Staking Rewards?

Staker können jederzeit USDC in den Liquidity Staking Pool einzahlen und sofort mit dem Verdienen von Rewards beginnen. DYDX Rewards werden kontinuierlich im Sekundentakt verdient, je nach Anteil eines jeden Stakers am Gesamtpool. Rewards können jederzeit beansprucht und ausgezahlt werden.

Der USDC-Einsatz bringt für den Zeitraum, in dem er aktiv bleibt, Prämien ein Das bedeutet, dass nach der Beantragung einer Abhebung von USDC weiterhin Prämien für diese USDC bis zum Ende der Laufzeit gezahlt werden. Zum Beispiel:

![Prämienabrechnung](<../.gitbook/assets/image (65) (1) (1).png>)

********Im obigen Szenario würde der Benutzer Rewards aus dem Zeitraum von Time0 bis Time2 verdienen, variierend je nach der tatsächlich gestakten Gesamtmenge im besagten Zeitraum. Wenn der Nutzer nur einen Teil seines Guthabens abheben möchte, würde das verbleibende Guthaben über **Time2** mit Prämien bedacht werden.

### Wie kann ich USDC einzahlen und im Liquidity Pool staken?

Führen Sie die folgenden Schritte aus, um USDC in den Liquidity Pool einzubinden:

* Gehen Sie zu [https://dydx.community/dashboard/pools/liquidity](https://dydx.community/dashboard/pools/liquidity)
* Klicken Sie auf “Stake“
* Sie müssen USDC vorerst aktivieren, wenn Sie zum ersten Mal einzahlen. Sie müssen dies nur einmal tun und die Gasgebühren nur einmal übernehmen.
* Geben Sie die Menge an USDC ein, die Sie im Pool staken möchten.
* Klicken Sie auf „Stake Funds“ – Sie müssen Gasgebühren zahlen, um zu staken, eine Auszahlung zu beantragen und USDC abzuheben.

![](<../.gitbook/assets/image (57).png>)

Gestakte USDC ist jetzt aktiv und werden sofort bei Prämien berücksichtigt.

Um USDC direkt auf den Smart Contract einzuzahlen und zu `stake`n, rufen Benutzer die Stake-Funktion auf. Benutzer können USDC auch im Namen einer anderen Adresse einzahlen und einsetzen, indem sie die Funktion `stakeFor` aufrufen. Selbst wenn Sie USDC direkt auf den Smart Contract setzen, wird davon ausgegangen, dass Sie über die Umlaufkreditvereinbarung informiert und überprüft wurden (Link [hier](https://dydx.foundation/revolving-credit-agreement)).

### Was ist das Blackout Window?

Ein Blackout Window ist eine Zeitspanne, in der die Benutzer keine Auszahlungen von gestakten USDC beantragen können. Die Funktion `requestWithdrawal` kann nicht während eines Blackout Window aufgerufen werden, das anfänglich als die letzten `14 Tage` einer Laufzeit konfiguriert ist. Neue Epochen beginnen alle 28 Tage. Mit anderen Worten: Die Nutzer können bis zu `14 Tage` vor Ablauf einer bestimmten Laufzeit eine Abhebung für die nächste Laufzeit beantragen.

### Wie kann ich USDC aus dem Staking Pool auszahlen lassen? Wie lange dauert es?

Es wird ein Zeitplan wird für Auszahlungen eingehalten, um Vorhersehbarkeit und eine reguläre Abfolge der verfügbar gemachten USDC im Pool zu gewährleisten. Ein Staker muss mindestens `14 Tage` vor der Ablauffriste das Unstaken von USDC beantragen, um die USDC des Stakers nach dem Ablauf dieses Zeitraums abheben zu können. Wenn Staker die Auszahlung nicht beantragen, werden seine gestakten USDC in die nächste Epoche hinübergenommen.

Um USDC abzuheben, rufen Benutzer die Funktion `requestWithdrawal` auf, um die Abhebung von USDC für den nächsten Zeitraum anzufordern. Die Gelder der Benutzer verbleiben für die laufene Epoche im Staking und können in dieser Zeit nicht abgebucht werden. Startet die nächste Epoche, werden die Gelder „inaktiv“ und stehen für die Auszahlung bereit.

Im nächsten Zeitraum rufen Benutzer die Funktion `withdrawStake` auf, um inaktive USDC an eine bestimmte Adresse abzuheben. Die Benutzer können die Menge der inaktiven Gelder auswählen, die sie auszahlen möchten, oder die Funktion \`withdrawMaxStake\` aufrufen, um alle inaktiven Gelder abzuheben. Die Funktion `withdrawMaxStake` ist weniger gaseffizient als die Abfrage des Maximums über eth\_call und das Aufrufen von `withdrawStake()`.

Um USDC im Liquidity Pool zu entstaken, gehen Sie wie folgt vor:

* Gehen Sie zu [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity)\*\*\*\*
* Klicken Sie auf „**Anfordern**”, um das folgende Modal zu öffnen:

![Auszahlung wird angefordert](<../.gitbook/assets/image (68) (1).png>)

* Geben Sie den USDC-Betrag ein, den Sie zur Auszahlung aus dem Pool anfordern möchten, und klicken Sie auf „**Auszahlung anfordern**“. Sie müssen Gasgebühren zahlen, um USDC zu entstaken.
* Staker, die mindestens 14 Tage (**Blackout Window**) vor Ende des aktuellen Zeitraums das Unstake von USDC beantragen, können ihre USDC zu Beginn der nächsten Laufzeit abheben.

### Welche Parameter kann die Governance ändern?

Die dYdX-Governance verpflichtet sich:

* Die gebotene Sorgfalt bei bestehenden Kreditnehmern walten zu lassen
* Hinzufügen neuer Kreditnehmer zum Staking Liquidity Pool und/oder Entfernen bestehender Kreditnehmer aus dem Staking Liquidity Pool
* Ändern der Zuteilungen von geliehenen USDC an zugelassene Kreditnehmer
   * Die Funktionen `setBorrowerAllocations` und `setBorrowingRestriction` werden aufgerufen, um die Zuteilungen bestimmter Kreditnehmer zu ändern. Sie können verwendet werden, um Kreditnehmer hinzuzufügen und zu entfernen. Erhöhungen treten in der nächsten Epoche in Kraft, aber Reduzierungen beschränken die Kreditaufnahme sofort. Diese Funktionen können während des Blackout Windows nicht aufgerufen werden.
* Die Laufzeitlänge und Blackout Window werden bei der Vertragsausgestaltung festgesetzt, können aber geändert werden

## **FAQ der Kreditnehmer**

### **Kreditaufnahme**

Gestakte USDC kommen in einen Pool, der zugelassenen Kreditnehmern zugeteilt wird. Jeder Kreditnehmer hat einen von der Governance kontrollierten Zuteilungssatz und kann Kredite bis zu dieser Quote aufnehmen. Das Unstaking unterliegt einer „Laufzeit“ – entstakte USDC können nur zu Beginn einer Laufzeit abgehoben (das heißt „inaktiv“) werden.

Zur Auszahlung angeforderte USDC müssen von den Kreditnehmern vor dem Laufzeitende zurückgegeben werden. Im Falle einer unzureichenden Deckung wird der Betrag zu einem „Schuldensaldo“ und der Staking-Vertrag wird wieder stabilisiert. Der säumige Kreditnehmer muss den Schuldensaldo zurückzahlen und wird von der Kreditaufnahme ausgeschlossen, bis er durch die Governance wieder aufgenommen wird.

Kreditnehmer unterliegen allen Bedingungen des Umlaufkreditvertrags (Link [hier](https://dydx.foundation/revolving-credit-agreement)).

### **StarkProxy Features**

#### **Auto-Pay**

Kreditnehmer können `autoPayOrBorrow()` verwenden, um die maximale Nutzung der zugewiesenen USDC und die rechtzeitige Rückzahlung der angeforderten Auszahlungen sicherzustellen. Die Funktion muss für einen Kreditnehmer nur einmal pro Laufzeit erfolgreich aufgerufen werden, um sicherzustellen, dass er seinen Verantwortlichkeiten nachkommt.

Die Funktion wird zurückgesetzt, wenn sie in der ersten Laufzeithälfte aufgerufen wird, da diese außerhalb des Blackout Window liegt. Es wird zurückgesetzt, wenn der `StarkProxy`-Vertrag nicht über genügend USDC für die Rückzahlung verfügt. In diesem Fall müssen USDC hinzugefügt oder von der Börse zurückgezogen werden, bevor `autoPayOrBorrow()` aufgerufen wird.

#### **Im Besitz des Kreditnehmers befindliche USDC**

Ein Kreditnehmer kann seinen eigenen USDC sicher beim `StarkProxy` hinterlegen und ihn auf dem dYdX-Ebene-2-Protokoll im selben Konto wie den geliehenen USDC verwenden. USDC kann in einer der folgenden Situationen von `StarkProxy` abgezogen werden:

* USDC, die im Rahmen des `StarkProxy`-Vertrags über das geliehene Guthaben hinaus gehalten werden, können jederzeit abgehoben werden.
* Die Governance kann eine Auszahlung eines bestimmten Betrags genehmigen.
   * Hinweis: Dies kann verwendet werden, um dem Kreditnehmer zu ermöglichen, Gewinne abzuheben, ohne die meisten USDC vom dYdX-Ebene-2-Protokoll entfernen zu müssen.

#### **Rollen des Kreditnehmers**

Der `StarkProxy`-Vertrag unterstützt die folgenden vom Kreditnehmer kontrollierten Rollen. Diese können abhängig von den Sicherheitsbedürfnissen des Kreditnehmers von einer einzigen Adresse oder separaten Adressen gehalten werden. Jede Rolle kann von einer beliebigen Anzahl von Adressen gehalten werden.

Eigentümer

* Gewähren oder entziehen Sie die Rolle des Delegierungsadministrators.
* Fügen Sie zulässige Empfänger für USDC hinzu, die von `StarkProxy` zurückgezogen wurden, oder entfernen Sie sie.
* Fügen Sie zulässige STARK-Schlüssel zur Verwendung auf dem dYdX-Ebene-2-Protokoll hinzu oder entfernen Sie sie.
* Legen Sie ERC20-Freigaben für die Verträge `LiquidityStakingV1` und `StarkPerpetual` fest.
* Rufen Sie `forcedWithdrawalRequest()` oder `forcedTradeRequest()` für den Vertrag `StarkEx Perpetual Exchange` auf.

Delegationsadministrator

* Erteilen oder entziehen Sie die Rollen des Kreditnehmers, Börsenbetreibers und des Verfügungsberechtigten.

Kreditnehmer

* Rufen Sie `autoPayOrBorrow()`, `borrow()`, `repay()` und `repayDebt()` für den Liquidity Staking-Vertrag auf.

Börsenbetreiber

* Rufen Sie `registerUserOnExchange()`, `depositToExchange()` und `pullFromExchange()` für den `StarkEx Perpetual Exchange`-Vertrag auf.

Verfügungsberechtigter

* Führen Sie eine gültige externe Auszahlung (siehe oben) von `StarkProxy` an einen zulässigen Empfänger durch.

#### **Einschränkungen**

Layer-2-Übertragungen auf dem dYdX-Ebene-2-Protokoll sind für Konten deaktiviert, die von einem `StarkProxy` kontrolliert werden.

#### **Wächterfunktion**

Die Wächterrolle wird von der dYdX-Governance kontrolliert. Seine Aufgabe besteht darin, die Sicherheit geliehener USDC zu gewährleisten und deren Rückgabe an Staker zu ermöglichen, falls der private Schlüssel eines Kreditnehmers verloren geht oder missbraucht wird.

Der Wächter kann jederzeit (vorbehaltlich der Sperrfrist) folgende Maßnahmen ergreifen:

* Begrenzung der Kreditaufnahme und der Einzahlung von geliehenen USDC auf die Börse.
* Rückzahlung eines geliehenen Guthabens mit USDC im `StarkProxy`-Vertrag.
* Rückzahlung eines Schuldensaldos mit USDC im `StarkProxy`-Vertrag.
* Rücktritt vom StarkEx-Vertrag zum `StarkProxy`-Vertrag (zum Beispiel als zweiter Schritt eines langsamen Ausstiegs aus der Börse).
* Stornieren einer erzwungenen Handelsanfrage, die vom Kreditnehmer initiiert wurde.
* Dem Kreditnehmer erlauben, einen Betrag aus dem `StarkProxy`-Vertrag abzuheben, wobei die Kontostandsprüfung umgangen wird.
* Aktualisieren des Smart Contract.

**Der Wächter kann folgende Maßnahmen ergreifen, wenn der Kreditnehmer ausstehende Schulden hat (vorbehaltlich einer Frist):**

* Eine erzwungene Auszahlung aus dem dYdX-Layer-2-Protokoll durchführen.
* Einen erzwungenen Handel (nur reduzieren) auf dem dYdX-Layer-2-Protokoll durchführen.

## Häufig gestellte Fragen zu Staking-Risiken

### Was sind die Risiken eines Stakings im Liquidity Staking Pool? Was passiert, wenn ein Kreditnehmer geliehene Mittel nicht zurückzahlt?

Ein System für unbesicherte Kreditaufnahme erfordert einen viel höheren Vertrauensstandard, den ein Kreditnehmer erfüllen muss. Liquiditätsanbieter, die aus dem Liquidity Staking Pool leihen, können geliehene Mittel nicht außerhalb des Liquidity Staking-Systems und des dYdX-Layer-2-Protokolls bewegen. Dennoch könnten gestakte USDC verloren gehen, wenn ein Liquiditätsanbieter den Fondshandel verlieren würde und nicht in der Lage wäre, seine geliehenen Zuteilungen durch externe Finanzierungsquellen aufzufüllen.

In diesem Fall können inaktive Gelder im Falle eines Fehlbetrags, wenn ein Kreditnehmer mit der Rückzahlung angeforderter Gelder verspätet ist, vergemeinschaftet werden, wie unten dargelegt. Im Falle eines Zahlungsausfalls bei geliehenen Mitteln droht einem säumigen Kreditnehmer ein erheblicher Reputationsschaden.

Obwohl jeder Staker und jeder Kreditnehmer Partei desvUmlaufkreditvertrags (Link [hier](https://dydx.foundation/revolving-credit-agreement)) ist, bietet dieser Vertrag keine Garantie dafür, dass Kreditnehmer ihre Verpflichtungen zurückzahlen werden.

### Wie behält der Vertrag die Zahlungsfähigkeit?

Zu jedem Zeitpunkt wird sich der Vertrag in einem der folgenden Zustände befinden, je nach Verhältnis der gestakten und geliehenen Salden:

![Vertragszahlungsfähigkeit](<../.gitbook/assets/image (41).png>)

Der Vertrag soll **insolvent** sein:

* wenn das geliehene Gesamtguthaben größer ist als das aktive Gesamtguthaben;
* oder gleichwertig, wenn das gesamte inaktive Guthaben größer ist als das gesamte nicht ausgeliehene Guthaben;
* oder gleichwertig, wenn das gesamte auszahlbare Guthaben größer ist als das USDC-Guthaben des Vertrags.

Andernfalls gilt der Vertrag als **solvent**.

Da die Kreditaufnahme auf den einem Kreditnehmer zugeteilten Anteil an aktiven USDC begrenzt ist und der inaktive Saldo nur zwischen den Laufzeiten zunehmen kann, kann der Vertrag typischerweise nur während der Übergänge zwischen den Laufzeiten von einem zahlungsfähigen in einen zahlungsunfähigen Zustand übergehen.

Wenn der Vertrag zu Beginn einer neuen Laufzeit insolvent ist, ist es wichtig, ihn so schnell wie möglich wieder zu stabilisieren. Die Solvenz wird über einen Mechanismus namens „Schuldenbuchhaltung“ wiederhergestellt. Jedes Mal, wenn der Vertrag insolvent ist, kann die Funktion `markDebt()` von jedem aufgerufen werden, indem eine Liste von Kreditnehmern angegeben wird, die ihre Zuteilungen überschritten haben. Der Betrag, um den das geliehene Guthaben eines Kreditnehmers seine Zuteilungsquote übersteigt, wird als Fehlbetrag des Kreditnehmers bezeichnet.

Wenn `markDebt()` aufgerufen wird, wird der Fehlbetrag jedes Kreditnehmers aus seinem geliehenen Saldo in einen Saldo verschoben, der als Schuldensaldo bezeichnet wird. Gleichzeitig wird der Gesamtbetrag dieser Fehlbeträge aus den inaktiven Guthaben der Staker entnommen und als Zahlungseingänge der Staker ausgezahlt. Das inaktive Guthaben jedes Stakers wird gekürzt und jeder Staker erhält einen entsprechenden Betrag in Form von Schulden. Auf diese Weise wird der Verlust aus der Insolvenz (anteilig) auf alle Staker mit inaktiven Guthaben aufgeteilt.

Dieser Vorgang wird im Folgenden dargestellt:

![Standard](<../.gitbook/assets/image (46).png>)

### Wofür steht „Schulden"?

Bei einem Ausfall des Kreditnehmers wird der Fehlbetrag (bis zu 100 % der inaktiven Salden) von einem inaktiven Saldo in eine Schuld umgewandelt (vergemeinschafteter Verlust unter Inhabern von inaktiven Salden). Die Schulden eines Stakers berechtigen den Staker nicht, aus dem Pool der gestakten USDC abzuheben– sie müssen ausdrücklich in Form von Schuldenrückzahlungen zurückgezahlt werden.

Die Schuld entspricht einer Bestätigung für USDC, die zu einem späteren Zeitpunkt gegen USDC eingelöst werden kann, entweder wenn der Kreditnehmer seine Schulden zurückzahlt oder durch eine andere von der Unternehmensführung festgelegte Art der Rückgewinnung.

### Welche Ressourcen stehen Stakern zur Verfügung, wenn ein Kreditnehmer ausfällt?

Staker und Kreditnehmer sind Parteien des Umlaufkreditvertrags (Link [hier](https://dydx.foundation/revolving-credit-agreement)), der eine durchsetzbare Vereinbarung zwischen jedem Staker und jedem Kreditnehmer erzeugt. Darüber hinaus ist der Smart Contract für den Liquidity Staking Pool so konzipiert, dass er Stakern einen Regress auf Kreditnehmer gewährt, obwohl er die Rückzahlung nicht garantieren kann.

Wenn `markDebt\()` auf einem Kreditnehmer aktiviert wird, verliert dieser das Recht, weitere Gelder aus dem Vertrag zu leihen. Dieses Recht kann durch die Governance wiederhergestellt werden.

Sobald Schulden „markiert“ wurden, werden sie aus dem Hauptbuchhaltungssystem entfernt und können von Stakern auf verschiedene Weise eingezogen werden. Wenn der verschuldete Kreditnehmer die Schulden zurückzahlt (oder wenn eine andere Partei, wie zum Beispiel die Verwaltung, sie in seinem Namen zurückzahlt), können die Staker, denen die Schulden geschuldet wurden, die Gelder nach dem Prinzip „Wer zuerst kommt, mahlt zuerst“ zurückerhalten. Flexiblere Lösungen können über die „Debt Operator“-Schnittstelle auf dem Smart Contract implementiert werden.

Was in der Praxis passiert, nachdem Staker Schulden erhalten, hängt vom Kontext ab. Wenn es sich um einen ehrlichen Fehler eines zugelassenen Kreditnehmers handelt, können Staker damit rechnen, dass sie schnell und vollständig ausbezahlt werden. Wenn USDC-Gelder verloren gegangen sind, kann die Governance eine Teilrückzahlung an die betroffenen Staker veranlassen. Wenn die Lösung ungewiss ist, kann die Governance entscheiden, betroffenen Stakern eine ERC20-Quittung auszustellen, die ihnen sofortige Liquidität ermöglicht, während sie auf eine Lösung warten. Wenn dies als angemessen erachtet wird, könnte die Governance entscheiden, Zinszahlungen an die Inhaber von Zertifikaten zu leisten, bis eine Lösung erreicht ist.

Alle diese Fälle werden grundsätzlich durch den Staking-Vertrag unterstützt, aber die angemessene Reaktion muss von der dYdX-Governance entschieden und ausgeführt werden. Je nach Situation kann es erforderlich sein, einen peripheren Smart Contract aufzusetzen und einzusetzen.
