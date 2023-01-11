---
description: >-
  Una guía técnica paso a paso de cómo crear una propuesta para transferir DYDX del tesoro de la comunidad a una dirección de destino.
---

# Guía técnica para construir una Propuesta de gasto de tesorería de la comunidad dYdX

Reverie elaboró una guía técnica exhaustiva para enviar una propuesta de gobernanza para transferir DYDX del tesoro de la comunidad por medio de una solicitud de retiro (SR) al repositorio de _contratos de gobernanza_ de dYdX.

Para crear esta propuesta, un miembro de la comunidad de dYdX debe tener **al menos 5 millones de DYDX** _(el 0.5 % de la reserva total)_ de poder de propuesta ([umbral de la propuesta](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters) para un [voto de bloqueo de tiempo corto](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)).

### Requisitos preliminares

Se deben cumplir los siguientes pasos antes de presentar la solicitud de retiro (SR):

1. **Ciclo de vida de la propuesta:** Se deben contabilizar los fondos en DRC siguiendo la [plantilla](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) de propuestas y debe llevarse a cabo un voto en Snapshot.
2. **Dirección de destino:** La dirección de destino debe generarse con antelación. Si la dirección de destino es multifirmas, se debe crear la billetera multifirmas.
3. **Cuenta de GitHub:** Una cuenta de GitHub para bifurcar el repositorio.
4. **Cantidad de la transferencia (opcional):** Es preferible que se establezca la cantidad solicitada de la transferencia antes de la SR. Sin embargo, si se usa una cantidad hipotética, se puede establecer como paso final antes de la aprobación.
5. **Hash IPFS de DIP (opcional):** Si se conoce la cantidad de la transferencia, se debe finalizar el DIP y enviarse a IPFS para generar su hash. Sin embargo, esto se puede establecer como paso final antes de la aprobación si la cantidad aún no se determina.

### Elaboración de la propuesta

1. **Bifurque el** [**repositorio de contratos de gobernanza de dYdX**](https://github.com/dydxfoundation/DIP) **en su cuenta de GitHub.**

<img src=".gitbook/assets/Untitled (2).png" alt="" data-size="original">

\
2\. **Clone el repositorio** y cambie el \[username] al suyo.

```shell
git clone https://github.com/[username]/governance-contracts.git
```

\
3\. **Variables de configuración**

En src/config/index.ts, agregue dos variables nuevas a la constante configSchema que se usará para fines de hacer pruebas. En los siguientes bloques de código, cambie los campos **'PROPOSAL\_NAME'** y **'PROPOSAL'** al nombre de la propuesta que se va a presentar.

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

En src/deploy-config/base-config.ts, agregue la dirección de destino y la cantidad de la transferencia como variables nuevas en la constante config:

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

**Nota**: La cantidad de financiamiento se tendrá que **multiplicar por 10^18** conforme a la norma ERC20. Si la cantidad aún no se conoce, se puede usar una temporal (p. ej. 10 → 10000000000000000000).

En src/lib/constants.ts, agregue la variable del hash de IPFS que hará referencia al DIP aprobado en el otro repositorio:

```typescript
src/lib/constants.ts
...
// Add a link to where the hash can be found
export const DIP_NUMBER_IPFS_HASH = '0x0000000000000000000000000000000000000000000000000000000000000000';
```

**Nota**: Si el DIP aún no se ha publicado, se puede utilizar un valor temporal para hacer pruebas (p. ej., ‘0x0000000000000000000000000000000000000000000000000000000000000000’)\


4\. **Código de la propuesta**

En _**src/migrations,**_ cree un nuevo archivo con el nombre de la propuesta → proposal-name.ts y llénelo con el siguiente código:

a. Agregue las importaciones necesarias en la parte superior:

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

b. Cree una nueva función usando el nombre de la propuesta debajo de las importaciones y agregue el siguiente código con dos variables únicas:

* **destinationAddress** → esta será la dirección que reciba el financiamiento
* **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → esta es la variable que creamos antes y que determinará la cantidad que va a transferirse

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
5\. **Tarea de despliegue**

Con la propuesta creada, podemos escribir el despliegue que generará transacción y los datos de llamada necesarios para presentar la propuesta.

En _**tasks/deployment,**_ cree un nuevo archivo con el mismo nombre que se usó para el código de la propuesta → proposal-name.ts y llénelo con el siguiente código:

a. Agregue las importaciones necesarias con las siguientes variables:

_**DIP\_NUMBER\_IPFS\_HASH**_ → esta es la variable que agregamos en lib/constants

_**createProposalNameProposal**_ → esta es la función que creamos en /src/migrations/proposal-name

```typescript
tasks/deployment/proposal-name.ts

import { types } from 'hardhat/config';

import mainnetAddresses from '../../src/deployed-addresses/mainnet.json';
import { hardhatTask } from '../../src/hre';
import { DIP_NUMBER_IPFS_HASH } from '../../src/lib/constants';
import { createProposalNameProposal } from '../../src/migrations/proposal-name';
```

b. Cree la tarea hardhat y llénela con la información de la propuesta en la línea de apertura de la tarea. \
\
Escriba el nombre de la propuesta en deploy:proposal-name: y agregue una breve descripción en “Proposal Description”.

La última línea llama a la función que importó del código de la propuesta, así que tendrá que ajustarse.

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
6\. **Elaboración de las pruebas**

Ahora que el código está listo para desplegarse, es hora de elaborar algunas pruebas en función de la propuesta. Las pruebas se hacen tanto de manera local como con una bifurcación de la mainnet para simular la ejecución de una propuesta en cadena.

a. **Agregue pruebas de propuesta**

En test/migrations, agregue una vez más un archivo nuevo con el nombre de la propuesta → proposal-name.ts e incluya el siguiente código:

* Agregue las importaciones necesarias, incluidas las funciones de la propuesta:

**createProposalNameProposal** → esta es la función que creamos en /src/migrations/proposal-name \


**MOCK\_PROPOSAL\_IPFS\_HASH** → vamos a usar un hash hipotético para fines de las pruebas

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

* Agregue las funciones de prueba con los siguientes pasos:

    * **fundProposalNameViaProposal** → cree esta función y cámbiele el nombre para que coincida con el de la propuesta.
    * **destinationAddress** → vuelva a etiquetar esto para que coincida con el nombre del destino.
    * **deployConfig.PROPOSAL\_FUNDING\_AMOUNT** → la variable del archivo base-config reemplazará esta función.
    * **FUND\_PROPOSAL\_NAME\_PROPOSAL\_ID** → esta es la variable que creamos en _**config/index.ts**_.
    * _**createProposalNameProposal** → esta función se importó antes para usarse_
    * **fundProposalNameViaNoProposal** → cree esta función y cámbiele el nombre para que coincida con el de la propuesta.

\
    Repase el código siguiente para reemplazar todas estas variables con el nombre de la propuesta y las variables existentes que ya creó antes:

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

b. **Agregue las funciones de prueba a la secuencia de comandos de prueba**

En test/migrations/deploy-contracts-for-test.ts, agregaremos las funciones que creó antes para que se incluyan en nuestras pruebas:

* Importe las funciones creadas

```typescript
test/migrations/deploy-contracts-for-test.ts

...

import { fundProposalNameNoProposal, fundProposalNameViaProposal } from './proposal-name-proposal';
```

* Agregue pruebas para ambas funciones creando una función general para pruebas → execute executeProposalNameProposalForTest; **cambie el nombre para que coincida con el de la propuesta**.
* También llamamos a la variable config **TEST\_PROPOSAL\_NAME\_TRUST\_WITH\_PROPOSAL** previamente creada y la variable **PROPOSAL\_NAME\_ADDRESS** de deployConfig.

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

c. **Agregue el contrato a los ayudantes de la prueba**

En test/helpers/get-deployed-contracts-for-test.ts, agregue la función creada antes para que las pruebas se lleven a cabo en las pruebas de la bifurcación de la mainnet:

* Importe la función executeProposalNameProposalForTest del archivo de migraciones:

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

* Agregue la función a la función getDeployedContractsForTest(), fuera del último bucle “else”:

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

d. **Archivo final de prueba**

Por último, agregamos una prueba tanto del hash IPFS y el saldo de la billetera multifirmas luego de la propuesta hipotética para asegurarse de que todo resulte como se espera.

En test/misc, agregue un nuevo archivo con el nombre de la propuesta etiquetado → proposal-name-proposal.spec.ts y llénelo con estas dos pruebas:

1. Importamos el hash IPFS de lib por medio de DIP\_NUMBER\_IPFS\_HASH
2. preprogramamos el siguiente número de proposalId usando ProposalNameId
3. revisamos el hash de la propuesta con la constante Hash
4. revisamos PROPOSAL\_NAME\_ADDRESS para comprobar que tenga el saldo esperado de PROPOSAL\_FUNDING\_AMOUNT

**Nota: Si esta dirección ya tiene DYDX, tendrá que preprogramarlo en el saldo para pasar la prueba.**

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

7\. **Presentación de la SR**

Una vez que todos estos cambios en el código se lleven a cabo y se guarden localmente, podemos confirmarlos en el repositorio bifurcado y abrir una SR al repositorio de dYdX para su revisión:

a. **Confirme los cambios por medio de la línea de comandos**

```shell
git add .
git commit -m 'funding proposal upload'
git push
```

b. **Presente una SR en el repositorio de dYdX**

****<img src=".gitbook/assets/Screenshot 2022-12-14 at 5.06.23 PM.png" alt="" data-size="original">****

c. **Espere la revisión y la aprobación del administrador del repositorio**

