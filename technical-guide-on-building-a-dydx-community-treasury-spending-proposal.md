---
description: >-
  A technical, step-by-step guide on how to create a proposal to transfer DYDX
  from the community treasury to a destination address.
---

# Technical Guide on building a dYdX Community Treasury Spending Proposal

Reverie has put together a comprehensive, technical guide for submitting a governance proposal to transfer DYDX from the Community Treasury through a Pull Request (PR) to the dYdX _governance-contracts_ repository.&#x20;

To create this proposal, a  dYdX community member must have **at least 5M DYDX** _(0.5% of total supply)_ of proposal power ([proposal threshold](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) for a [short timelock vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)).

### Preliminary Requirements

The following steps must be completed ahead of completing the Pull Request (PR):

1. **Proposal Lifecycle:** The DRC must be posted following the proposal [template](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md)  and there must be a successful Snapshot vote.
2. **Destination Address:** The destination address must be generated ahead of time. If the destination address is a multi-sig, the multi-sig wallet must be created.
3. **GitHub account:** A GitHub account to fork the repository.
4. **Transfer Amount (Optional):** Preferably, the requested transfer amount has been established ahead of the PR. However, if using a notional amount, it can be set as a final step prior to approval.
5. **DIP IPFS Hash (Optional):** If the transfer amount is known, the DIP should be finalized and pushed to IPFS to generate it’s hash. However, this can be set a final step prior to approval if the amount is not yet determined.

### Building the Proposal

1. **Fork the** [**dYdX governance-contracts repository**](https://github.com/dydxfoundation/DIP) **to your GitHub account.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Clone the Repository,** and change the \[username] to your own.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Configuration Variables**

In src/config/index.ts, add two new variables to the configSchema constant that will be used for testing purposes. In the following code blocks, change the **'PROPOSAL\_NAME'** and **'PROPOSAL'** fields to the name of the proposal being submitted.

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

In src/deploy-config/base-config.ts, add the destination address and transfer amount as new variables in the config constant:

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

**Note**: The funding amount will need to be **multiplied by 10^18** per ERC20 standard. If the amount is not yet known, a temporary amount can be used (e.g. 10 → 10000000000000000000)

In src/lib/constants.ts, add the IPFS hash variable that will reference the DIP approved in the other repository:

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found 
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Note**: If the DIP hasn’t been published yet, a temporary value can be used for testing (e.g. ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **Proposal code**

In _**src/migrations,**_ create a new file named after the proposal → proposal-name.ts and populate with the following code:

a. Add the imports needed at the top:

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

b. Create a new function using the proposal name below the imports and add the following code with two unique variables:

* **destinationAddress** → this will be the address that receives the funding
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → this is the variable we created earlier that will determine the amount to be transferred

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
5\. **Deployment Task**

With the proposal created, we can write the deployment that will generate the transaction and calldata needed to submit the proposal.

In _**tasks/deployment,**_ create a new file with the same name used for the proposal code → proposal-name.ts and populate with the following code:

a. Add the imports needed with the following variables:

_**DIP\_NUMBER\_IPFS\_HASH**_ → this is the variable we add in lib/constants

_**createProposalNameProposal**_ → this is the function we created in /src/migrations/proposal-name

```typescript
tasks/deployment/proposal-name.ts

import { types } from 'hardhat/config';

import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. Create the hardhat task and populate it with the proposal information on the task opening line. \
\
Replace with the proposal-name in ‘deploy:proposal-name: and replace with a brief description in ‘Proposal Description’.

The last line calls the function you imported from the proposal code, so that will need to be adjusted.

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
6\. **Building tests**

Now that the code is ready for deployment, it’s time to build some tests around the proposal. Testing is done both locally and using a mainnet fork to simulate a proposal being executed on-chain.

a. **Add Proposal Tests**

In test/migrations, add a new file again with the proposal name → proposal-name.ts and include the following code:

*   Add the imports needed including the proposal functions:

    **createProposalNameProposal** → this is the function we created in /src/migrations/proposal-name.\


    **MOCK\_PROPOSAL\_IPFS\_HASH** → we’ll use a mock hash for testing purposes

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

*   Add the testing functions with the following steps:

    * **fundProposalNameViaProposal** → create this function and rename it to match the proposal name.
    * **destinationAddress** → re-label this to match the destination name
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → this will be replaced by the variable from the base-config file
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → this is the variable we created in _**config/index.ts**_
    * _**createProposalNameProposal** → imported this function above to be used_
    * **fundProposalNameViaNoProposal** → create this function and rename it to match the proposal name

    \
    Run through the code below to replace all these variables with the proposal name and existing variables already created above:

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

b. **Add Testing Functions to Test Script**

In test/migrations/deploy-contracts-for-test.ts, we’ll add the functions created above so they are included in our tests:

* Import the functions created

```typescript
test/migrations/deploy-contracts-for-test.ts

...

import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Add tests for both functions by creating a general testing function → executeProposalNameProposalForTest, **replace the name to match the proposal**
* We also call the config variable **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** previously created and the **PROPOSAL\_NAME\_ADDRESS** from deployConfig

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

c. **Add contract to Testing helpers**

In test/helpers/get-deployed-contracts-for-test.ts, add the function created above so that the tests are run in the mainnet fork testing:

* Import the executeProposalNameProposalForTest function from the migrations file:

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

* Add the function to the getDeployedContractsForTest() function, outside of the last else loop:

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

d. **Final Test file**

Finally, we add a test of both the IPFS hash and the balance of the multisig after the mock proposal to ensure everything ends up as expected.&#x20;

In test/misc, add a new file with the proposal name labelled → proposal-name-proposal.spec.ts and populate with these two tests:

1. We import the IPFS Hash from lib through DIP\_NUMBER\_IPFS\_HASH
2. we hardcode the next proposalId number using ProposalNameId
3. we check the proposal hash with the constant Hash
4.  we check the PROPOSAL\_NAME\_ADDRESS to see if it has an expected balance of the PROPOSAL\_FUNDING\_AMOUNT

    **Note: if this address already has DYDX, you will need to hardcode into the balance for the test to pass**

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

7\. **Submitting the PR**

Once all these code changes are made and saved locally, we can commit to the forked repository and open a PR to the dYdX repository for review:

a. **Commit the changes through the command line**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **Submit a PR to the dYdX repository**

****<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">****

c. **Wait for review and approval from the repository manager**

