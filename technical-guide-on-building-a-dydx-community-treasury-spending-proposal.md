---
description: >-
  Un guide technique, qui décrit étape par étape, la façon de créer une proposition de transfert ethDYDX de la trésorerie de la communauté vers une adresse de destination.
---

# Guide technique sur l'élaboration d'une proposition de dépenses de trésorerie de la communauté dYdX

Reverie a élaboré un guide technique complet pour soumettre une proposition de gouvernance visant à transférer des $ethDYDX du Trésor communautaire par le biais d'une demande d'extraction (PR, Pull Request) vers le référentiel _des contrats de gouvernance_ dYdX.

Pour créer cette proposition, un membre de la communauté dYdX doit avoir **au moins 5 millions de jetons de gouvernace** _(0,5 % de l'offre totale)_ de pouvoir de [proposition](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) (seuil de proposition pour un [vote à court terme](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)).

### Exigences préliminaires

Les étapes suivantes doivent être accomplies avant l'achèvement de la demande d'extraction (PR) :

1. **Durée de vie de la proposition :** la DRC doit être publiée en suivant le [modèle](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) de proposition et il doit y avoir un vote Snapshot réussi.
2. **Adresse de destination :** l'adresse de destination doit être générée à l'avance. Si l'adresse de destination est un multi-sig, le portefeuille multi-sig doit être créé.
3. **Compte GitHub :** un compte GitHub pour forker le référentiel.
4. **Montant du transfert (facultatif) :** de préférence, le montant du transfert demandé a été établi avant la PR. Toutefois, si vous utilisiez un montant notionnel, il peut être défini comme une étape finale avant l'approbation.
5. **Hachage DIP IPFS (facultatif) :** si le montant du transfert est connu, le DIP doit être finalisé et poussé vers l'IPFS pour générer son hachage. Cependant, cela peut être défini comme une étape finale avant l'approbation si le montant n'est pas encore déterminé.

### Construire la proposition

1. **Forkez le** [**référentiel des contrats de gouvernance dYdX**](https://github.com/dydxfoundation/DIP) **sur votre compte GitHub.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Clonez le référentiel** et changez le \[username] en votre propre nom d'utilisateur.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Variables de configuration**

Dans src/config/index.ts, ajoutez deux nouvelles variables à la constante configSchema qui sera utilisée à des fins de test. Dans les blocs de code suivants, changez les champs **'PROPOSAL\_NAME'** et **'PROPOSAL'** par le nom de la proposition soumise.

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

Dans src/deploy-config/base-config.ts, ajoutez l'adresse de destination et le montant du transfert en tant que nouvelles variables dans la constante config :

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

**Remarque** : Le montant du financement devra être **multiplié par 10^18** selon la norme ERC20. Si le montant n'est pas encore connu, un montant temporaire peut être utilisé (par exemple 10 → 10000000000000000000)

Dans src/lib/constants.ts, ajoutez la variable de hachage IPFS qui fera référence au DIP approuvé dans l'autre référentiel :

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Remarque** : Si le DIP n'a pas encore été publié, une valeur temporaire peut être utilisée pour le test (par exemple ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **Code de proposition**

Dans _**src/migrations,**_ créez un nouveau fichier nommé d'après la proposition → proposal-name.ts et remplissez le code suivant :

a. Ajoutez les importations nécessaires en haut :

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

b. Créez une nouvelle fonction en utilisant le nom de proposition sous les importations et ajoutez le code suivant avec deux variables uniques :

* **destinationAddress** → il s'agit de l'adresse qui recevra le financement
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → il s'agit de la variable que nous avons créée précédemment qui déterminera le montant à transférer

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
5\. **Tâche de déploiement**

Avec la proposition créée, nous pouvons écrire le déploiement qui générera transaction et les données d'appel nécessaires pour soumettre la proposition.

Dans _**tâches/déploiement,**_ créez un nouveau fichier avec le même nom utilisé pour le code de proposition → proposal-name.ts et remplissez avec le code suivant :

a. Ajoutez les importations nécessaires avec les variables suivantes :

_**DIP\_NUMBER\_IPFS\_HASH**_ → il s'agit de la variable que nous ajoutons dans lib/constants

_**createProposalNameProposal**_ → il s'agit de la fonction que nous avons créée dans /src/migrations/proposal name

```typescript
tasks/deployment/proposal-name.ts
import { types } from 'hardhat/config';
import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. Créez la tâche hardhat et remplissez-la avec les informations de proposition sur la ligne d'ouverture de la tâche. \
\
Remplacez le proposal-name dans ‘deploy:proposal-name: et remplacez-le par une brève description dans ‘Description de la proposition’.

La dernière ligne appelle la fonction que vous avez importée à partir du code de proposition, il faudra donc l'ajuster.

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
6\. **Tests de construction**

Maintenant que le code est prêt pour le déploiement, il est temps de construire certains tests autour de la proposition. Les tests sont effectués à la fois localement et en utilisant un fork du mainnet pour simuler une proposition en cours d'exécution sur la chaîne.

a. **Ajoutez des tests de proposition**

Dans test/migrations, ajoutez à nouveau un nouveau fichier avec le nom de proposition → proposal-name.ts et incluez le code suivant :

*   Ajoutez les importations nécessaires, y compris les fonctions de proposition :

**createProposalNameProposal** → il s'agit de la fonction que nous avons créée dans /src/migrations/proposal name. \


**MOCK\_PROPOSAL\_IPFS\_HASH** → nous allons utiliser un hachage fictif à des fins de test

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

*   Ajoutez les fonctions de test avec les étapes suivantes :

    * **fundProposalNameViaProposal** → créez cette fonction et renommez-la pour correspondre au nom de la proposition.
    * **destinationAddress** → re-étiquetez ceci pour correspondre au nom de destination
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → ceci sera remplacé par la variable du fichier base-config
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → il s'agit de la variable que nous avons créée dans _**config/index.ts**_
    * _**createProposalNameProposal** → importez cette fonction ci-dessus pour être utilisée_
    * **fundProposalNameViaNoProposal** → créez cette fonction et renommez-la pour correspondre au nom de la proposition

\
    Exécutez par le code ci-dessous pour remplacer toutes ces variables par le nom de proposition et les variables existantes déjà créées ci-dessus :

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

b. **Ajoutez des fonctions de test dans le script de test**

Dans test/migrations/deploy-contracts-for-test.ts, nous allons ajouter les fonctions créées ci-dessus afin qu'elles soient incluses dans nos tests :

* Importez les fonctions créées

```typescript
test/migrations/deploy-contracts-for-test.ts
...
import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Ajoutez des tests pour les deux fonctions en créant une fonction de test générale → executeProposalNameProposalForTest, **remplacez le nom pour correspondre à la proposition**
* Nous appelons aussi la variable config **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** précédemment créée et le **PROPOSAL\_NAME\_ADDRESS** à partir de deployConfig

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

c. **Ajoutez un contrat aux aides de test**

Dans test/helpers/get-deployed-contracts-for-test.ts, ajoutez la fonction créée ci-dessus afin que les tests soient exécutés dans le test de fork du mainnet :

* Importez la fonction executeProposalNameProposalForTest à partir du fichier de migrations :

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

* Ajoutez la fonction à la fonction getDeployedContractsForTest(), en dehors de la dernière boucle else :

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

d. **Fichier de test final**

Enfin, nous ajoutons un test de hachage IPFS et de solde du multisig après la proposition fictive pour assurer que tout se termine comme prévu.

Dans test/misc, ajoutez un nouveau fichier avec le nom de proposition étiquté → proposal-name-proposal.spec.ts et remplissez avec ces deux tests :

1. Nous importons le hachage IPFS à partir de la lib par DIP\_NUMBER\_IPFS\_HASH
2. nous codons en dur le numéro de proposalId suivant en utilisant ProposalNameId
3. nous vérifions le hachage de proposition avec le hachage constant
4.  nous vérifions si le PROPOSAL\_NAME\_ADDRESS a un solde attendu du PROPOSAL\_FUNDING\_AMOUNT

**Remarque : si cette adresse a déjà la mention DYDX, vous devrez coder en dur dans le solde pour que le test passe**

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

7\. **Soumettre le PR**

Une fois que tous ces changements de code sont effectués et enregistrés localement, nous pouvons nous engager dans le référentiel forked et ouvrir un PR dans le référentiel dYdX pour examen :

a. **Validez les modifications par la ligne de commande**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **Soumettez un PR dans le référentiel dYdX**

<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">

c. **Attendez l'examen et l'approbation du gestionnaire de référentiel**

