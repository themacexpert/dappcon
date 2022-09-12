# Building Cross Chain DApps with Moonbeam @DappCon 2022
![Banner Image](https://i.ibb.co/DbBXnYJ/Workshop-20220912-Dapp-Con-Kevin-Neilson-External.png)

This guide contains all the links you'll need for the workshop. We won't assume any pre-existing account setup, so we will start from a blank slate. 

## Send a message to another chain with Axelar
In this demo, we will use Axelar's General message passing to call a contract on another chain. We will be mostly following the steps of [this blog post guide](https://moonbeam.network/blog/connected-contracts-axelar/), with the exception of the gas amounts, which have changed since the publish date. 

To get started, copy and paste the contents of [SimpleGeneralMessage.sol](https://gist.github.com/jboetticher/0188244031df80e9b180568e30bfa7a5) into Remix.

The required gas amounts in WEI to send along with the message from Moonbase Alpha are the following: 
- Polygon Mumbai: 339003286300000000
- Avalanche Fuji: 970363238301000000
- Fantom Testnet: 553898649000000000
- Ethereum Ropst: 16000000000000000000

### Initial Setup
1. [Install MetaMask](https://metamask.io/)
2. [Add Moonbase Alpha Network to MetaMask](https://docs.moonbeam.network/)
3. Import ALICE Account into your MetaMask. This is a Shared Public Test Account that's already funded with plenty of testnet funds. Private Key: 0x28194e8ddb4a2f2b110ee69eaba1ee1f35e88da2222b5a7d6e3afa14cf7a3347
 

## Remote Execution with XCM

### Initial Setup

1. [Install MetaMask](https://metamask.io/)
2. [Add Moonbase Alpha Network to MetaMask](https://docs.moonbeam.network/)
3. [Get funds from the faucet](https://apps.moonbeam.network/moonbase-alpha/faucet/)
4. [Swap some (not all) DEV tokens for xcUNITS](https://moonbeam-swap.netlify.app/#/swap)

### Calculating a Sovereign Address
- [Clone the xcmTools repo](https://github.com/albertov19/xcmTools)
- [Shawn Tabrizi's Utilities](https://www.shawntabrizi.com/substrate-js-utilities/)

### Account Setup
- [Create a New Account on the Moonbase Relay Chain](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ffrag-moonbase-relay-rpc-ws.g.moonbase.moonbeam.network#/accounts)
- [Import the ALICE Account on the Moonbase Alpha Parachain](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fwss.api.moonbase.moonbeam.network#/accounts) Private Key: 0x28194e8ddb4a2f2b110ee69eaba1ee1f35e88da2222b5a7d6e3afa14cf7a3347
- Also, import the ALICE account to your MetaMask

### Calculating the Derivative Account
- [Clone the PolkaTools repo](https://github.com/albertov19/PolkaTools)
- [Check account balance of derivative account](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ffrag-moonbase-relay-rpc-ws.g.moonbase.moonbeam.network#/chainstate)

### Transfer 
- [Fill out the transfer information on the relay chain to get the call bytes but don't submit here](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ffrag-moonbase-relay-rpc-ws.g.moonbase.moonbeam.network#/extrinsics)
- [Initiate the remote transfer transaction on the Moonbase Alpha Parachain](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fwss.api.moonbase.moonbeam.network#/extrinsics)
- Parameters you'll need include:
- Index: 42
- Foreign Asset ID: 42259045809535163221576417993425387648
- Weight: 1000000000

### Using XCMTransactor.sol
- [Access the precompile here:](https://github.com/PureStake/moonbeam/blob/c39a717e2501a3470ae589c52daaa51786189cce/precompiles/xcm-transactor/XcmTransactor.sol)
- [Copy and paste it into remix](http://remix.ethereum.org/)
- [Calculate the external XC-20 address](https://www.rapidtables.com/convert/number/decimal-to-hex.html)
- [Verify the address on Moonbase Alpha Moonscan](https://moonbase.moonscan.io/)
