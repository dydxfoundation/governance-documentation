---
description: >-
  Um guia técnico e passo a passo sobre como criar uma proposta para transferir ethDYDX do tesouro da comunidade para um endereço de destino.
---

# Guia técnico sobre a criação de uma proposta de gastos do Tesouro da Comunidade da dYdX

A Reverie criou um guia técnico e abrangente para enviar uma proposta de governança a fim de transferir $ethDYDX do Tesouro da Comunidade por meio de uma solicitação pull (PR, na sigla em inglês) ao repositório _governance-contracts_ da dYdX.

Para criar essa proposta, um membro da comunidade dYdX precisa ter **pelo menos 5M de tokens de governança** _(0,5% do total do fornecimento)_ em poder proposicional ([limite de proposta](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) para um [voto de timelock curto](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)).

### Requisitos preliminares

As etapas a seguir devem ser concluídas antes da solicitação de pull (PR):

1. **Ciclo de vida** da proposta: a DRC deve ser postada conforme o [modelo](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) de proposta e precisa haver uma votação de Snapshot bem-sucedida.
2. **Endereço de destino:** o endereço de destino deve ser gerado com antecedência. Se o endereço de destino for uma carteira multi-sig, ela deve ser criada.
3. **Conta do GitHub:** uma conta do GitHub para fazer o fork do repositório.
4. **Valor da transferência (opcional):** de preferência, o valor da transferência solicitada precisa ser estabelecido antes do PR. No entanto, se estiver usando um valor referencial, ele poderá ser definido como uma etapa final antes da aprovação.
5. **Hash do IPFS (opcional):** se a valor da transferência for conhecido, o DIP deve ser finalizado e enviado para o IPFS a fim de gerar o hash. No entanto, isso pode ser definido em uma etapa final antes da aprovação se o valor ainda não foi determinado.

### Como criar a proposta

1. **Faça o fork do** [**repositório governance-contracts da dYdX**](https://github.com/dydxfoundation/DIP) **em sua conta do GitHub.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Clone o repositório** e altere \[username] no seu repositório.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Variáveis de configuração**

Em src/config/index.ts, adicione duas novas variáveis à constante configSchema que será usada para fins de teste. Nos blocos de código a seguir, altere os campos **'PROPOSAL\_NAME'** e **'PROPOSAL'** para o nome da proposta que será enviada.

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

Em src/deploy-config/base-config.ts, adicione o endereço de destino e o valor da transferência como novas variáveis na constante config:

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

**Observação**: o valor de financiamento precisará ser **multiplicado por 10^18** conforme o padrão ERC20. Se valor ainda não for conhecido, um valor temporário pode ser usado (por exemplo, 10 → 10000000000000000000)

Em src/lib/constants.ts, adicione a variável hash IPFS que fará referência ao DIP aprovado no outro repositório:

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Observação**: se o DIP ainda não tiver sido publicado, um valor temporário pode ser usado para testes (por exemplo, ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **Código de proposta**

Em _**src/migrations,**_ crie um novo arquivo com o nome da proposta → proposal-name.ts e preencha o código a seguir:

a. Adicione as importações necessárias no topo:

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

b. Crie uma nova função usando o nome da proposta abaixo das importações e adicione o código a seguir com duas variáveis exclusivas:

* **destinationAddress** → este será o endereço que recebe os fundos
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → esta é a variável que criamos anteriormente que determinará valor a ser transferido

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
5\. **Tarefa de implantação**

Com a proposta criada, podemos escrever a implementação que gerará a transação e os dados de chamada necessários para enviar a proposta.

Em _**tasks/deployment,**_ crie um novo arquivo com o mesmo nome usado para o código da proposta → proposal-name.ts e preencha o código a seguir:

a. Adicione as importações necessárias com as seguintes variáveis:

_**DIP\_NUMBER\_IPFS\_HASH**_ → esta é a variável que adicionamos em lib/constants

_**createProposalNameProposal**_ → esta é a função que criamos em /src/migrations/proposal-name

```typescript
tasks/deployment/proposal-name.ts
import { types } from 'hardhat/config';
import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. Crie a tarefa hardhat e preencha-a com as informações da proposta na linha de abertura da tarefa. \
\
Substitua com o nome da proposta em ‘deploy:proposal-name‘ e substitua por uma breve descrição em ‘Descrição da proposta’.

A última linha chama a função que você importou do código da proposta, portanto será preciso ajustá-la.

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
6\. **Testes de construção**

Agora que o código está pronto para a implantação, é hora de fazer alguns testes na proposta. Os testes são feitos localmente usando um fork da mainnet para simular uma proposta que está sendo executada on-chain.

a. **Adicionar testes de proposta**

Em test/migrations, adicione novamente um novo arquivo com o nome da proposta → proposal-name.ts e inclua o código a seguir:

*   Adicione as importações necessárias, incluindo as funções da proposta:

**createProposalNameProposal** → esta é a função que criamos em /src/migrations/proposal-name \


**MOCK\_PROPOSAL\_IPFS\_HASH** → usaremos um mock hash para fins de teste

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

*   Adicione as funções de teste com as etapas a seguir:

    * **fundProposalNameViaProposal** → crie esta função e a renomeie para corresponder ao nome da proposta.
    * **destinationAddress** → renomeie para corresponder ao nome de destino
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → isso será substituído pela variável do arquivo base-config
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → esta é a variável que criamos em _**config/index.ts**_
    * _**createProposalNameProposal** → importe esta função para ser usada_
    * **fundProposalNameViaNoProposal** → crie esta função e a renomeie para corresponder ao nome da proposta

\
    Execute o código abaixo para substituir todas essas variáveis com o nome o nome da proposta e variáveis já criadas acima:

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

b. **Adicione funções para fazer o teste de script**

Em test/migrations/deploy-contracts-for-test.ts, vamos adicionar as funções criadas acima para que elas sejam incluídas em nossos testes:

* Importar as funções criadas

```typescript
test/migrations/deploy-contracts-for-test.ts
...
import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Adicione testes para ambas as funções criando uma função de teste geral → executeProposalNameProposalForTest, **substitua o nome para corresponder à proposta**
* Também chamamos a variável config **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** criada anteriormente e a **PROPOSAL\_NAME\_ADDRESS** de deployConfig

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

c. **Adicione o contrato aos assistentes de testes**

Em test/helpers/get-deployed-contracts-for-test.ts, adicione a função criada acima para que os testes sejam executados nos testes do fork da mainnet:

* Importe a função executeProposalNameProposalForTest do arquivo de migrações:

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

* Adicione a função à função getDeployedContractsForTest(), fora do último else loop:

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

d. **Arquivo de teste final**

Por fim, adicionamos um teste da hash de IPFS e o saldo da carteira multisig após a proposta mock para garantir que tudo se dê conforme o esperado.

Em test/misc, adicione um novo arquivo com o nome da proposta rotulado → proposal-name-proposal.spec.ts e preencha-o com estes dois testes:

1. Importamos o Hash IPFS da biblioteca por meio de DIP\_NUMBER\_IPFS\_HASH
2. Colocamos direto no código o número de proposalId seguinte usando ProposalNameId
3. Conferimos a hash da proposta com a constante Hash
4.  Verificamos PROPOSAL\_NAME\_ADDRESS para conferir se há um saldo esperado em PROPOSAL\_FUNDING\_AMOUNT

**Observação: se este endereço já tiver DYDX, você precisará colocar o saldo direto no código para que o teste passe**

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

7\. **Envio do PR**

Quando todas essas alterações de código forem feitas e salvas localmente, podemos enviar o commit ao fork do repositório e abrir um PR para o repositório dYdX, que entrará para revisão:

a. **Faça o commit das alterações pela linha de comando**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **Envie um PR para repositório dYdX**

<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">

c. **Aguarde a análise e aprovação do gerenciador de repositórios**

