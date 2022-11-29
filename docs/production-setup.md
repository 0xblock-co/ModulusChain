# Production Setup for an RPC node:

This document will guide you through all the steps needed to setup your own `zkEVM-Node` for production.

# Warning:

>Currently the Executor/Prover does not run on ARM-powered Macs. For Windows users, WSL/WSL2 use is not recommended. 
> - Recommended specs: 
>    - Node: 16G RAM 4 cores
>    - Prover: 1TB RAM 128 cores
> - Unfortunately, M1 chips are not supported - for now since some optimizations on the prover require specific Intel instructions, this means some non-M1 computers won't work regardless of the OS, eg: AMD

## Network Components

Required:

- `Ethereum Node` - L1 Network
- `zkEVM-Node` - L2 Network
  - `JSON RPC Server` - Interface to L2 network
  - `Synchronizer` - Responsible to synchronize data between L1 and L2
  - `Sequencer` - Responsible to select transactions from the pool and propose new batches
  - `Aggregator`  - Responsible to consolidate the changes in the state proposed by the `Sequencers`
- `zk-Prover` - Zero knowledge proof generator

Optional:

- `Metamask` - Wallet to manage blockchain accounts
- `Block Scout Explorer` - Web UI to interact with the network information


## Requirements

The current version of the environment requires `go`, `docker` and `docker-compose` to be previously installed, check the links bellow to understand how to install them:

- <https://go.dev/doc/install> or just 
```bash
sudo snap install go --classic
```
- <https://www.docker.com/get-started> or just
```bash
sudo snap install docker
```
- <https://docs.docker.com/compose/install/>


## Clone Repo

Before we start:

> It's very important to say that the Prover is a software that requires a lot of technology power to be executed properly, with that said, we recommend you to have a dedicated machine with the following configuration to run the prover:

- 128 CPU cores
- 1TB RAM

```bash
git clone git@github.com:0xblock-co/ModulusChain.git
cd ModulusChain
```

## Configuration
### Config keystore
  Modify `./acc.keystore` file
  Config database user/password in `./docker-compose.yml`
  

```bash
make run-rpc
make run-explorer
make run-bridge
```
