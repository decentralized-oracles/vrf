# VRF with Ink! Smart Contracts and Phat contracts

The Phat Contract `VrfOracle` pulls the requests from the Ink! Smart Contract `VrfConsumer`, generates the random values sends them into Ink! Smart Contract

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

