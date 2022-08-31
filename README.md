# Croak Wallet JS Docs
Guide for installation and usage of Croak's Web3 walllet.

## Installation

NPM
```
npm i croak-wallet-sdk
```
Yarn
```
yarn add croak-wallet-sdk
```
## Usage

### Initialization
First we need to ensure a div with id `croak-wallet` in the html body.
 
```<div id="croak-wallet"></div>```
``` 
import { croakWallet } from 'croak-wallet-sdk/wallet';
await croakWallet.init({
                chain:'polygon',
                authNetwork: 'testnet'}
            );
```

## Login/Logout

To login or logout a user, you can use croak's prebuilt UI or build your own and call SDK methods.
To use prebuilt UI

### showConnectModal

```croakWallet.showConnectModal(['google'])```

This will show a modal with a login with google button.
If you are building your own UI you can directly call the login methods
### login

```croakWallet.login('google')```


### isConnected

```
let isConnected = croakWallet.isConnected();
console.log(isConnected); // will be a boolean
```

## logout
```croakWallet.logout('google')```


## User Details
Methods to fetch user details

### getUserInfo
Get details about the logged in user.
```
let userInfo = croakWallet.getUserInfo();
console.log(userInfo.email);
console.log(userInfo.name);
console.log(userInfo.profileImage);
```

### getWalletId
Get the walletID of the logged in user, You can use this to transfer NFT to some other user.
```
let walletId = croakWallet.getWalledId()
```

## NFT Fetch/Transfer Methods

Methods to manage user's NFTs

### fetchNFTs
Get list of user's NFTs

```
let nfts = croakWallet.fetchNFTs()
```


### transferNFT
Transfer a NFT from the wallet of one user to another user.
```
croakWallet.transferNFT(walletIdTo,  nftId,  amount);
```
### createSellOrder

Start a sell order for token from the wallet. P2P sale.
```
croakWallet.createSellOrder(nftId,  amount,  currencyId,  currencyAmount);
```
### createBuyOrder
Make a buy order from the wallet

```
croakWallet.createBuyOrder(nftId, nftAmount, currencyId, currencyAmount);
```
