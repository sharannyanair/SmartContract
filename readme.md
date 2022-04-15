# SmartContract :

A step by step guide to create and deploy a smart contract (ERC20) using node.js application for token distribution

## Prerequisite:

Create an infura account (infura.io/)  and create an ethereum project.Once project iscreated it will provide an project ID, which will be used in code (.env file)as INFURA_TOKEN
Create a metamask account .The metamask address is used as OWNER_ADDRESS in .env
The private key in metamask is used as a SUPER_SECRET_PRIVATE_KEY in .env
Node.js should be installed on the machine

### Install dependencies*

Install Docker (https://docs.docker.com/get-docker/ ).The application uses Docker as a container for the application .With the help of Docker we build, share and run application.
Install web3 , ethereumJS, big-number and .env (npm install *)


## Steps to deploy Smart Contract
* Clone the GitHub repo using below command.
*  Open project in Remix IDE. In DeployedControl.sol file,update name and  symbol of the token to be distributed.
       
         constructor() {
        _name = "Project x21154520";
        _symbol = "SHYN";
        
        _mint(msg.sender, 1000000000000000000000000);}

*  Compile and deploy the DeployedControl.sol file.The contract address is used as CONTRACT_ADDRESS  in .env
*  Dockerfile,.dockerignore and docker-compose.yml are docker dependency file used in the source code
*  To build and run application on docker environment, use <br />
    `docker build . -t x21154520/project_blockchain_smartcontract` <br />
    The docker build command builds an image from a Dockerfile.In the command ,we specify a repository and tag at which to save the new image if the build succeeds

    The repository can be viewed at
    [Docker Hub](https://hub.docker.com/layers/203078292/x21154520/project_blockchain_smartcontract/latest/images/sha256-6426b28e461a9c288c5af7ca6fa074f02393b2255c6e4ceaab19174277d7edcd?context=repo)

*  Type below command to run application

    `docker run -p 8090:8080 x21154520/project_blockchain_smartcontract:latest`

*  There can only be one CMD instruction in a Dockerfile. The main purpose of a CMD is to provide defaults for an executing   container.For this project , we specify the distribute.js file as a entrypoint instruction.

    `CMD ["node", “distribute.js"]`

*  You an go to [etherscan.io](https://ropsten.etherscan.io/) to search and view the transactions made from the metamask owner address.

