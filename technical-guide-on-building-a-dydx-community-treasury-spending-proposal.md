---
description: >-
  ethDYDXをコミュニティトレジャリーから宛先アドレスに送り込む方法に関する技術的な、ステップバイステップガイド。
---

# dYdXコミュニティトレジャリー支出提案の構築に関するテクニカルガイド

Reverieは、dYdX_ガバナンスコントラクト_リポジトリに、$ethDYDXをプルリクエスト（PR）を通じてコミュニティトレジャリーから送り込むガバナンス提案を提出するための、包括的な技術的ガイドをまとめました。

この提案を作成するには、dYdXコミュニティメンバーは、提案力の**少なくとも5Mガバナンストークン**_（総供給の0.5％）_（[短いタイムロック投票](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)の[提案のしきい値](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)）を持っている必要があります。

### 予備要件

プルリクエスト（PR）の完了に先立ち、以下のステップを完了する必要があります：

1. **提案ライフサイクル：**DRCは提案[テンプレート](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md)に従って掲載し、スナップショット投票が成功する必要があります。
2. **宛先アドレス：**宛先アドレスは、事前に生成する必要があります。宛先アドレスがマルチシグの場合、マルチシグウォレットを作成する必要があります。
3. **GitHub口座：**リポジトリをフォークするためのGitHubアカウントです。
4. **送金額（オプション）：**希望される場合、リクエストされた送金額は、PRに先駆けて確立されています。ただし、概金額を使用する場合、承認前に最終ステップとして設定できます。
5. **DIP IPFSハッシュ（オプション）：**金額がわかっている場合、DIPは最終的に決定され、IPFSにプッシュし、ハッシュを生成する必要があります。ただし、金額が確定していない場合は、承認前の最終段階として設定することが可能です。

### 提案の構築

1. [**dYdXガバナンスコントラクトリポジトリ**](https://github.com/dydxfoundation/DIP)を**GitHub口座に****フォーク**してください。

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **リポジトリをクローン**し、\[username]を自分自身に変更してください。

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **構成**変数

src/config/index.tsに、テストのために使用されるconfigSchema定数に2つの新しい変数を追加します。以下のコードブロックで、**「PROPOSAL\_NAME」**と「PROP**OSAL」**フィールドを、送信する提案の名前に変更します。

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

src/deploy-config/base-config.tsに、config定数に宛先アドレスと金額を新しい変数として追加します：

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

**注**：金額は、ERC20標準あたり**10 ^ 18に乗じ**る必要があります。金額がまだわからない場合、一時金額を使用できます（例： 10 → 10000000000000000000）

src/lib/constants.tsに、他のリポジトリで承認されたDIPを参照するIPFSハッシュ変数を追加します：

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**注**：DIPがまだ公開されていない場合は、テスト用に仮の値（例：‘0x0000000000000000000000000000000000000000000000000000000000000000’)\を使用することができます。


4\.**提案コード**

_**src/migrations**_で、proposal → proposal-name.tsにちなんで名前を付けた新しいファイルを作成し、以下のコードを入力します：

a. 上部に必要なインポートを追加します：

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

b. インポート以下の提案名を使用して新しい関数を作成し、以下のコードを2つのユニークな変数で追加します：

* **destinationAddress** → これは、資金を受け取るアドレスです
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → これは、私たちが以前に作成した変数です。これは、送金する金額を決定します

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
5\. **デプロイメントタスク**

提案が作成されると、提案を送信するために必要なトランザクションとコールデータを生成するデプロイメントを書くことができます。

_**tasks/deployment**_で、提案コード → proposal-name.tsに使用する同じ名前の新しいファイルを作成し、以下のコードで入力します：

a. 以下の変数で必要なインポートを追加します：

_**DIP\_NUMBER\_IPFS\_HASH**_ → これは、lib/constantsに追加する変数です

_**createProposalNameProposal**_ → これは、/src/migrations/proposal-nameで作成した関数です

```typescript
tasks/deployment/proposal-name.ts
import { types } from 'hardhat/config';
import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. hardhatタスクを作成し、タスクの開始\\行に提案情報を入力しますdeploy:proposal-name:のproposal-nameに置き換え、「Proposal Description」の簡単な説明に置き換えます。

最後の行は、提案コードからインポートした関数を呼び出すため、その調整が必要です。

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
6\. **テストの構築**

コードをデプロイメントする準備ができたので、提案を中心にいくつかのテストを構築します。テストは、ローカルとメインネットフォークを使用して、オンチェーンで実行される提案をシミュレートします。

a. **提案テストの追加**

test/migrationsに、proposal name → proposal-name.tsで新しいファイルをもう一度追加し、以下のコードを含めます：

*   提案関数を含め、必要なインポートを追加します：

**createProposalNameProposal** → これは、/src/migrations/proposal-nameで作成した関数です。\


**MOCK\_PROPOSAL\_IPFS\_HASH** → テストのためにモックハッシュを使用します。

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

*   テスト関数を以下のステップで追加します：

    * **fundProposalNameViaProposal** → この関数を作成し、提案名に一致する名前を変更します。
    * **destinationAddress** → 宛先名にマッチするようにラベル付けします。
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → これは、base-configファイルからの変数に置き換えられます。
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → これは、_**config/index.ts**_で作成した変数です。
    * _**createProposalNameProposal** → 上記の関数を使用するためにインポートしました。_
    * **fundProposalNameViaNoProposal** → この関数を作成し、提案名に一致する名前を変更します。

\以下のコードを通じて、これらの変数すべてを提案名と既存の変数に置き換えます。

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

b. **テストスクリプトにテスト関数を追加する**

test/migrations/deploy-contracts-for-test.tsに、上記の関数を追加します：

* 作成した関数をインポートする

```typescript
test/migrations/deploy-contracts-for-test.ts
...
import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* 一般的なテスト関数 → executeProposalNameProposalForTestを作成し、両方の関数にテストを追加し、**提案に一致する名前を置き換えます**。
* また、これまで作成した設定変数**TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL**と、deployConfigから**PROPOSAL\_NAME\_ADDRESS**を呼び出します。

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

c. **テストヘルパーにコントラクトを追加する**

test/helpers/get-deployed-contracts-for-test.tsに、上記の関数を追加し、メインネットフォークテストでテストが実行されるようにします。

* executeProposalNameProposalForTest関数をマイグレーションファイルからインポートします。

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

* getDeployedContractsForTest()関数に関数を追加します:

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

d. **最終テストファイル**

最後に、モック提案の後、IPFSハッシュとマルチシグの残高のテストを追加し、すべてが予想通りに終了するようにします。

test/miscに、「proposal name labelled → proposal-name-proposal.spec.ts（提案名ラベル付き → 提案名-提案.spec.ts）」と書かれた新しいファイルを追加し、これらの2つのテストを記入します。

1. IPFSハッシュは、DIP\_NUMBER\_IPFS\_HASHを通じてlibからインポートします。
2. ProposalNameIdを使用して、次のproposalId番号をハードコードします。
3. 提案ハッシュは、定数ハッシュでチェックします。
4.  PROPOSAL\_NAME\_ADDRESSをチェックし、PROPOSAL\_FUNDING\_AMOUNTの残高が予想されているかどうか確認します。

**注：このアドレスにdYdXがすでに存在する場合、テストに合格する残高にハードコードする必要があります。**

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

7\. **PRの送信**

これらのコード変更がすべて行われ、ローカルに保存されたら、フォークされたリポジトリにコミットし、dYdXリポジトリにPRを開くことができます。

a. **コマンドラインを通じて変更をコミットする**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b.**dYdXリポジトリにPRを送信する**

<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">

c. **リポジトリマネージャーからのレビューと承認を待つ**

