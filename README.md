# (WIP) Ethdev toolbox docker

A set of Docker images to ease the install and use of ethereum protocol. 

*Launching all services at the same time is an heavy process due to the multitude of services. If you decide to run them all at once, please note that it can take a while before everything gets ready*

## Local Ethereum Network
A set of Docker images to create a local Ethereum network with three nodes and a monitor. This was built to understand how local Ethereum networks have to be set up and to provide a local test environment. **Never use this in a productive environment, as the docker-compose.yml contains hardcoded passwords and private keys for convenience** 

### Usage
Setting up this networks requires you to install Docker. Clone the repository, and run `docker-compose up` from the repository root. The network should start and synchronize without any further configuration. It is using the Clique protocol (Proof-of-Authority), so the network runs very efficiently and does not use a lot of energy.

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

### usage

Start the service. You should be able to connect to `localhost:8585`. Port has been changed to avoid conflict with miners.

## Remix IDE 

A web interface  for developping, debugging and compilation test smart-contracts

## TODO : Truffle

### TODO : build contracts through docker

### TODO : unit tests of contracts through docker

## Clixplorer

A block explorer for PoA Eth network. 

Provided by [Magicking](https://github.com/Magicking/Clixplorer)

### TODO: Usage

