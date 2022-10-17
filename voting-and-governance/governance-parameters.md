---
description: Überblick über die Governance-Parameter.
---

# Parameter

Sobald die Governance gelauncht ist, werden DYDX-Inhaber sofort und unwiderruflich Kontrolle haben über:

* Allokation der Community Treasury
* Neue Token-Listings auf dem Protokoll
* Risikoparameter für das Protokoll
* Kapitalallokationen an Marktmacher im Liquidity Staking Pool
* Hinzufügen neuer Marktmacher zum Liquidity Staking Pool
* Bestimmung der Auszahlungen aus dem Safety Staking Pool im Falle von Verlusten
* Änderung aller zum Zeitpunkt des Launches vorhandenen Prämien und Pools
* Die Governance Verträge als solche

dYdX Governance hat Kontrolle über die Parameter der folgenden Verträge:

* [Timelock](https://github.com/dydxfoundation/governance-docs/tree/28153eacbdaafb32078630fafa7ad64f111ac9ab/voting-and-governance-process/parameters.md#timelock-parameters)
* Priority Timelock
* Gouverneur
* DYDX Token
* Treasury
* Merkle Distributor
* Liquidity Staking
* Sicherheitsmodul
* Stark Proxy
* Stark Perpetual

## Timelock-Parameter

![](../.gitbook/assets/1-initial-timelock-parameters.png)

## Gouverneur-Parameter

| Parameter | Beschreibung | Wert |
| ----------------- | ----------------------------------------------------------------------------- | -------------- |
| Abstimmungsverzögerung | Verzögerung (in Blöcken) zwischen der Erstellung von Vorschlägen und Abstimmung über den Vorschlag | 6.570 Blöcke |
| Executor-Rolle hinzufügen | Adresse, die neue Executors hinzufügen kann | Short Timelock |
| Rolle der Eigentümer | Kann Strategie / Abstimmungsverzögerung abändern / Executoren die Erlaubnis entziehen + verfügt über andere Rollen | Long Timelock |

## DYDX Token

| Parameter | Beschreibung | Wert |
| --------- | ------------------------------------------- | -------------- |
| Eigentümer | Kann DYDX Token nach Mint-Beschränkung minten | Short Timelock |

## Parameter der Prämien-Treasury

| Parameter | Beschreibung | Wert |
| ----------- | ------------------------------------------------------ | -------------- |
| Eigentümer | Kann jeden von der Treasury gehaltenen Token genehmigen oder übertragen | Short Timelock |
| Proxy-Admin | Kann den Vertrag aktualisieren | Short Timelock |

##

## Parameter der Community Treasury

| Parameter | Beschreibung | Wert |
| ----------- | ------------------------------------------------------ | -------------- |
| Eigentümer | Kann jeden von der Treasury gehaltenen Token genehmigen oder übertragen | Short Timelock |
| Proxy-Admin | Kann den Vertrag aktualisieren | Short Timelock |

##

## Merkle Distributor

| Parameter | Beschreibung | Wert |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------- |
| Rolle der Eigentümer | Kann die Prämien Oracle-Adresse aktualisieren, den IPNS Name aktualisieren und ist Administrator aller Rollen | Short Timelock |
| Rolle des Config Updaters | Kann Prämien-Parameter festlegen, den Epochenplan ändern oder den IPFS-Aktualisierungszeitraum ändern | Short Timelock |
| Rolle des Pausierers | Kann Updates an der Merkle Root pausieren | Merkle-pauser Timelock |
| Rolle des Entpausers | Kann Pausierungen der Aktualisierungen an der Merkle Root aufheben | Short Timelock |
| Rolle des Claim Operators | Kann Prämien im Namen eines Benutzers abholen | Anspruchsvollmacht |
| Intervall | Länge einer Epoche | 28 Tage |
| Offset | Start der Epoche Null | 3. August 15:00 UTC 2021 |
| IPNS Name | IPNS Name, unter welchem Prämiendaten veröffentlicht werden | rewards-data.dydx.foundation |
| IPFS Aktualisierungszeitraum | Zeitraum nach Ablauf einer Epoche, nach welcher die Exchange-Statistiken der neuen Epoche auf IPFS über den IPNS Namen verfügbar sein sollten | 3 Minuten |
| Proxy-Admin | Kann den Vertrag aktualisieren | Short Timelock |

##

## Liquidity Staking

| Parameter | Beschreibung | Wert |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Rolle der Eigentümer | Admin aller Roller | Short Timelock |
| Rolle des Epochen-Parameter | Kann Epochen-Parameter wie beispielsweise das Intervall, Offset und Blackout Window einstellen | Short Timelock |
| Rolle des Prämien-Bemessers | Kann die Rate der Prämien bemessen | Short Timelock |
| Rolle des Kreditnehmer-Admins | Kann Allokationen an Kreditnehmer bestimmen und Kreditnehmer zum Darlehen zulassen oder einschränken | Short Timelock |
| Rolle des Claim Operators | Kann Prämien im Namen eines Benutzers abholen | Anspruchsvollmacht |
| Rolle des Stake Operators | Kann in gestakte Benutzerguthaben (z.B. Auszahlungen durchführen) im Namen eines Benutzers eingreifen | Short Timelock |
| Rolle des Darlehen-Operators | Kann Kreditschulden senken und Staker-Schulden absenken | Short Timelock |
| Intervall | Länge einer Epoche | 28 Tage |
| Offset | Start der Epoche Null | 3. August 15:00 UTC 2021 |
| Blackout Window | Länge des Blackout Windows | 14 Tage |
| Ausstellungsrate der Prämien | Token, die den Stakern sekündlich als Prämien zugewiesen werden | 0.1585489619 \* 10^18 (in wei) |
| Zuweisungen an Kreditnehmer | Prozentsatz der Geldmittel, die einem jeden Kreditnehmer zugewiesen werden | Wintermute 25 %, Amber 25 %, Sixtant 20 %, Kronos 20 %, DAT Trading 10 % |
| Proxy-Admin | Kann den Vertrag aktualisieren | Short Timelock |

## Sicherheitsmodul

| Parameter | Beschreibung | Wert |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------------ |
| Rolle der Eigentümer | Admin aller Roller | Short Timelock |
| Rolle des Slashers | Kann gestakte Tokenbilanzen beschlagnahmen und diese Guthaben abheben | Short Timelock |
| Rolle des Epochen-Parameter | Kann Epochen-Parameter wie beispielsweise das Intervall, Offset und Blackout Window einstellen | Short Timelock |
| Rolle des Prämien-Bemessers | Kann die Rate der Prämien bemessen | Short Timelock |
| Rolle des Claim Operators | Kann Prämien im Namen eines Benutzers abholen | Anspruchsvollmacht |
| Rolle des Stake Operators | Kann in gestakte Benutzerguthaben (z.B. Auszahlungen durchführen) im Namen eines Benutzers eingreifen | Short Timelock |
| Intervall | Länge einer Epoche | 28 Tage |
| Offset | Start der Epoche Null | 3. August 15:00 UTC 2021 |
| Blackout Window | Länge des Blackout Windows | 14 Tage |
| Ausstellungsrate der Prämien | Token, die den Stakern sekündlich als Prämien zugewiesen werden | 0.1585489619 \* 10^18 (in wei) |
| Proxy-Admin | Kann den Vertrag aktualisieren | Long Timelock |

## Stark Proxy

| Parameter | Beschreibung | Wert |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Rolle der Eigentümer | Kann diejenigen Empfänger hinzufügen/entfernen, die Gelder + STARK Keys erhalten, ERC20-Bewilligungen für Liquidity Staking und Stark Perpetual Contracts ausgeben, Zwangsmaßnahmen ausrufen und ist Verwalter der Eigentümer und Verwalter delegierter Administrationsrollen | Marktmacher |
| Rolle von delegierten Admins | Hierbei handelt es sich um einen Administrator von Kreditnehmer-, Exchange-Operator- und Auszahlungsoperatorrollen | Marktmacher |
| Rolle des Kreditnehmers | Kann Kreditfunktionen auf Basis des Liquidity Staking Contracts aufrufen | Marktmacher |
| Rolle des Exchange-Operatoren | Kann Exchange-Funktionen auf dem Stark Perpetual Contract aufrufen | Marktmacher |
| Rolle des Auszahlungsoperatoren | Kann überschüssige Gelder eines Kreditsaldos abheben und einem zugelassenen Empfänger übersenden | Marktmacher |
| Wächterrolle | Kann Abschlussaktionen durchführen, Zwangsmaßnahmen im Falle dass ein Kreditnehmer überfällige Schulden hat, ausführen, offene Aktionen mit geliehenen Geldern einschränken und die Rolle des Auszahlungsoperatoren dazu ermächtigen, eine Tokenmenge von außerhalb abzuheben. | Short Timelock |
| Veto-Wächterrolle | Kann ein Veto gegen durch den Eigentümer initiierte, erzwungene Trade-Anfragen während der Wartezeit einlegen | Merkle-Pauser Timelock |

## Stark Perpetual

| Parameter | Beschreibung | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| -------------------------------------- | ----------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Hinzufügen einer neuen Anlage |             | N | N | N | Y |
| Konfiguration einer bestehenden Anlage ändern |             | N | N | N | Y |
| Proxy-Admin |             | N | N | N | Y |
| Operator hinzufügen |             | N | N | N | Y |
| Operator entfernen |             | N | N | N | Y |
| Verifizierer hinzufügen |             | N | N | N | Y |
| Verifizierer entfernen |             | N | N | N | Y |
