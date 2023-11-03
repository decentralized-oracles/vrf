# VRF with Ink! Smart Contract (on Astar Network) and Ink! Phat Contract (on Phala Network)

Scenario described here in the communication betwen Ink! Smart Contract on Astar Network and Ink! Phat Contract on Phala Network:
1) A request to compute a random value between min and max values is stored in the Smart Contract `VrfConsumer` (on Astar Network)
2) The Phat Contract `VrfOracle` (on Phala Network) pulls the request from the Smart Contract `VrfConsumer` (on Astar Network), generates the random value and sends the number to the Smart Contract `VrfConsumer` (on Astar Network)
3) The Smart Contract `VrfConsumer` (on Astar Network) verifies the data used by the Phat Contract `VrfOracle` and saves the number to be displayed in the UI 

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
You have to configure the rpc, the pallet id, the call id and the contract id to call the Smart Contract `VrfConsumer`.

For example:
```
RPC=https://shibuya.public.blastapi.io
PALLET_ID=70
CALL_ID=6
#public key of the contract aesULxtrttD4VGe1oDWGnDihbknjQ44GYwN1L8RXMcWZxis
CONTRACT_ID=0xd0a5af9b2cd1fa7ca7b8c37cb1323b6596c7810b661085dbc32bdcd3a498219c
```
![config_target_contract](https://github.com/GuiGou12358/decentralized_oracle-vrf/assets/92046056/aee3b404-91b6-46a9-8882-1e38a94c65d3)


#### Enable Meta-Tx

Meta transaction allows the Phat Contract to submit rollup tx with attest key signature while using arbitrary account to pay the gas fee. 
To enable meta tx in the unit test you have to set the private key

For example, the private key of account //bob: 0x398f0c28f98885e046333d4a41c19cee4c37368a9832c6502f6cfd182e2aef89

If you don't use Meta-Tx, you have to be sure that address of Phat Contract `VrfOracle` will be able to pay transaction fees on Astar Network.

## Configure Ink! Smart Contract `VrfConsumer`

You have to grant the Phat Contract `VrfOracle` as attestor in the Smart Contract `VrfConsumer`.
![configure attestor](https://github.com/GuiGou12358/decentralized_oracle-vrf/assets/92046056/3f91f50b-0007-4a6d-9b37-badb04946620)

You have to register the hash of the source code used to generate the random number by the Phat Contract `VrfOracle`.
![get_core_js](https://github.com/GuiGou12358/decentralized_oracle-vrf/assets/92046056/6b9b3d8a-f5d3-4923-8f8f-d6b5ec7690fb)
![set_core_js](https://github.com/GuiGou12358/decentralized_oracle-vrf/assets/92046056/88634faf-e6c3-4b15-9cb2-3daaa965252b)

