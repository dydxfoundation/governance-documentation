---
description: >-
  本分步技术指南说明如何创建提案，将 ethDYDX 从社区资金库转至目标地址。

---

# 关于构建 dYdX 社区资金库支出提案的技术指南

Reverie 已编制一份综合性技术指南，通过拉取请求 (PR) 提交治理提案，将 $ethDYDX 从“社区资金库”转至 dYdX _治理合约_储存库。

要创建此提案，dYdX 社区成员必须拥有**至少 500 万治理代币** _（总供应的 0.5%）_的提案权（[短时间锁投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)的[提案阈值](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)）。

### 初步要求

须在完成拉取请求 (PR) 之前完成以下步骤：

1. **提案生命周期：**须按照提案[模板](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md)发布 DRC，并且必须有成功的快照投票。
2. **目标地址：** 目标地址必须提前生成。如果目标地址是多重签名，则必须创建多重签名钱包。
3. **GitHub 账户：** 用于分叉储存库的 GitHub 账户。
4. **转移金额（可选）：** 请求的转移金额最好是已在 PR 之前确定。但是，如果使用名义金额，可在审批前的最后一步设置该金额。
5. **DIP IPFS 哈希（可选）：** 如果转账金额已知，则应最终确定 DIP 并将其推送到 IPFS 以生成哈希。然而，如果金额尚未确定，可以在审批前的最后一步确定。

### 建立提案

1. **将** [**dYdX 治理合约储存库**](https://github.com/dydxfoundation/DIP) **分叉到您的 GitHub 账户。**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **克隆储存库，**将 \[username] 改为您自己的名称。

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **配置变量**

在 src/config/index.ts 中，将两个新变量添加到将用于测试目的的 configSchema 常量。在以下代码块中，将 **'PROPOSAL\_NAME'** 和 **'PROPOSAL'** 字段改为当前提交提案的名称。

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

在 src/deploy-config/base-config.ts 中，在 config 常量中添加目标地址和转移金额当作新变量：

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

**注**：按照 ERC20 标准，资金金额须**乘以 10^18**。如果金额未知，则可使用临时金额（例如 10 → 10000000000000000000）


在 src/lib/constants.ts 中，添加 IPFS 哈希变量，此变量将引用另一储存库中批准的 DIP：


```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**注**：如果 DIP 尚未发布，可以在测试中使用临时值（例如 ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\。**提案代码**

在 _**src/migrations**_ 中，创建一个以提案命名的新文件 → proposal-name.ts 并填充以下代码：

a. 在顶部添加所需的导入：

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

b.使用导入下方的提案名称，创建一个新函数，并添加以下代码和两个唯一变量：

* **destinationAddress** → 这将是接收资金的地址
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → 这是我们之前创建的变量，它将确定要转移的金额

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
5\. **部署任务**

创建提案后，可以编写部署，以生成提交提案所需的交易和调用数据。

在 _**tasks/deployment**_ 中，创建一个与提案代码同名的新文件 → proposal-name.ts 并填充以下代码：

a. 用以下变量添加所需的导入：


_**DIP\_NUMBER\_IPFS\_HASH**_ → 这是我们在 lib/constants 中添加的变量

_**createProposalNameProposal**_ → 这是我们在 /src/migrations/proposal-name 中创建的函数

```typescript
tasks/deployment/proposal-name.ts
import { types } from 'hardhat/config';
import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. 创建 hardhat 任务，并在任务开始行中填充提案信息。\
\
替换为'deploy:proposal-name:中的提案名称，并替换为'Proposal Description'中的简要描述。

最后一行调用从提案代码中导入的函数，所以需要调整。


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
6\. **构建测试**

既然已准备好部署代码，现在可以对提案构建一些测试。测试在本地执行，也使用主网分叉来模拟链上执行的提案。


a. **添加提案测试**

在 test/migrations 中，再次用提案名称添加一个新文件 → proposal-name.ts，并包括以下代码：


*   添加所需的导入，包括提案功能：

**createProposalNameProposal** → 这是我们在 /src/migrations/proposal-name 中创建的函数。\


**MOCK\_PROPOSAL\_IPFS\_HASH** → 我们将在测试中使用模拟哈希

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

*   在以下步骤添加测试函数：

    * **fundProposalNameViaProposal** → 创建此函数，并重命名以匹配提案名称。
    * **destinationAddress** → 将其重新标签，以匹配目标名称
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → 这将由 base-config 文件中的变量取代
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → 这是我们在 _**config/index.ts**_ 中创建的变量
    * _**createProposalNameProposal** → 导入以上函数待用_
    * **fundProposalNameViaNoProposal** → 创建此函数，重命名以匹配提案名称

\
    运行下面的代码，将所有这些变量替换为上面已经创建的提案名称和现有变量：

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

b. **将测试函数添加到测试脚本**

在 test/migrations/deploy-contracts-for-test.ts 中，我们将添加上面创建的函数，以使其包含在测试中：

* 导入创建的函数

```typescript
test/migrations/deploy-contracts-for-test.ts
...
import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* 添加这两个函数的测试，创建一般测试函数 → executeProposalNameProposalForTest **，更换名称以匹配提案**
* 我们还从 deployConfig 调用配置变量 **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL**（之前创建）和 **PROPOSAL\_NAME\_ADDRESS**

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

c. **添加合约到测试助手**

在 test/helpers/get-deployed-contracts-for-test.ts 中，添加上面创建的函数，以便测试在主网分叉测试中运行：

* 从迁移文件中导入 executeProposalNameProposalForTest 函数：

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

* 将该函数添加到 getDeployedContractsForTest() 函数中，在最后一个 else 循环之外：


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

d. **最终测试文件**

最后，我们在模拟提案之后添加了对 IPFS 哈希和多重签名余额的测试，以确保一切按预期结束。

在 test/misc 中，添加一个标有提案名称的新文件 → proposal-name-proposal.spec.ts 并填充以下两个测试：

1. 我们使用 DIP\_NUMBER\_IPFS\_HASH，从 lib 导入 IPFS Hash
2. 我们使用 ProposalNameId，对下一个 proposalId 编号进行硬编码
3. 我们用常量哈希检查提案哈希
4.  我们检查 PROPOSAL_NAME_ADDRESS，以确定其是否有 PROPOSAL_FUNDING_AMOUNT 的预期余额。

**注：如果该地址已经有 DYDX，则需要硬编码到余额中才能通过测试**

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

7\. **提交 PR**

我们完成所有代码修改并保存在本地后，就可以提交到分叉储存库，并向 dYdX 储存库提交 PR 以供审查：

a. **通过命令行提交更改**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **向 dYdX 储存库提交 PR**

<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">

c. **等待储存库经理的审批**

