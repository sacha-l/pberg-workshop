# Workshop - Protocol Berg 2023 👋

_Emerging interfaces for building web3 applications_

These are here for you to follow along and refer to code examples that demonstrate the concepts we'll be covering.

Because this workshop's focus is on cross-chain programs, all of these point to parts of the the examples in the [XCM docs examples repo](https://github.com/paritytech/xcm-docs/tree/main/examples). The runtimes are mock runtimes used to test cross-chain message instructions.

The XCM simulator mocks a [simple test net](https://github.com/paritytech/xcm-docs/tree/0e4a5fb58b9421288f4fc5e6def9c5d8b6b3f065/examples/src/simple_test_net) composed of:
- an asset hub parachain
- some other parachain
- a relay chain

**Note:** All of these runtimes are _very bare bones_ and don't contain any pallets related to consensus.

## Mock runtime examples

*Definitions*:

* Appchains = parachains, parathreads
* State transition function = appchain logic = chain “runtime”
* Appchain “modules” = runtime modules = pallets 

1. Have a look at what the mock runtime of the _assets parachain_ is composed of (see: [code snippet](https://github.com/paritytech/xcm-docs/blob/0e4a5fb58b9421288f4fc5e6def9c5d8b6b3f065/examples/src/simple_test_net/asset_hub.rs#L377-L390))


1. Notice that the mock relay chain also has `pallet_xcm` and `mock_msg_queue` (see [code snippet](https://github.com/paritytech/xcm-docs/blob/0e4a5fb58b9421288f4fc5e6def9c5d8b6b3f065/examples/src/simple_test_net/relay_chain.rs#L324-L337))


## Cross-chain programs on Polkadot using XCMP

*Definitions:*

- XCM - cross-consensus message format
- XCMP - cross-chain message passing protocol, XCM is related to XCMP in the same way that REST is related to RESTful.
- XCVM - virtual machine with fixed instruction set

Example of the pallets in the Polkadot Assset Hub parachain runtime, which provide a way for sending and receiving XCMs (see: [code snippet on slide 32](https://github.com/polkadot-fellows/runtimes/blob/main/system-parachains/asset-hubs/asset-hub-polkadot/src/lib.rs#L752-L756)).

### XCM instructions

1. The XCM simulator contains all of the instructions available to the XCVM (cross-consensus virtual machine). Have a look at the full list of instructions [here](https://paritytech.github.io/polkadot-sdk/master/xcm_simulator/enum.Instruction.html).

1. An example set of instructions to allow a user to send assets from the Relay chain, create collection of non-fungible assets and mint from that collection.

* [Teleport](https://github.com/paritytech/xcm-docs/blob/0e4a5fb58b9421288f4fc5e6def9c5d8b6b3f065/examples/src/1_transfers/teleport.rs#L19-L40): this message will send native Relay chain tokens to the assets chain.

* [Transact](https://github.com/paritytech/xcm-docs/blob/0e4a5fb58b9421288f4fc5e6def9c5d8b6b3f065/examples/src/3_transact/mod.rs#L80-L93): this message constructs a call that will create a collection on the Assets chain and mint from that collection in a single set of instructions.

# Resources

Resources to dig deeper into some of the concepts we talk about.

## Other Polkadot-compatible cross-chain protocols

- [SubBridge](https://docs.phala.network/other-products/subbridge): a bridging protocol that uses a MPC-based relayer to process cross-chain messages.
- [ISMP](https://github.com/polytope-labs/ismp-substrate/tree/main): a trustless messaging protocol that leverages Polkadot's shared security model to process messages.
- [Pallet IBC](https://github.com/ComposableFi/centauri/blob/master/contracts/pallet-ibc/README.md): a pallet for communicating over the IBC protocol from a Substrate runtime.

## Digging into XCM

* [XCM wiki](https://wiki.polkadot.network/docs/learn/xcm): learn hub for all things XCM 
* [XCM examples](https://github.com/paritytech/xcm-docs/tree/main/examples): examples that use the [XCM simulator](https://github.com/paritytech/polkadot-sdk/tree/master/polkadot/xcm/xcm-simulator) to execute cross-chain calls

## Learn by doing

* [XCM playground](https://github.com/AlexD10S/xcm-playground/tree/master): a stripped down version of the examples in the XCM docs.

* [Rococo](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frococo-rpc.polkadot.io#/explorer) is a live testnet with a whole bunch of parachains connected to it. Get yourself some test tokens from the [faucet](https://paritytech.github.io/polkadot-testnet-faucet/) and try it out.

* [Trappist](https://github.com/paritytech/trappist) is a web3 developer playground for experimenting with cross-chain applications and services built with the Polkadot SDK. You can use it to experiment cross-chain calls by launch a local test net using Zombie net.

- [Saturn Typescript SDK](https://saturn-docs.invarch.network/): Saturn is a powerful multisig protocol that leverageS no-code account abstraction to provide a seamless experience across different chains. It contains easy to use ways to construct XCM calls using TypeScript.

- [Kodadot](https://github.com/kodadot/nft-gallery): is a marketplace for Polkadot NFTs, working on user experiences for creating and minting NFT collections. If you're a front-end developer, their repositories are a good starting point to look at how to build your own user-facing apps using their libraries.
