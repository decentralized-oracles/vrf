# VRF with Ink! Smart Contract (on Astar Network) and Ink! Phat Contract (on Phala Network)

Here :
1) a request to compute a random value between min and max values will be stored in the Smart Contract `VrfConsumer` (on Astar Network)
2) The Phat Contract `VrfOracle` (on Phala Network) pulls the requests from the Smart Contract `VrfConsumer` (on Astar Network), generates the random value and send it to the Smart Contract `VrfConsumer` (on Astar Network)
3) The Smart Contract `VrfConsumer` (on Astar Network) verifies the data used by the Phat Contract `VrfOracle` to generate the random number and saves the number to be displayed in the UI 

You can find a demo here: https://vrf-decentralized-oracle.substrate.fi/

The Phat Contract and Ink! Smart Contract have been built with the Phat Offchain Rollup.
The full documentation of this SDK can be found here: https://github.com/Phala-Network/phat-offchain-rollup


## Phat Contract `VrfOracle`

To deploy this Phat Contract you can build the contract or use existing artifacts

More information here: [phat/contracts/vrf_oracle/README.md](phat/contracts/vrf_oracle/README.md)

### Build the contract

To build the contract:
```bash
cd phat/contracts/vrf_oracle
cargo contract build
```

### Use existing artifacts
All artifacts are here: [phat/artifacts](phat/artifacts)


## Ink! Smart Contract `VrfConsumer`

To deploy this Ink! Smart Contract you can build the contract or use existing artifacts

More information here: [ink/contracts/vrf_consumer/README.md](ink/contracts/vrf_consumer/README.md)

### Build the contract

To build the contract:
```bash
cd ink/contracts/vrf_consumer
cargo contract build
```

### Use existing artifacts
All artifacts are here: [ink/artifacts](ink/artifacts)



## Configure Phat Contract `VrfOracle`
You have to configure the rpc, the pallet id, teh call id and the contract id to call the Smart Contract `VrfConsumer`.

For example:
RPC=https://shibuya.public.blastapi.io
PALLET_ID=70
CALL_ID=6
# public key of the contract aesULxtrttD4VGe1oDWGnDihbknjQ44GYwN1L8RXMcWZxis
CONTRACT_ID=0xd0a5af9b2cd1fa7ca7b8c37cb1323b6596c7810b661085dbc32bdcd3a498219c



#### Enable Meta-Tx

Meta transaction allows the Phat Contract to submit rollup tx with attest key signature while using arbitrary account to pay the gas fee. 
To enable meta tx in the unit test you have to set the private key

For example, the private key of account //bob: 0x398f0c28f98885e046333d4a41c19cee4c37368a9832c6502f6cfd182e2aef89

If you don't use Meta-Tx, you have to be sure that address of Phat Contract `VrfOracle` will be able to pay transaction fees on Astar Network.

## Configure Ink! Smart Contract `VrfConsumer`

You have to grant the Phat Contract `VrfOracle` as attestor in the Smart Contract `VrfConsumer`.

You have to register the hash of the source code used to generate the random number by the Phat Contract `VrfOracle`.
