---
description: >-
  Пошаговое техническое руководство по созданию предложения о переводе ethDYDX из казны сообщества на адрес назначения.
---

# Техническое руководство по созданию предложения о расходовании средств, находящихся в казне сообщества dYdX

Пользователь Reverie подготовил исчерпывающее техническое руководство по представлению предложения по управлению для перевода $ethDYDX из казны сообщества с помощью запроса на внесение изменений в репозиторий _контрактов на управление_ dYdX.

Чтобы создать это предложение, член сообщества dYdX должен иметь **не менее 5 млн токенов управления** _(0,5% от общего доступного количества токенов)_. Это [пороговое значение](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) для внесения предложений с целью [голосования с короткой блокировкой по времени](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor).

### Предварительные требования

Перед подачей запроса на внесение изменений необходимо сделать следующее:

1. **Жизненный цикл предложения.** Нужно опубликовать ЗК согласно [шаблону](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) предложения, а члены сообщества должны проголосовать за предложение на Snapshot.
2. **Адрес назначения.** Необходимо заранее создать адрес назначения. Если адрес назначения требует мультиподписи, нужно создать кошелек с мультиподписью.
3. **Учетная запись GitHub.** Необходима учетная запись GitHub для создания форка репозитория.
4. **Количество переводимых средств (необязательно).** Желательно установить переводимое количество средств до отправки запроса на внесение изменений. Однако если это значение условное, то количество средств можно установить прямо перед утверждением.
5. **Хэш IPFS ППУ (необязательно).** Если известно количество переводимых средств, то ППУ необходимо оформить и отправить в IPFS для генерации хэша. Однако если количество средств еще не определено, это можно сделать прямо перед утверждением.

### Создание предложения

1. **Создайте форк** [**репозитория governance-contracts dYdX**](https://github.com/dydxfoundation/DIP) **в своем аккаунте GitHub.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Клонируйте репозиторий** и укажите ваше имя пользователя вместо \[username].

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Переменные конфигурации**

Добавьте две новые переменные в константу configSchema в файле src/config/index.ts. Они будут использоваться для тестирования. В следующих блоках кода измените поля **PROPOSAL\_NAME** и **PROPOSAL** на название отправляемого предложения.

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

Добавьте адрес назначения и количество переводимых средств в качестве новых переменных в константу config в файле src/deploy-config/base-config.ts.

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

**Примечание**. Согласно стандарту ERC-20 количество переводимых средств нужно **умножить на 10^18**. Если количество средств еще неизвестно, можно указать временное значение (например, 10 → 10000000000000000000).

Добавьте переменную хэша IPFS, которая будет ссылаться на ППУ в другом репозитории, в файл src/lib/constants.ts:

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Примечание**. Если ППУ еще не было опубликовано, для тестирования можно указать временное значение (например, ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **Код предложения**

Создайте новый файл с названием предложения (proposal-name.ts) в файле _**src/migrations**_, а затем внесите в него следующий код:

а) Добавьте функции импорта в верхней части файла:

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

б) Создайте новую функцию, используя название предложения, ниже функций импорта и добавьте следующий код с двумя уникальными переменными:

* **destinationAddress** — это адрес, который получит переводимые средства.
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** — это созданная ранее переменная, которая определит количество переводимых средств.

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
5\. **Развертывание**

Создав предложение, мы можем написать код развертывания, который будет генерировать транзакцию и данные вызова, необходимые для отправки предложения.

В разделе _**tasks/deployment**_ создайте новый файл с тем же названием, что использовалось для кода предложения (proposal-name.ts), и внесите в него следующий код:

а) Добавьте необходимые функции импорта со следующими переменными:

_**DIP\_NUMBER\_IPFS\_HASH**_ — это переменная, которую мы добавляем в раздел lib/constants.

_**createProposalNameProposal**_ — это функция, которую мы создали в разделе /src/migrations/proposal-name.

```typescript
tasks/deployment/proposal-name.ts
import { types } from 'hardhat/config';
import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

б) Создайте задачу hardhat и внесите информацию о предложении в ее первую строку. \
\
Укажите название предложения вместо proposal-name в ‘deploy:proposal-name:’, а затем введите краткое описание в ‘Proposal Description’.

Последняя строка вызывает функцию, которую вы импортировали из кода предложения, поэтому ее нужно будет скорректировать.

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
6\. **Создание тестов**

Теперь, когда код готов к развертыванию, пришло время создать несколько тестов для предложения. Тестирование проводится как локально, так и с помощью форка мейннета для моделирования выполнения предложения в цепочке.

а) **Добавьте тесты предложения**

Снова добавьте новый файл с названием предложения в раздел test/migrations и внесите в него следующий код:

*   Добавьте необходимые функции импорта, включая функции предложения:

**createProposalNameProposal** — это функция, которую мы создали в разделе /src/migrations/proposal-name. \


**MOCK\_PROPOSAL\_IPFS\_HASH** — это имитация хэша для тестирования.

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

*   Добавьте функции тестирования, сделав следующее:

    * **fundProposalNameViaProposal** — создайте эту функцию и переименуйте ее, чтобы ее название совпадало с названием предложения.
    * **destinationAddress** — измените этот параметр, чтобы он совпадал с названием назначения.
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** — этот параметр будет заменен переменной из файла base-config.
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** — это переменная, которую мы создали в файле _**config/index.ts**_.
    * _**createProposalNameProposal** — импортируйте эту функцию выше для использования._
    * **fundProposalNameViaNoProposal** — создайте эту функцию и переименуйте ее, чтобы ее название совпадало с названием предложения.

\
    Выполните приведенный ниже код, чтобы заменить все эти переменные и существующие переменные, уже созданные выше, на название предложения:

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

б) **Добавьте функции тестирования в тестовый сценарий**

В файл test/migrations/deploy-contracts-for-test.ts мы добавим функции, созданные выше, чтобы включить их в наши тесты:

* Импортируйте созданные функции

```typescript
test/migrations/deploy-contracts-for-test.ts
...
import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Добавьте тесты для обеих функций, создав общую функцию тестирования executeProposalNameProposalForTest. **Переименуйте ее так, чтобы ее название совпадало с названием предложения**.
* Мы также вызываем ранее созданную переменную конфигурации **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** и **PROPOSAL\_NAME\_ADDRESS** из deployConfig.

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

в) **Добавьте контракт для тестирования**

Добавьте функцию, созданную выше, в файл test/helpers/get-deployed-contracts-for-test.ts, чтобы тесты запускались в рамках тестирования форка мейннета:

* Импортируйте функцию executeProposalNameProposalForTest из файла переноса:

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

* Добавьте эту функцию в getDeployedContractsForTest() вне последнего цикла else:

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

г) **Окончательный тестовый файл**

Наконец, мы добавляем проверку хэша IPFS и баланса мультиподписи после имитации предложения, чтобы убедиться, что все завершится так, как ожидалось.

Добавьте новый файл proposal-name-proposal.spec.ts с названием предложения в раздел test/misc, а затем включите в него следующие два теста:

1. Мы импортируем хэш IPFS из lib с помощью DIP\_NUMBER\_IPFS\_HASH.
2. Мы жестко кодируем следующий номер proposalId с помощью ProposalNameId.
3. Мы проверяем хэш предложения с помощью константы Hash.
4.  Мы проверяем PROPOSAL\_NAME\_ADDRESS на предмет наличия ожидаемого баланса PROPOSAL\_FUNDING\_AMOUNT.

**Примечание. Если у этого адреса уже есть DYDX, вам потребуется жестко закодировать баланс для завершения теста.**

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

7\. **Отправка запроса на внесение изменений**

После внесения всех изменений в код и их локального сохранения мы можем зафиксировать форк репозитория и отправить запрос на внесение изменений в репозиторий dYdX для рассмотрения:

а) **Зафиксируйте изменения с помощью командной строки**.

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

б) **Отправьте запрос на внесение изменений в репозиторий dYdX**.

<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">

в) **Дождитесь рассмотрения и одобрения со стороны менеджера репозитория**.

