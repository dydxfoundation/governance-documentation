---
description: >-
  Ein technischer Schritt-für-Schritt-leitfaden zur Erstellung eines Vorschlags zur Übertragung von ethDYDX aus Mitteln der Community an eine Zieladresse.
---

# Technischer Leitfaden zur Erstellung eines Ausgabenvorschalgs für die dYdX Community

Reverie hat einen umfassenden, technischen Leitfaden für die Einreichung eines Governance-Vorschlags zur Übertragung von $ethDYDX aus Mitteln der Community durch eine Pull-Anfrage in das dYdX _Governance-Contracts_ Repository zusammengestellt.

Um diesen Vorschlag zu erstellen, muss ein Mitglied der dYdX-Community **über mindestens 5 Mio Governance-Token** (_0,5 % des Gesamtangebots)_ an Vorschlagsrechten ([Vorschlagsschwellenwert](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) für eine [kurzzeiitige Wahl](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) verfügen.

### Vorläufige Anforderungen

Die folgenden Schritte müssen vor der Fertigstellung der Pull-Anfrage abgeschlossen werden:

1. **Lebenszyklus des Vorschlags** Das DRC muss gemäß der [Vorschlagsvorlage](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) gepostet werden und es muss eine erfolgreiche Snapshot-Abstimmung erfolgen.
2. **Zieladresse:** Die Zieladresse muss im Voraus generiert werden. Wenn die Zieladresse eine Multi-Sig-Adresse ist, muss das Multi-Sig-Wallet erstellt werden.
3. **GitHub-Konto:** Ein GitHub-Konto, um das Repository zu spalten.
4. **Übertragungsmenge (optional):** Vorzugsweise wurde die angeforderte Übertragungsmenge schon vor der Pull-Anfrage festgelegt. Wenn allerdings ein fiktiver Betrag verwendet wird, kann es als letzter Schritt vor der Genehmigung erfolgen.
5. **DIP-IPFS-Hash (optional):** Wenn der Übertragungsbetrag bekannt ist, sollte das DIP abgeschlossen und zum IPFS verschoben werden, um das Hash zu generieren. Es kann jedoch als ein letzter Schritt vor der Genehmigung festgelegt werden, wenn der Betrag noch nicht ermittelt wurde.

### Den Vorschlag erstellen

1. **Gabeln Sie das **d[**YdX-Governance-Contracts-Repository **](https://github.com/dydxfoundation/DIP)a**uf Ihr GitHub-Konto.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Klonen Sie das Repository,** und ändern Sie den \[username] auf Ihren eigenen.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Konfigurationsvariablen**

Fügen Sie in src/config/index.ts zwei neue Variablen zur configSchema-Konstante hinzu, die für Testzwecke verwendet werden. Ändern Sie in den folgenden Code-Blocks die Felder **„VORSCHLAG\_NAME“** und **„VORSCHLAG“** in den Namen des eingereichten Vorschlags.

```typescript
src/config/index.ts
...
const configSchema = {
	...
	FUND_PROPOSAL_NAME_PROPOSAL_ID: parseInteger({ default: null }),
	TEST_PROPOSAL_NAME_WITH_PROPOSAL: parseInteger({ default: true }),
};
...
```

Fügen Sie in src/deploy-config/base-config.ts die Zieladresse und die Übertragungsmenge als neue Variablen in der Konfigurationskonstante hinzu:

```typescript
src/deploy-config/base-config.ts
....
const config = {
	....
	
	PROPOSAL_NAME_ADDRESS = '0x...',
	PROPOSAL_FUNDING_AMOUNT = '10000000000000000000',
};
...
```

**Hinweis**: Der Finanzierungsbetrag muss gemäß ERC20 **mit 10^18 multipliziert **werden. Wenn der Betrag noch nicht bekannt ist, kann auch ein temporärer Betrag verwendet werden (z. B. 10 → 10 000 000 000 000 000 000).

Fügen Sie in src/lib/constants.ts die IPFS-Hash-Variable hinzu, die auf das im anderen Repository genehmigte DIP verweist:

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Hinweis**: Wenn das DIP noch nicht veröffentlicht wurde, kannn zum Test ein temporärer Wert verwendet werden (z. B. „0x0 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000 000“)\


4\. **Vorschlags-Code**

Erstellen Sie in _**src/migrations**_ eine neue Datei, benannt nach dem Vorschlag → Vorschlag-name.ts und tragen Sie den folgenden Code ein:

a. Fügen Sie die benötigten Importe oben hinzu:

```typescript
src/migrations/proposal-name.ts
import { SignerWithAddress } from '@nomiclabs/hardhat-ethers/signers';
import {
  DydxGovernor__factory,
} from '../../types';
import { getDeployConfig } from '../deploy-config';
import { getDeployerSigner } from '../deploy-config/get-deployer-address';
import { getHre } from '../hre';
import { log } from '../lib/logging';
import { waitForTx } from '../lib/util';
import { Proposal } from '../types';
```

b. Erstellen Sie eine neue Funktion unter Verwendung des Vorschlagnamens unter den Importen und fügen Sie folgenden Code mit zwei einziartigen Variablen hinzu:

* **Zieladresse** → diese Adresse wird die Finanzierung erhalten
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → dies ist die Variable, die wir zuvor erstellt haben, mit der die zu übertragende Menge festgelegt wird

```typescript
src/migrations/proposal-name.ts
export async function createProposalNameProposal({
  proposalIpfsHashHex,
  dydxTokenAddress,
  governorAddress,
  shortTimelockAddress,
  communityTreasuryAddress,
  destinationAddress, // This is the address that will receive the funding
  signer,
}: {
  proposalIpfsHashHex: string,
  dydxTokenAddress: string,
  governorAddress: string,
  shortTimelockAddress: string,
  communityTreasuryAddress: string,
  destinationAddress: string,
  signer?: SignerWithAddress,
}) {
  const hre = getHre();
  const deployConfig = getDeployConfig();
  const deployer = signer || await getDeployerSigner();
  const deployerAddress = deployer.address;
  log(`Creating proposal with proposer ${deployerAddress}.\n`);
  const governor = await new DydxGovernor__factory(deployer).attach(governorAddress);
  const proposalId = await governor.getProposalsCount();
  const proposal: Proposal = [
    shortTimelockAddress,
    [communityTreasuryAddress],
    ['0'],
    ['transfer(address,address,uint256)'],
    [hre.ethers.utils.defaultAbiCoder.encode(
      ['address', 'address', 'uint256'],
      [dydxTokenAddress, destinationAddress, deployConfig.PROPOSAL_FUNDING_AMOUNT],
    )],
    [false],
    proposalIpfsHashHex,
  ];
  await waitForTx(await governor.create(...proposal));
  return {
    proposalId,
  };
}
```

\
5\. **Bereitstellungsaufgabe**

Mit dem erstellten Vorschlag können wir die Bereitstellung schreiben, mit der die erforderlichen Transaktions- und Anrufdaten erstellt werden, um den Vorschlag einzureichen.

Erstellen Sie in _**tasks/deployment,**_ eine neue Datei mit demselben Namen, der auch für den Vorchlags-Code verwendet wurde → Vorschlag-name.ts und tragen Sie den folgenden Code ein:

a. Fügen Sie die benötigten Importe mit den folgenden Variablen hinzu:

_**DIP\_NUMBER\_IPFS\_HASH**_ → Dies ist die Variable, die wir in lib/constants hinzufügen.

_**createProposalNameProposal**_ → Dies ist die Funktion, die wir in /src/migrations/proposal-name erstellt haben.

```typescript
tasks/deployment/proposal-name.ts
import { types } from 'hardhat/config';
import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. Erstellen Sie die Hardhat-Aufgabe und tragen Sie die Vorschlagsdaten in die Eröffnungszeile der Aufgabe ein. \
\
Ersetzen Sie den Vorschlag-name in „deploy:proposal-name: und ersetzen Sie ihn mit einer Beschreibung in „Proposal Description“.

Die letzte Zeile ruft die Funktion auf, die Sie aus dem Vorschlags-Code importiert haben, muss also angepasst werden.

```typescript
tasks/deployment/proposal-name.ts
hardhatTask('deploy:proposal-name', 'Proposal Description.')
  .addParam('proposalIpfsHashHex', 'IPFS hash for the uploaded DIP describing the proposal', DIP_NUMBER_IPFS_HASH, types.string)
  .addParam('dydxTokenAddress', 'Address of the deployed DYDX token contract', mainnetAddresses.dydxToken, types.string)
  .addParam('governorAddress', 'Address of the deployed DydxGovernor contract', mainnetAddresses.governor, types.string)
  .addParam('shortTimelockAddress', 'Address of the deployed short timelock Executor contract', mainnetAddresses.shortTimelock, types.string)
  .addParam('communityTreasuryAddress', 'Address of the deployed community treasury contract', mainnetAddresses.communityTreasury, types.string)
  .setAction(async (args) => {
    await createProposalNameProposal(args);
  });
```

\
6\. **Tests durchführen**

Nachdem der Code nun für die Bereitstellung bereit ist, wird es Zeit, einige Tests rund um den Vorschlag zu erstellen. Das Testen erfolgt lokal unter Verwendung eines Mainnet-Forks, um zu simulieren, dass ein Vorschlag in der Chain ausgeführt wird.

a. **Vorschlagstests hinzufügen**

Fügen Sie in Test/Migrationen erneut eine neue Datei mit dem Vorschlagnamen → proposal-name.ts hinzu und tragen Sie den folgenden Code ein:

*   Fügen Sie die benötigten Importe einschließlich der Vorschlagsfunktionen hinzu:

**createProposalNameProposal** → Dies ist die Funktion, die wir in /src/migrations/proposal-name erstellt haben. \


**MOCK\_PROPOSAL\_IPFS\_HASH** → wir verwenden für Testzwecke ein Attrappen-Hash

```typescript
test/migrations/proposal-name.ts
import BNJS from 'bignumber.js';
import { BigNumber, BigNumberish } from 'ethers';
import config from '../../src/config';
import { getDeployConfig } from '../../src/deploy-config';
import { getDeployerSigner } from '../../src/deploy-config/get-deployer-address';
import { log } from '../../src/lib/logging';
import { waitForTx } from '../../src/lib/util';
import { impersonateAndFundAccount } from '../../src/migrations/helpers/impersonate-account';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
import {
  DydxGovernor__factory,
  DydxToken__factory,
  Treasury__factory,
} from '../../types';
import { advanceBlock, increaseTimeAndMine } from '../helpers/evm';
const MOCK_PROPOSAL_IPFS_HASH = (
  '0x0000000000000000000000000000000000000000000000000000000000000000'
);
```

*   Ergänzen Sie die Testfunktionen mit den folgenden Schritten:

    * **fundProposalNameViaProposal** → Erstellen Sie diese Funktion und benennen Sie sie um, sodass sie mit dem Vorschlagnamen übereinstimmt.
    * **destinationAddress** → Beschriften Sie dies neu, sodass es zum Zielnamen passt
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → Dies wird durch die Variable aus der Basiskonfigurationsdatei ersetzt.
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → Diese Variable haben wir in _**config/index.ts**_ erstellte
    * _**createProposalNameProposal** → Importieren Sie diese Funktion oben zur Verwendung._
    * **fundProposalNameViaNoProposal** → Erstellen Sie diese Funktion und benennen Sie sie um, sodass sie zum Vorschlagnamen passt.

\
    Führen Sie den folgenden Code aus, um alle diese Variablen durch den Vorschlagnamen und bestehende, bereits oben erstellte Variablen zu ersetzen:

```typescript
test/migrations/proposal-name.ts
export async function fundProposalNameViaProposal({
  dydxTokenAddress,
  governorAddress,
  shortTimelockAddress,
  communityTreasuryAddress,
  destinationAddress,
}: {
  dydxTokenAddress: string,
  governorAddress: string,
  shortTimelockAddress: string,
  communityTreasuryAddress: string,
  destinationAddress: string,
}): Promise<void> {
  const deployConfig = getDeployConfig();
  const deployer = await getDeployerSigner();
  const dydxToken = new DydxToken__factory(deployer).attach(dydxTokenAddress);
  const governor = new DydxGovernor__factory(deployer).attach(governorAddress);
  await fundCommunityTreasuryFromFoundationIfNecessary({
    dydxTokenAddress,
    communityTreasuryAddress,
    minTreasuryBalance: deployConfig.PROPOSAL_FUNDING_AMOUNT,
  });
  // Pick a voter with enough tokens to meet the quorum requirement.
  const voterAddress = deployConfig.TOKEN_ALLOCATIONS.DYDX_TRADING.ADDRESS;
  const voter = await impersonateAndFundAccount(voterAddress);
  const voterBalance = await dydxToken.balanceOf(voterAddress);
  if (voterBalance.lt(new BNJS('2e25').toFixed())) {
    throw new Error('Not enough votes to pass the proposal.');
  }
  // Vote on an existing proposal (can be used with mainnet forking).
  let proposalId: BigNumberish;
  if (config.FUND_PROPOSAL_NAME_PROPOSAL_ID !== null) {
    proposalId = config.FUND_PROPOSAL_NAME_PROPOSAL_ID;
  } else {
    log('Creating proposal');
    ({ proposalId } = await createProposalNameProposal({
      proposalIpfsHashHex: MOCK_PROPOSAL_IPFS_HASH,
      dydxTokenAddress,
      governorAddress,
      shortTimelockAddress,
      communityTreasuryAddress,
      destinationAddress,
      signer: voter,
    }));
    log('Waiting for voting to begin');
    for (let i = 0; i < deployConfig.VOTING_DELAY_BLOCKS + 1; i++) {
      if (i > 0 && i % 2000 === 0) {
        log('mining', i);
      }
      await advanceBlock();
    }
  }
  let proposalState = await governor.getProposalState(proposalId);
  if (proposalState !== 2) {
    throw new Error('Expected proposal to be in the voting phase.');
  }
  log('Submitting vote');
  await waitForTx(await governor.connect(voter).submitVote(proposalId, true));
  log('Waiting for voting to end');
  let minedCount = 0;
  for (; ;) {
    for (let i = 0; i < 2000; i++) {
      await advanceBlock();
      minedCount++;
    }
    log('mining', minedCount);
    proposalState = await governor.getProposalState(proposalId);
    if (proposalState !== 2) {
      break;
    }
  }
  if (proposalState !== 4) {
    throw new Error(`Expected proposal to have succeeded but state was ${proposalState}`);
  }
  log('Queueing the proposal');
  await waitForTx(await governor.queue(proposalId));
  const delaySeconds = deployConfig.SHORT_TIMELOCK_CONFIG.DELAY;
  await increaseTimeAndMine(delaySeconds);
  log('Executing the proposal');
  await waitForTx(await governor.execute(proposalId));
  log('Proposal executed');
  log('\n=== FUNDING PROPOSAL COMPLETE ===\n');
}
export async function fundProposalNameNoProposal({
  dydxTokenAddress,
  shortTimelockAddress,
  communityTreasuryAddress,
  destinationAddress,
}: {
  dydxTokenAddress: string,
  shortTimelockAddress: string,
  communityTreasuryAddress: string,
  destinationAddress: string,
}): Promise<void> {
  const deployConfig = getDeployConfig();
  const mockShortTimelock = await impersonateAndFundAccount(shortTimelockAddress);
  const communityTreasury = new Treasury__factory(mockShortTimelock).attach(
    communityTreasuryAddress,
  );
  await fundCommunityTreasuryFromFoundationIfNecessary({
    dydxTokenAddress,
    communityTreasuryAddress,
    minTreasuryBalance: deployConfig.PROPSAL_FUNDING_AMOUNT,
  });
  await waitForTx(
    await communityTreasury.transfer(
      dydxTokenAddress,
      destinationAddress,
      deployConfig.PROPOSAL_FUNDING_AMOUNT,
    ),
  );
  log('\n=== PROPOSAL FUNDING COMPLETE ===\n');
}
async function fundCommunityTreasuryFromFoundationIfNecessary({
  dydxTokenAddress,
  communityTreasuryAddress,
  minTreasuryBalance,
}: {
  dydxTokenAddress: string,
  communityTreasuryAddress: string,
  minTreasuryBalance: string,
}): Promise<void> {
  const deployConfig = getDeployConfig();
  const mockFoundation = await impersonateAndFundAccount(deployConfig.TOKEN_ALLOCATIONS.DYDX_FOUNDATION.ADDRESS);
  const dydxToken = new DydxToken__factory(mockFoundation).attach(dydxTokenAddress);
  const communityTreasuryBalance: BigNumber = await dydxToken.balanceOf(communityTreasuryAddress);
  if (communityTreasuryBalance.lt(minTreasuryBalance)) {
    // Transfer necessary funds to the treasury.
    await waitForTx(
      await dydxToken.transfer(
        communityTreasuryAddress,
        minTreasuryBalance,
      ),
    );
  }
}
```

b. **Fügen Sie Testfunktionen zum Test-Skript hinzu**

In test/migrations/deploy-contracts-for-test.ts fügen wir die oben erstellten Funktionen hinzu, sodass Sie in unseren Tests enthalten sind:

* Importieren Sie die erstellten Funktionen.

```typescript
test/migrations/deploy-contracts-for-test.ts
...
import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Fügen Sie Tests für beide Funktionen hinzu, indem Sie eine allgemeine Testfunktion erstellen → executeProposalNameProposalForTest, **ersetzen Sie den Namen, sodass er zum Vorschlag passt**
* Wir rufen auch die zuvor erstellte Konfigurationsvariable **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** und die **PROPOSAL\_NAME\_ADDRESS** von deployConfig auf.

```typescript
...
export async function executeProposalNameProposalForTest(
  deployedContracts: AllDeployedContracts,
) {
  const deployConfig = getDeployConfig();
  if (config.TEST_PROPOSAL_NAME_TRUST_WITH_PROPOSAL) {
    await fundProposalNameViaProposal({
      dydxTokenAddress: deployedContracts.dydxToken.address,
      governorAddress: deployedContracts.governor.address,
      shortTimelockAddress: deployedContracts.shortTimelock.address,
      communityTreasuryAddress: deployedContracts.communityTreasury.address,
      destinationAddress: deployConfig.PROPOSAL_NAME_ADDRESS,
    });
  } else {
    await fundProposalNameNoProposal({
      dydxTokenAddress: deployedContracts.dydxToken.address,
      shortTimelockAddress: deployedContracts.shortTimelock.address,
      communityTreasuryAddress: deployedContracts.communityTreasury.address,
      destinationAddress: deployConfig.PROPOSAL_NAME_ADDRESS,
    });
  }
}
...
// put this above the configureForTest function
```

c. **Fügen Sie einen Vertrag zu Testhelfern hinzu**

Fügen Sie in test/helpers/get-deployed-contracts-for-test.ts die oben erstellte Funktion hinzu, damit die Tests im Mainnet-Fork ausgeführt werden

* Importieren Sie die Funktion executeProposalNameProposalForTest aus derMigrationsdatei:

```typescript
test/helpers/get-deployed-contracts-for-test.ts
...
import {
  configureForTest,
  deployContractsForTest,
  executeSafetyModuleRecoveryProposalsForTest,
  executeStarkProxyProposalForTest,
  executeGrantsProgramProposalForTest,
  executeGrantsProgramv15ProposalForTest,
  executeWindDownBorrowingPoolProposalForTest,
  executeUpdateMerkleDistributorRewardsParametersProposalForTest,
  executeWindDownSafetyModuleProposalForTest,
  executeProposalNameProposalForTest,
} from '../migrations/deploy-contracts-for-test';
```

* Fügen Sie die Funktion zu getDeployedContractsForTest() hinzu, außerhalb der letzten else-Schleife:

```typescript
test/helpers/get-deployed-contracts-for-test.ts
async function getDeployedContractsForTest(): Promise<AllDeployedContracts> {
  if (!config.isHardhat()) {
    return getAllContracts();
  }
  let deployedContracts: AllDeployedContracts;
  if (config.FORK_MAINNET) {
    deployedContracts = await getAllContracts();
  } else {
    deployedContracts = await deployContractsForTest();
    // Execute the proposals which have already been executed on mainnet.
    //
    // The proposals will be executed when running on a local test network,
    // but will not be executed when running on a mainnet fork.
    await executeSafetyModuleRecoveryProposalsForTest(deployedContracts);
    await executeStarkProxyProposalForTest(deployedContracts);
    await executeGrantsProgramProposalForTest(deployedContracts);
    await executeGrantsProgramv15ProposalForTest(deployedContracts);
    await executeWindDownBorrowingPoolProposalForTest(deployedContracts);
    await executeUpdateMerkleDistributorRewardsParametersProposalForTest(deployedContracts);
    await executeWindDownSafetyModuleProposalForTest(deployedContracts);
  }
  await executeProposalNameProposalForTest(deployedContracts);
  // Execute the proposals which have not yet been executed on mainnet.
  await configureForTest(deployedContracts);
  return deployedContracts;
}
```

d. **Endgültige Testdatei**

Schlussendlich fügen wir einen Test sowohl zum IPFS-Hash als auch zur Bilanz des Multi-Sig nach dem Attrappenvorschlag hinzu, um sicherzustellen, dass alles wie erwartet zu Ende geht.

Fügen Sie in test/misc eine neue Datei mit dem Vorschlagsnamen → proposal-name-proposal.spec.ts beschriftet, hinzu und tragen Sie diese zwei Tests ein:

1. Wir importieren dieses IPFS-Hash aus derBibliothek durch DIP\_NUMBER\_IPFS\_HASH
2. wir codieren die nächste Vorschlags-Id unter Verwendung von ProposalNameId
3. wir überprüfen das Vorschlags-Hash mit dem konstanten Hash
4.  wir überprüfen die Adresse PROPOSAL\_NAME\_ADDRESS, um zu sehen, ob es eine ausgeglichene Bilanz des Betrags PROPOSAL\_FUNDING\_AMOUNT hat

**Hinweis: wenn diese Adress bereits DYDX hat, müssen Sie fest einprogrammieren, damti die Bilanz den Test besteht**

```typescript
test/misc/proposal-name-proposal.spec.ts
import { expect } from 'chai';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { describeContract, TestContext } from '../helpers/describe-contract';
function init() {}
describeContract('proposal-name', init, (ctx: TestContext) => {
  it('Proposal IPFS hash is correct', async () => {
    const ProposalNameId = #;
    const proposal = await ctx.governor.getProposalById(ProposalNameId);
    expect(proposal.ipfsHash).to.equal(DIP_NUMBER_IPFS_HASH);
  });
  it('Destination receives tokens from the community treasury', async () => {
    const balance = await ctx.dydxToken.balanceOf(ctx.config.PROPOSAL_NAME_ADDRESS);
    expect(balance).to.equal(ctx.config.PROPOSAL_FUNDING_AMOUNT);
  });
});
```

7\. **Die Pull-Anfrage einreichen**

Nachdem alle diese Codeveränderungen gemacht wurden, können wir an das geforkte Repiository übergeben und eine Pulll-Anfrage an das dYdX für Überprüfer öffnen:

a. **Bestätigen Sie die Änderungen durch die Befehlszeile**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **Reichen Sie eine Pull-Anfrage an das dYdX-Repository** ein

<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">

c. **Warten Sie auf die Überprüfung und Genehmigung durch den Repository-Manager**

