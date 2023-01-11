---
description: >-
  커뮤니티 트레저리에서 목적지 주소로 DYDX를 전송하기 위한 계획안을 작성하는 방법에 대한 기술적인 단계별 가이드입니다.
---

# dYdX 커뮤니티 트레저리 지출 계획안 작성에 대한 기술 가이드

Reverie는 풀 리퀘스트(PR)를 이용하여 DYDX를 커뮤니티 트레저리에서 dYdX _거버넌스 계약 리포지토리_로 전송하기 위한 거버넌스 계획안을 제출하기 위한 포괄적인 기술 가이드를 작성했습니다.

이 계획안을 작성하려면, dYdX 커뮤니티 구성원은 **적어도 5M DYDX**_(총 공급량의 0.5%)_의 계획안 권한([단기 타임락 투표](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)를 위한 [계획안 임계값](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters))을 가져야 합니다.

### 예비 요건

풀 리퀘스트(PR)를 완료하기 전에 다음 단계를 완료해야 합니다.

1. **계획안 수명 주기:** DRC는 계획안 [템플릿](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md)에 따라 게시되어야 하며 스냅샷 투표가 성공적이어야 합니다.
2. **목적지 주소:** 목적지 주소를 미리 생성해야 합니다. 목적지 주소가 다중 서명(multi-sig)인 경우, 다중 서명 지갑을 생성해야 합니다.
3. **GitHub 계정:** 리포지토리를 분기할 GitHub 계정입니다.
4. **송금액(옵션):** 요청된 송금액이 PR보다 먼저 설정되면 좋습니다. 하지만 명목상의 금액을 사용하는 경우에는 승인 전 최종 단계에서 설정할 수 있습니다.
5. **DIP IPFS 해시(옵션):** 송금액을 알면 DIP를 마무리하고 IPFS로 푸시하여 해시를 생성해야 합니다. 그러나, 아직 해당 금액이 확정되지 않은 경우 승인 전 최종 단계에서 설정할 수 있습니다.

### 계획안 작성

1. ****[**dYdX 거버너스 계약 리포지토리**](https://github.com/dydxfoundation/DIP)**를 사용자의 GitHub 계정으로 분기합니다.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **리포지토리 복제본을 만들고,** \[username]을 본인의 사용자 이름으로 변경합니다.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **구성 변수**

src/config/index.ts에서 테스트 목적으로 사용할 configSchema 상수에 두 개의 새로운 변수를 추가합니다. 다음 코드 블록애서, **'PROPOSAL\_NAME'** 및 **'PROPOSAL'** 필드를 제출 중인 계획안의 이름으로 변경합니다.

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

src/deploy-config/base-config.ts에서 목적지 주소와 송금액을 설정 상수의 새 변수로 추가합니다.

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

**참고**: 자금 금액은 ERC20 표준에 따라 **10^18을 곱해야 합니다**. 해당 금액이 아직 정해지지 않은 경우, 임시 금액을 사용할 수 있습니다(예: 10 → 10000000000000000000).

다른 리포지토리에서 승인된 DIP를 참조할 IPFS 해시 변수를 src/lib/constants.ts에 추가합니다.

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**참고**: DIP가 아직 게시되지 않은 경우 테스트에 임시 값을 사용할 수 있습니다(예: ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **계획안 코드**

_**src/migrations**_에, proposal-name.ts와 같이 계획안 이름의 새 파일을 다시 만들고 해당 파일에 다음 코드를 작성합니다.

a. 맨 위에 필요한 import를 추가합니다.

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

b. import 아래에서 계획안 이름을 사용하여 새 함수를 만들고 다음 코드를 두 개의 고유한 변수와 함께 추가합니다.

* **destinationAddress** → 자금을 받는 주소가 됩니다.
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → 이전에 생성한 변수로 송금할 금액을 결정합니다.

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
5\. **배포 작업**

계획안이 생성되면 계획안을 제출하는 데 필요한 트랜잭션 및 호출 데이터를 생성하는 배포를 작성할 수 있습니다.

_**tasks/deployment**_에서 계획안 코드에 사용된 proposal-name.ts 파일과 동일한 이름을 갖는 새 파일을 만들고 해당 파일에 다음 코드를 작성합니다.

a. 다음 변수에 필요한 import를 추가합니다.

_**DIP\_NUMBER\_IPFS\_HASH**_ → lib/constants에 추가하는 변수입니다.

_**createProposalNameProposal**_ → /src/migrations/proposal-name에서 생성했던 함수입니다.

```typescript
tasks/deployment/proposal-name.ts

import { types } from 'hardhat/config';

import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. hardhat 작업을 생성하고 작업 시작 줄에 있는 계획안 정보로 채웁니다. \
\
'deploy:proposal-name:'에 있는 proposal-name을 교체하고 ‘Proposal Description’을 간략한 설명으로 교체합니다.

마지막 줄은 계획안 코드에서 가져온 함수를 호출하므로 수정이 필요합니다.

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
6\. **테스트 빌드**

이제 코드를 배포할 준비가 되었으므로 계획안을 중심으로 몇 가지 테스트를 빌드할 차례입니다. 로컬에서 테스트를 진행하고 메인넷 포크를 사용하여 계획안이 온체인에서 실행되도록 시뮬레이션합니다.

a. **계획안 테스트 추가**

test/migrations에 proposal-name.ts과 같이 계획안 이름이 들어간 새 파일을 다시 추가하고 해당 파일에 다음 코드를 포함시킵니다.

* 다음 계획안 함수를 포함하여 필요한 import를 추가합니다.

**createProposalNameProposal**, /src/migrations/proposal-name에서 생성했던 함수입니다. \


**MOCK\_PROPOSAL\_IPFS\_HASH** → 테스트 목적에 맞게 모의 해시(mock hash)를 사용합니다.

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

* 다음 단계에 따라 테스트 함수를 추가합니다.

    * **fundProposalNameViaProposal** → 이 함수를 만들고 계획안 이름과 일치하도록 이름을 변경합니다.
    * **destinationAddress** → 목적지 이름과 일치하도록 레이블을 다시 지정합니다.
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → 이는 base-config 파일의 변수로 대체됩니다.
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → _**config/index.ts**_에서 생성한 변수입니다.
    * _**createProposalNameProposal** → 사용하려는 위의 함수를 가져왔습니다._
    * **fundProposalNameViaNoProposal** → 이 함수를 만들고 계획안 이름과 일치하도록 이름을 변경합니다.

\
    아래 코드를 실행하여 위에서 이미 생성한 계획안 이름 및 기존 변수로 이러한 모든 변수를 변경합니다.

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

b. **테스트 스크립트에 테스트 함수 추가**

위에서 만든 함수를 test/migrations/deploy-contracts-for-test.ts에 추가하여 테스트에 포함합니다.

* 생성한 함수 가져오기

```typescript
test/migrations/deploy-contracts-for-test.ts

...

import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* 일반 테스트 함수를 생성하여 두 함수에 대한 테스트 추가 → executeProposalNameProposalForTest, **계획안과 일치하도록 이름을 변경합니다.**
* 이전에 생성한 **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** 및 deployConfig의 **PROPOSAL\_NAME\_ADDRESS** 설정 변수도 호출합니다.

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

c. **테스트 도우미에 계약 추가**

테스트가 메인넷 분기 테스트에서 실행되도록 test/helpers/get-deployed-contracts-for-test.ts에 위에서 만든 함수를 추가합니다.

* 다음 마이그레이션 파일에서 executeProposalNameProposalForTest 함수를 가져옵니다.

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

* 마지막 else 루프 외부에 있는 getDeployedContractsForTest() 함수에 이 함수를 추가합니다.

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

d. **최종 테스트 파일**

마지막으로 모의 계획안을 실행한 후 IPFS 해시와 다중 서명의 잔액에 대한 테스트를 추가하여 모든 것이 예상대로 종료되는지 확인합니다.

test/misc에 계획안 이름이 proposal-name-proposal.spec.ts인 새 파일을 추가하고 다음 두 테스트로 채웁니다.

1. DIP\_NUMBER\_IPFS\_HASH를 통해 lib에서 IPFS 해시를 가져옵니다.
2. ProposalNameId를 사용하여 다음 번 proposalId 번호를 하드코딩합니다.
3. 해시 상수로 계획안 해시를 확인합니다.
4. PROPOSAL\_NAME\_ADDRESS를 확인하여 PROPOSAL\_FUNDING\_AMOUNT의 예상 잔액이 있는지 확인합니다.

**참고: 이 주소에 이미 DYDX가 있는 경우 테스트를 통과하려면 잔액에 하드코딩해야 합니다.**

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

7\. **PR 제출**

이러한 모든 코드 변경이 완료되고 로컬에 저장되면 분기된 리포지토리에 커밋하고 dYdX 리포지토리에 대한 PR을 열어 다음과 같이 검토할 수 있습니다.

a. **명령줄을 통해 변경 사항을 커밋합니다.**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **dYdX 리포지토리에 PR을 제출합니다.**

****<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">****

c. **리포지토리 관리자의 검토 및 승인을 기다립니다.**

