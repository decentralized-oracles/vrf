# VrfOracle

This Ink! Phat Contract `VrfOracle` (on Phala Network):
1) Listens the requests sent by the Ink! Smart Contract (on Astar Network)
2) Generates a random value between min and max values
3) Send the value to the Ink! Smart Contract (on Astar Network)


## Build

To build the contract:

```bash
cargo contract build
```

## Run Integration tests

Unfortunately, the cross contract call doesn't work in a local environment. 
It means the JS contract used to compute the random value can not been reached and the tests can not be run for the time being.  
