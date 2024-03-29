# Step-by-step instructions on Ethereum blockchain deployment for Ubuntu 18.04

:exclamation: Some alternative frontend implementation steps are also located below.



## Prerequisites ##
Environment: Ubuntu 18.04

Check Ubuntu version by typing
`lsb_release -a`

Check Node.js and Truffle versions  by typing  
`node -v` and  `truffle version`

Check Geth version by typing.
`geth version`
Geth is the command line interface for running a full ethereum node implelented in Go.

## Installation and other operations ##
To install Geth, run
`sudo apt-get install software-properties-common`,
`sudo add-apt-repository -y ppa:ethereum/ethereum`,
`sudo apt-get update`,
`sudo apt-get install ethereum`.

After installing, run
`geth account new` to create an account on your node
`geth --help` to check all other options

 Get test Ether here : https://faucet.rinkeby.io/
 Once the transaction is confirmed, you will be able to see it on 
 `https://kovan.etherscan.io/address/<your address here>`
 
## Steps ##

#BACKEND#

1. Set up Truffle developing framework 
  -run `npm install -g truffle`
  
2. Start a new project
  -`mkdir aave`
   `cd aave`
   `truffle init`
   
3. Truffle sets up 3 directories:
   -contracts  
   -migrations (to deploy smart contracts)
   -test (mocha style tests)
   and
   -truffle.config (to configure environments, which RPC node to use)
 
 4. Write smart contract
    Check it on https://remix.ethereum.org/#optimize=false&evmVersion=null&version=soljson-v0.5.11+commit.c082d0b4.js for errors.
   
 5. Set up local blockchain. Install Ganache on your machine.https://www.trufflesuite.com/ganache
 
 6. Deploy to a local blockchain
   -`truffle migrate --network development`
    If no error was found, proceed with deploying it on Kovan testnet.
    
 
 7. Start geth.Create new Kovan account
   `geth`
   `-geth --kovan account new` (for mainnet `geth account new`)
   
 8. List your accounts
    `geth --kovan account list`

 9. At this point, we need some test ETH.
    See ## Installation and other operations ##.
    
10. Deploy contracts on Kovan.Point Geth at the kovan network.Wait for it to sync.
    `./build/bin/geth --rinkeby --rpc --rpcapi db,eth,net,web3,personal --unlock="<your address here>"`
    
11. Once it is synced, run the migration
    `truffle migrate --network kovan`
    You should be able to see the contract in the terminal, and, also, on the Kovan testnet https://kovan.etherscan.io/.
    
    
#FRONTEND#


1. Include the web3.js script in <head>
 
2. Instantiate the web3 instance with a local geth

3. Instantiate the contract with an abi file (this is the interface file that comes when you compile your contracts. 
   You can find this by looking at the compiled json in /build/contracts/aave.json

4. Find the specific deployed contract with the interface in #3

5. Call functions the contract interface accordingly   
 
   
   





