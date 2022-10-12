---
description: >-
  In order to ease market maker onboarding, the dYdX team created this guide.
  Please read through the document in its entirety before beginning any
  integration steps.
---

# Market Maker Onboarding

## dYdX Suggested Market Maker Onboarding Flow:

1. Connect your preferred ethereum wallet to dYdX L2 Perpetual protocol.
2. Deposit USDC into your Perpetual account.
3. You will need to generate a STARK Key which identifies your account on Layer 2 and is saved locally on your browser. The Stark Key associates dYdX users with Ethereum account addresses so a user must first request to sign the linkage of an Ethereum key to a STARK Key and then register the STARK Key on dYdX’s smart contract before any other operation can take place. Click “Generate Stark Key” and sign the transaction. Signing is free and will not send a transaction. You can recover your Stark Key at any time with your wallet.

Alternatively, programmatic traders may derive their STARK key pair using the following method:

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

More about STARK Keys can be found here.

4\. Next you will need an API key which will require your Ethereum signature, or via a web3 provider. Note, Eth signatures are needed only for onboarding and managing API keys but not for trading—STARK key signatures are required for trading. API Keys can be registered and obtained using the following functions:

_Registering:_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_Obtaining:_

```
api_keys = client.private.get_api_keys()
```

_Alternatively (3. And 4.)_, If you don't want the private key to be online, you can generate the STARK key securely with the following steps to get the required credentials.

a. From the dYdX Perpetuals exchange, right-click anywhere in your web-browser, and select Inspect to open Developer Tools

b. Go to Application > Local Storage > https://trade.dydx.exchange

c. Select STARK\_KEY\_PAIRS and click the drop-down next to your wallet address to get the stark private key

d. Select API\_KEY\_PAIRS and click the drop-down next to your wallet address to get the API key, secret key, and passphrase
