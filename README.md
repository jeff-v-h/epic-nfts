# Basic Sample Hardhat Project

This project demonstrates a basic Hardhat use case. It comes with a sample contract, a test for that contract, a sample script that deploys that contract, and an example of a task implementation, which simply lists the available accounts.

Try running some of the following tasks:

```shell
npx hardhat accounts
npx hardhat compile
npx hardhat clean
npx hardhat test
npx hardhat node
node scripts/sample-script.js
npx hardhat help
```

## Requirements

- Alchemy API URL key
- Wallet on Ethereum Rinkeby Test Network such as Metamask
- Etherscan account

## Development

To run locally only, remove the "networks" property exported from hardhat.config.js.
To run on rinkeby testnet, add the following properties to the exported object from hardhat.config.js

```js
networks: {
    rinkeby: {
        url: process.env.STAGING_ALCHEMY_KEY,
        accounts: [process.env.PRIVATE_KEY]
    }
}
```

Add in your alchemy api url and rinkeby wallet (such as MetaMask) private account key to a .env file. Ther eis a .sample-env file to copy from.

Use the scripts/run.js file to test compilation of smart contract: `npx hardhat run scripts/run.js`.

## Compiling the smart contract

1. Once run.js works, copy it over to deploy.js.
2. Run the deploy.js script on the rinkeby network to deploy the smart contract on the testnet: `npx hardhat run scripts/deploy.js --network rinkeby`.
3. Take note of the contract address in the console for minting. It can also be searched for on an NFT marketplace such as OpenSea to see the NFT deployed.

## Minting an nft from the deployed smart contract

The code and the web app can be viewed on this [Replit repo](https://replit.com/@JeffreyHuang2/nft-starter-project#src/App.jsx).

1. Using the deployed contract address "Compiling the smart contract", paste it into the CONTRACT_ADDRESS in the App.jsx file's CONTRACT_ADDRESS constant. It lies within one of the nested functions.
2. New artifacts are created everytime a contract is deployed. Go to artifacts/contracts/MyEpicNFT.sol/MyEpicNFT.json and copy all the json within the file.
3. Paste and replace the json content in the webapp's src/utils/MyEpicNFT.json.
4. Run the app in a new browser tab and minting an NFT should succeed after a few moments. Check logs in devtools for progression.
5. In devtools, once successfully minted an etherscan url should be printed. Go to it and when it is successful (after indexing), copy the contract address (in the row with label "Interacted With (To):") and search for it on an NFT marketplace to see the minted NFT.

Remember, everytime a new smart contract is deployed, both the contract address and json content need to be updated in the web app to match.

## Check Smart contract on etherscan

`npx hardhat verify YOUR_CONTRACT_ADDRESS --network rinkeby`
