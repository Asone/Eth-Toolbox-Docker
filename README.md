# (WIP) Ethdev toolbox docker

**DISCLAMER : This is a Work In Progress project and all services might not be functional yet.

A set of Docker images to ease the install, config and use of ethereum protocol. 

It provides the following containers : 
- [`Geth + Eth-netstats`] : Local PoA Ethereum chain and monitoring ✅
- [`ganache-cli`]() : Local Dev network with Ganache-cli ✅
- [`remix-ide`]() : Smart-contract IDE for development & debug ❌
- [`MyEtherwallet`]() : Ethereum Wallet manager ❓
- [`Clixplorer`]() : Block explorer for PoA network ❌
- [`PoA Explorer`]() : Block explorer for PoA network ❌ 
- [`Truffle`]() : Smart-contracts compiler and unit tester ❌
- [`IPFS`]() : local IPFS node ❌


Please, note that **it is NOT recommended to start all services at once** as some tools are redundant and many libraries quite heavy to install and run. It is **instead** recommended to **pick what services to launch and customize the configuration provided in `docker-compose.yml`** instead.

## Local Ethereum Network

A set of Docker images to create a local Ethereum network with three nodes and a monitor. This was built to understand how local Ethereum networks have to be set up and to provide a local test environment. **Never use this in a productive environment, as the docker-compose.yml contains hardcoded passwords and private keys for convenience** 

### Usage

run `docker-compose up geth-bootnode geth-dev-miner-1 geth-dev-miner-2 geth-dev-miner-3 geth-monitor-backend geth-monitor-frontend` from the repository root.

 It will run the required services for running a PoA network with monitoring.

 The network should start and synchronize without any further configuration. It is using the Clique protocol (Proof-of-Authority), so the network runs very efficiently and does not use a lot of energy.

The started  services are described below in the next paragraphs.

### The bootnode
The nodes in the network are connecting with the bootnode. This is a special ethereum node, designed to provide a register of the existing nodes in the network. The parameter `nodekeyhex`in the `docker-compose.yml` is needed to derive the `enodeID` which is later passed to the other nodes. The IP needs to be fixed, as the other nodes need to know where to find the bootnode, and DNS is not supported. The bootnode does not participate in synchronization of state or mining.

### Miners / Geth Nodes
There are three nodes that participate in the network. The state is synchronized between them and they are trying to create blocks with mining. Initially they connect to the bootnode with the information derived from the fixed IP and the nodekeyhex. If you want to interact with the network, you need to connect via RPC. You can attach a geth instance, connect Remix IDE or connect your browser with web3 and build a ÐApp.

The RPC Ports of the nodes are mapped to your localhost, the addresses are:

* [http://localhost:8545](http://localhost:8545) - geth-miner-1
* [http://localhost:8546](http://localhost:8546) - geth-miner-2
* [http://localhost:8547](http://localhost:8547) - geth-miner-3

### Monitoring

The monitoring is being provided by two nodes, the monitoring-backend and the monitoring-frontend. The backend connects to the ethereum nodes and retrieves metrics from them. It communicates with the monitoring-frontend with websockets. The frontend can be found under [http://localhost:3000](http://localhost:3000)

provided by : [javahippie](https://github.com/javahippie/geth-dev) 

## Ganache-cli RPC Client

A fast RPC client for development and testing. 

### Usage

run `docker-compose up ganache`. You should be able to connect through[localhost:8585]()`. 

Port has been changed to avoid conflict with miners.

### Configuration

You can configure [ganache-cli parameters]() of ganache-cli in the  `docker-compose.yml` file. 

## Truffle

Truffle is a smart-contract development framework which provides unit testings, ABI generation and deployment strategy for smart-contracts.

### Usage

run `docker-compose exec truffle truffle compile`.

On build service will create a default truffle project in `./smart-contracts/` if it is empty. 

truffle files should be stored in this directory. 


## Remix IDE 

A web interface for developping, debugging and compilation test smart-contracts

### [TODO] Usage

### [TODO] Configuration 

## [TODO] Truffle

### [TODO] Build 

### [TODO] Test

## Clixplorer

A block explorer for PoA Eth network. 

### Usage 

run `docker-compose up clixplorer` and connect to [localhost:xxxx](http://localhost:xxxx). 

### [TODO] Configuration 

Provided by [Magicking](https://github.com/Magicking/Clixplorer)

