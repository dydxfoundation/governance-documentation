---
description: >-
  Topluluk hazinesinden bir hedef adrese DYDX aktarmak için bir teklifin nasıl oluşturulacağına dair teknik, adım adım bir kılavuz.
---

# dYdX Topluluk Hazinesi Harcama Teklifi Oluşturmak için Teknik Kılavuz

Reverie, Topluluk Hazinesinden DYDX aktarmak amacıyla dYdX _yönetişim sözleşmeleri_ repository'sine bir Çekme İsteği (PR) yapmak için yönetişim teklifi gönderilmesi hakkında kapsamlı, teknik bir kılavuz hazırladı.

Bu teklifi oluşturabilmesi için, bir dYdX topluluğu üyesinin, teklif gücünün **en az 5 milyon DYDX'ine** _(toplam arzın %0,5'i)_ sahip olması gerekir ([short timelock oylama](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor) için [teklif eşiği](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)).

### Ön Koşullar

Çekme Talebi (PR) tamamlanmadan önce aşağıdaki adımlar tamamlanmalıdır:

1. **Teklif Yaşam Döngüsü:** Teklif [şablonunun](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) ardından DRC gönderilmeli ve başarılı bir Snapshot oylaması gerçekleştirilmelidir.
2. **Hedef Adresi:** Hedef adresi, zamanı gelmeden oluşturulmalıdır. Hedef adresi bir multi-sig (çok imzalı adres) ise, multi-sig cüzdanı oluşturulmalıdır.
3. **GitHub hesabı:** Repository'yi fork etmek için bir GitHub hesabı.
4. **Transfer Miktarı (İsteğe Bağlı):** Tercihen PR öncesinde istenen transfer miktarı belirlenmelidir. Bununla birlikte, bir itibari (notional) miktar kullanılıyorsa, onay öncesinde son adım olarak belirlenebilir.
5. **DIP IPFS Karması (İsteğe Bağlı):** Transfer miktarı biliniyorsa, DIP kesinleştirilip IPFS'ye push edilerek karması (hash) oluşturulmalıdır. Bununla birlikte, miktar henüz belirlenmemişse, onay öncesinde son adımda belirlenebilir.

### Teklifin Oluşturulması

1. [**dYdX yönetişim-sözleşmeleri repository**](https://github.com/dydxfoundation/DIP)'sini **GitHub hesabınıza** **fork edin**.

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Repository'yi klonlayın** ve \[kullanıcı adı] kısmını kendi kullanıcı adınızla değiştirin.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Yapılandırma Değişkenleri**

src/config/index.ts dosyasında test amaçları için kullanılacak configSchema sabitine iki yeni değişken ekleyin. Aşağıdaki kod bloklarında **'PROPOSAL\_NAME'** ve **'PROPOSAL'** alanlarını gönderilecek teklifin adı olarak değiştirin.

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

src/deploy-config/base-config.ts dosyasında, config sabitine iki yeni değişken olarak hedef adresini ve transfer miktarını ekleyin:

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

**Not**: ERC20 standardı gereğince fonlama miktarının **10^18 ile çarpılması** gerekecektir. Miktar henüz bilinmiyorsa, geçici bir miktar kullanılabilir (ör. 10 → 10000000000000000000)

src/lib/constants.ts dosyasına, diğer repository'de onaylanan DIP'ye referans verecek IPFS karma değişkenini ekleyin:

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Not**: DIP henüz yayınlanmadıysa, test için geçici bir değer kullanılabilir (ör. ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **Teklif kodu**

_**src/migrations**_ dizininde teklifin adını taşıyan yeni bir dosya oluşturun → teklifin-adı.ts ve bu dosyaya aşağıdaki kodu ekleyin:

a. En üste gereken importları ekleyin:

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

b. importların altında teklifin adını kullanarak yeni bir fonksiyon oluşturun ve şu iki benzersiz değişkeni içeren aşağıdaki kodu ekleyin:

* **destinationAddress** → bu, varlığı (parayı, fonu) alan adres olacaktır
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → bu, daha önce oluşturduğumuz ve aktarılacak miktarı belirleyecek değişkendir

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
5\. **Deployment (Devreye Alma) Görevi**

Teklif oluşturulduktan sonra teklifin gönderilmesi için gereken işlemi ve çağrı verilerini (calldata) oluşturacak deployment'ı yazabiliriz.

_**tasks/deployment**_ dizininde teklif kodu için kullanılanla aynı adı taşıyan yeni bir dosya oluşturun → teklifin-adı.ts ve içine aşağıdaki kodu ekleyin:

a. Aşağıdaki değişkenlerle beraber gereken importları ekleyin:

_**DIP\_NUMBER\_IPFS\_HASH**_ → bu, lib/constants içine eklediğimiz değişkendir

_**createProposalNameProposal**_ → bu, /src/migrations/teklifin-adı içinde oluşturduğumuz fonksiyondur

```typescript
tasks/deployment/proposal-name.ts

import { types } from 'hardhat/config';

import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. Hardhat görevini oluşturun ve içine görev açılış satırındaki teklif bilgilerini ekleyin. \
\
‘deploy:proposal-name:‘in yerine teklifin adını girin ve ‘Proposal Description’ın yerine kısa bir açıklama girin.

Son satırda, teklif kodundan import ettiğiniz fonksiyon çağrılır; bu nedenle bunun da değiştirilmesi gerekir.

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
6\. **Testlerin hazırlanması**

Kod devreye alıma (deployment) hazır olduğuna göre, artık teklif üzerinde bazı testler oluşturma zamanı geldi. Testler hem yerel olarak yapılır, hem de zincir üzerinde yürütülen bir teklifi simüle etmek için bir mainnet forku kullanılarak yapılır.

a. **Teklif Testleri Ekleyin**

test/migrations dizininde teklifin adını taşıyan yeni bir dosya oluşturun → teklifin-adı.ts ve içine aşağıdaki kodu ekleyin:

* Teklif fonksiyonları dahil olmak üzere gereken importları ekleyin:

**createProposalNameProposal** → bu, /src/migrations/teklifin-adı içinde oluşturduğumuz fonksiyondur. \


**MOCK\_PROPOSAL\_IPFS\_HASH** → test için bir sahte (mock) karma (hash) kullanacağız

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

* Test fonksiyonlarını aşağıdaki adımlarla ekleyin:

    * **fundProposalNameViaProposal** → bu fonksiyonu oluşturun ve adını teklifin adına uyacak şekilde değiştirin.
    * **destinationAddress** → hedefin adına uyacak şekilde adını değiştirin
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → bu, base-config dosyasındaki değişkenle değiştirilmelidir
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → bu, _**config/index.ts**_ içinde oluşturduğumuz değişkendir
    * _**createProposalNameProposal** → bu fonksiyonu, kullanılması için yukarıda import etmiştik_
    * **fundProposalNameViaNoProposal** → bu fonksiyonu oluşturun ve adını teklifin adına uyacak şekilde değiştirin

\
    Aşağıdaki kodu gözden geçirin ve buradaki tüm değişkenleri, teklifin adıyla ve yukarıda oluşturulmuş mevcut değişkenler ile değiştirin:

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

b. **Test Komut Dizisine (Test Script) Test Fonksiyonlarını Ekleyin**

test/migrations/deploy-contracts-for-test.ts dosyasının içine yukarıda oluşturulan fonksiyonları ekleyerek testlerimize dahil edeceğiz:

* Oluşturulan fonksiyonları import edin

```typescript
test/migrations/deploy-contracts-for-test.ts

...

import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Genel bir test fonksiyonu oluşturarak her iki fonksiyon için de testler ekleyin → executeProposalNameProposalForTest; **bu fonksiyonun adını teklif adı ile uyacak şekilde değiştirin**
* Ayrıca daha önce oluşturulan config değişkeni **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL**'ı ve deployConfig'den **PROPOSAL\_NAME\_ADDRESS**'i çağıracağız

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

c. **Test yardımcılarına sözleşme ekleyin**

test/helpers/get-deployed-contracts-for-test.ts dosyasına yukarıda oluşturulan fonksiyonu ekleyerek testlerin mainnet fork testinde çalıştırılmasını sağlayın:

* migrations dosyasından executeProposalNameProposalForTest fonksiyonunu import edin:

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

* Bu fonksiyonu son else döngüsünün dışında, getDeployedContractsForTest() fonksiyonuna ekleyin:

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

d. **En Son Test dosyası**

Son olarak, her şeyin beklendiği gibi sonuçlanmasını sağlamak için sahte (mock) tekliften sonra hem IPFS karması hem de multisig bakiyesi (balance) için bir test ekliyoruz.

test/misc dizinine teklifin adı ile etiketlenmiş yeni bir dosya ekleyin → teklifin-adı-proposal.spec.ts ve dosya içine aşağıdaki iki testi ekleyin:

1. DIP\_NUMBER\_IPFS\_HASH üzerinden lib'deki IPFS Hash'i import ediyoruz
2. ProposalNameId'yi kullanarak bir sonraki proposalId numarasını doğrudan kodun içine ekliyoruz
3. teklif karmasının sabit Karma'ya eşit olup olmadığını kontrol ediyoruz
4. PROPOSAL\_NAME\_ADDRESS içindeki bakiyenin (balance) beklendiği gibi PROPOSAL\_FUNDING\_AMOUNT bakiyesine (balance) eşit olup olmadığını kontrol ediyoruz

**Not: Bu adreste zaten DYDX varsa, testten geçmek için bakiyeye (balance) doğrudan kodun içine eklemeniz gerekecektir**

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

7\. **PR (Pull Request) gönderilmesi**

Tüm bu kod değişiklikleri yapılıp yerel olarak kaydedildikten sonra, fork edilen repository'ye commit yapabilir ve gözden geçirilmesi için dYdX repository'sine bir PR gönderebiliriz:

a. **Değişiklikleri komut satırından commit edin**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **dYdX repository'sine bir PR gönderin**

****<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">****

c. **Repository yöneticisinin kontrol ve onayını bekleyin**

