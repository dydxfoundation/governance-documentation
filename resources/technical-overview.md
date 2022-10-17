---
description: Überblick über Governance-Architektur und Smart-Contracts.
---

# Technische Übersicht

## Übersicht der Governance-Architektur

Die dYdX-On-Chain-Governance unterstützt die folgenden Funktionen:

* Erstellung und Abstimmung über Vorschläge
* Speicherauszüge von gehaltenen Token beim Start eines Vorschlages zu erstellen
* Delegieren separater Abstimmungs- und Vorschlagsbefugnisse
* Festlegen von Governance-Schwellenwerten, einschließlich Vorschlags-, Quorum- und Abstimmungsschwellenwerten
* Ersetzt den Smart-Contract „Governance-Strategie“, der bestimmt, wie Stimmen gezählt werden
* Konfigurieren mehrerer Executor-Verträge, die Folgendes ermöglichen:
  * schnelle Protokoll-Upgrades und Geldverteilung über Short-Time-Lock-Executoren;
  * Governance-Upgrades über Long-Time-Lock-Executoren.

Es gibt 6 Smart-Contracts, die dYdX Governance unterstützen:

* **Der `DydxToken`-Vertrag**: Bewahrt Snapshots auf, die Abfragen für die Abstimmungs- oder Vorschlagsbefugnis einer Adresse bei einer beliebigen Blocknummer unterstützen. Unterstützt die getrennte Übertragung von Stimm- und Vorschlagsbefugnissen.
* **Der `DydxGovernor`-Vertrag**: Verfolgt Vorschläge und kann Vorschläge über die Executor Smart-Contracts ausführen.
* **Die `Executor`-Verträge**: Können Transaktionen in die Warteschlange stellen, stornieren und ausführen, über die von der Governance abgestimmt wurde. Wenn ein Vorschlag erfolgreich ist, können die Funktionsaufrufe im Vorschlag durch den im Vorschlag angegebenen Executor-Vertrag ausgeführt werden. Transaktionen in der Warteschlange können nach einer Verzögerung ausgeführt werden, deren Dauer durch den Executor-Vertrag bestimmt wird.
* **Der** **`Priority Timelock`****-Vertrag**: Derselbe wie der Timelock-Vertrag, jedoch erlaubt er dem Prioritäts-Prüfer die Ausführung von Transaktionen innerhalb der **Priority Periode** (7 Tage) vor Ablauf der Timelock-Verzögerung.
* **Der `Governance-Strategie`-Vertrag**: Enthält die Logik zum Zählen von Stimmen. Derzeit werden Stimmen aus dem DYDX-Token und dem Sicherheitsmodul gezählt. Aufrüstbar über die Langzeitsperre.
* **Der `Vertrag über das Sicherheitsmodul`**: Enthält Logiken zum Staking von DYDX-Token, zur Tokenisierung einer abgesteckten Position und zum Verdienen von Belohnungen, während die Abstimmungs- und Vorschlagsrechte und Delegierungsfunktionen der zugrunde liegenden Token beibehalten werden.

{% tabs %} {% tab title="Mainnet" %} | Vertrag    				| Adresse					| | ------------------------------------ | ------------------------------------------ | | DydxToken    				| 0x92D6C1e31e14520e676a687F0a93788B716BEff5 | | DydxGovernor    			| 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 | | Short Timelock Executor 		|  0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc | | Long Timelock Executor       		| 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B | | Merkle-Pauser Timelock Executor 	| 0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52 | | Starkware Priority Timelock Executor | 0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE | | Rewards Treasury                     | 0x639192D54431F8c816368D3FB4107Bc168d0E871 | | Community Treasury                   | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b | | Sicherheitsmodul    			| 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC | | GovernanceStrategy    			| 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 | | Rewards Treasury Vester    		| 0xb9431E19B29B952d9358025f680077C3Fd37292f | | Community Treasury Vester     	| 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 | | Merkle Distributor    		 | 0x01d3348601968aB85b4bb028979006eac235a588 | | Chainlink Adapter     		| 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 | | Liquidity Staking                    | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 | | Claims Proxy                         | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e | | StarkEx Helper Governor              | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a | | StarkEx Remover Governor V2          | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 | | Rewards Treasury Proxy Admin         | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d | | Community Treasury Proxy Admin       | 0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 | | Sicherheitsmodul Proxy Admin    | 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C | | Merkle Distributor Proxy Admin       | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 | | Liquidity Staking Proxy Admin        | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 | | StarkProxy \[0]                      | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 | | StarkProxy \[1]                      | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF | | StarkProxy \[2]                      | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 | | StarkProxy \[3]                      | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 | | StarkProxy \[4]                      | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 | | StarkProxy Proxy Admin \[0]          | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 | | StarkProxy Proxy Admin \[1]          | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 | | StarkProxy Proxy Admin \[2]          | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 | | StarkProxy Proxy Admin \[3]          | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA | | StarkProxy Proxy Admin \[4]          | 0xfa45DCDbEc82C94082d283B62506320DB8632054 | {% endtab %} {% endtabs %}

## Open-Source Code & auditiert

Der gesamte Smart-Contract-Quellcode für die Governance-Verträge und Staking-Pools ist unter [https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts) zu finden.

Den Quellcode für das auf dydx.community gehostete Governance-Frontend finden [Sie hier](https://github.com/dydxfoundation/pnyx).

Alle wichtigen neuen Smart-Verträge wurden von Peckshield geprüft. Es wurden keine Sicherheitsprobleme mit erheblicher oder hoher Priorität gefunden. Die Kern-Governance- und Token-Verträge stammen aus den Aave-Governance-Verträgen, die von [CertiK](https://www.certik.io/), [Certora](https://www.certora.com/) und [Peckshield](https://peckshield.com/en) geprüft und seit Monaten live im Mainnet kampferprobt wurden.

## Core Governance-Verträge

![Rote gestrichelte Linien zeigen an, dass der Vertrag erweiterbar ist](../.gitbook/assets/3-core-governance-contracts-1.png)

### DydxToken

Der DydxToken-Vertrag wurde von Aave inspiriert. Kleinere Änderungen wurden vom dYdX-Team vorgenommen.

DYDX wird unter [0x92D6C1e31e14520e676a687F0a93788B716BEff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

### DydxGovernor

Der DydxGovernor-Vertrag wurde von Aave inspiriert. Kleinere Änderungen wurden von dYdX vorgenommen.

Governor wird unter [0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

### GovernanceStrategy

Der GovernanceStrategy-Vertrag wurde von Aave inspiriert.

Die Strategie wird unter [0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

### Executors

Der Executor-Vertrag wurde von Aave inspiriert. Kleinere Änderungen wurden von dYdX vorgenommen.

Das **Long Timelock** wird unter [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

Das **Short Timelock** wird bei [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

Das **Merkle Timelock** wird unter [0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

Das **Starkware Priority Timelock** wird unter [0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae) im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

## DYDX-Incentives-Verträge

### Merkle Distributor

![Rote gestrichelte Linien zeigen an, dass der Vertrag erweiterbar ist](../.gitbook/assets/3-core-governance-contracts-2.png)

Der Merkle Distributor Smart-Vertrag verteilt DYDX-Token-Belohnungen gemäß einem Merkle-Baum von Guthaben. Der Baum kann regelmäßig mit dem kumulativen Prämienguthaben jedes Benutzers aktualisiert werden, sodass im Laufe der Zeit neue Prämien an Benutzer verteilt werden können.

Ein Update wird durchgeführt, indem die vorgeschlagene Merkle Root auf den letzten Wert eingestellt wird, der vom Oracle Vertrag zurückgegeben wurde. Die vorgeschlagene Merkle Root kann nach Ablauf einer Wartezeit aktiviert werden. Während der Wartezeit hat die dYdX-Governance die Möglichkeit, die Merkle Root einzufrieren, falls die vorgeschlagene Root falsch oder bösartig ist. Root-Updates können von ShortTimelockExecutor fortgesetzt werden.

Der Merkle Distributor Smart-Vertrag wurde von Uniswap- und Badger-Designs inspiriert. Der Smart Contract wird unter 0x01d3348601968aB85b4bb028979006eac235a588 im Ethereum-Mainnet bereitgestellt. Es wurde von Commit erstellt  \[in Kürze].

**ABI**

\[in Kürze]

### Sicherheitsmodul

![Rote gestrichelte Linien zeigen an, dass der Vertrag erweiterbar ist](../.gitbook/assets/3-core-governance-contracts-3.png)

Das Sicherheitsmodul ist ein Staking-Pool, der DYDX-Belohnungen für Benutzer bietet, die DYDX für die Sicherheit des Protokolls einsetzen.

**ABI**

\[in Kürze]

### Liquidity-Modul

![Rote gestrichelte Linien zeigen an, dass der Vertrag erweiterbar ist](../.gitbook/assets/3-core-governance-contracts-4.png)

Das Liquiditätsmodul ist eine Sammlung von intelligenten Verträgen zum Abstecken und Ausleihen, die die Zuweisung von USDC-Geldern für Marktmacher-Zwecke an der dYdX-Ebene-2-Börse anregen.

Staker erhalten DYDX-Belohnungen für das Staking von USDC. Die eingesetzten Mittel können von bestimmten vorab genehmigten Partnern auf Reputationsbasis ohne Sicherheiten ausgeliehen werden. Die Mittel dürfen nur an der L2-Börse verwendet werden – dies wird über den StarkProxy-Vertrag durchgesetzt, der mit dem StarkEx Perpetual Exchange-Vertrag interagiert.

![Ein Diagramm des Liquiditätsmoduls](../.gitbook/assets/3-core-governance-contracts-5.png)

### StarkProxy

Dieser Vertrag erlaubt dem Besitzer, Gelder von LiquidityStaking zu leihen und diese Gelder auf StarkPerpetual zu verwenden. Zusätzliche Gelder können vom Eigentümer hinterlegt werden, und alle Gelder, die den geliehenen Betrag übersteigen, können frei abgehoben werden. Dieser Vertrag interagiert mit dem [StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual)-Vertrag, der von Starkware geschrieben und zuvor geprüft und bereitgestellt wurde.

### Treasury-Verträge

![Rote gestrichelte Linien zeigen an, dass der Vertrag erweiterbar ist](../.gitbook/assets/3-core-governance-contracts-6.png)

Der TreasuryVester-Vertrag wurde von [Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol) inspiriert.

Das Short Timelock kann nur von der Governance genehmigte Aktionen ausführen.

Es gibt zwei Treasury Vesters und Treasury-Verträge, einen für Incentive-Vertrags-Belohnungen und den anderen für das Halten von „Allzweck“-Treasury-Fonds.

Da die Governance jedes Treasury kontrolliert, kann sie Gelder an jede Adresse überweisen und/oder jede Adresse genehmigen, um Gelder aus beiden Treasuries auszugeben. Beispielsweise müssen die Prämienprogramme Token-Genehmigungslimits haben, die von der Governance festgelegt werden.

Jeder Treasury Vester wird Token linear über ~5 Jahre (3. August 2021 - 3. August 2026) an das entsprechende Treasury übertragen.

## Periphere Verträge

### Chainlink Oracle-betriebene Belohnungen (Belohnungen für Handels- und Liquiditätsanbieter)

Das Ziel dieses Systems ist es, über ein dezentralisiertes Netzwerk von Oracle-Unterzeichnern die DYDX-Token-Belohnungen zu berechnen und zu veröffentlichen, die von Händlern über die dYdX-Ebene-2-Börse verdient wurden. Belohnungen werden in einem Merkle-Baum gespeichert, der die kumulativen Belohnungen enthält, die jeder Benutzer seit dem Start des Verteilungsprogramms verdient hat. In jeder Epoche wird die Merkle Root auf dem MerkleDistributorV1-Smart-Vertrag aktualisiert, um die in der letzten Epoche verdienten Belohnungen widerzuspiegeln.

Wir haben das Oracle-System von Chainlink integriert, um Belohnungsdaten in der Kette zu veröffentlichen. Wir verwenden IPNS, um die Handelsdaten zu veröffentlichen, die Chainlink zum Aufbau des Merkle-Baums verwendet. Durch die Verwendung von IPNS können wir die Handelsdaten für die letzte Epoche unter demselben IPNS-Link wie frühere Epochen veröffentlichen, was bedeutet, dass sich der Speicherort der Daten nicht ändert.

Nach der Berechnung der entsprechenden Belohnungen aus den rohen Handelsdaten postet Chainlink den Merkle-Belohnungsbaum an IPFS. Die IPFS-CID mit den Merkle-Baumdaten wird im Merkle-Vertriebsvertrag zusammen mit der Merkle Root für die Belohnungen dieser Epoche gespeichert.

Das folgende Flussdiagramm zeigt die Systemarchitektur von Chainlink Oracle-Powered Rewards:

![](../.gitbook/assets/3-core-governance-contracts-merkle-distributor.png)

### Andere Anlagen

* dYdX Foundation Marken-Anlagen sind [**hier**](https://dydx.foundation/brand) verfügbar\*\*\*\*
