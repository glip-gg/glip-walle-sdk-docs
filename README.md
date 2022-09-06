# Glip Wallet JS Docs
Guide for installation and usage of Glip's Web3 walllet.

## Installation

NPM
```
npm i glip-wallet-sdk
```
Yarn
```
yarn add glip-wallet-sdk
```
## Usage

### Initialization
First we need to ensure a div with id `glip-wallet` in the html body.
 
```<div id="croak-wallet"></div>```

```js
import { glipWalletSDK } from 'glip-wallet-sdk/wallet';
let initializedGlipWallet = false;

const getGlipWallet = async () => {
    if(initializedGlipWallet) {
        return initializedGlipWallet;
    }
    await glipWalletSDK.init({
        // add any supported chain here.
        chain:'polygon',
        // add testnet for testing and cyan for production
        authNetwork: 'cyan',
        // add your clientIdentifier here and replace testing one
        clientIdentifier: '62de50119081671256277620'
    });
    return glipWalletSDK;
};


export default getGlipWallet;

```

Now you can import glip wallet anywhere you need in your app and no need to re initialize it.
```js
  let glipWallet = await getGlipWallet()
```


## Login/Logout

To login or logout a user, you can use croak's prebuilt UI or build your own and call SDK methods.
To use prebuilt UI

### showConnectModal

```glipWalletSDK.showConnectModal(['google'])```

This will show a modal with a login with google button.
If you are building your own UI you can directly call the login methods
### login

```js
  glipWallet.login('google')
```


### isConnected

```
let isConnected = glipWallet.isConnected();
console.log(isConnected); // will be a boolean
```

## logout
```glipWallet.logout('google')```


## User Details
Methods to fetch user details

### getUserInfo
Get details about the logged in user.
```
let userInfo = glipWallet.getUserInfo();
console.log(userInfo.email);
console.log(userInfo.name);
console.log(userInfo.profileImage);
```

### getWalletId
Get the walletID of the logged in user, You can use this to transfer NFT to some other user.
```
let walletId = glipWallet.getWalledId()
```
<!---
## NFT Fetch/Transfer Methods

Methods to manage user's NFTs

### fetchNFTs
Get list of user's NFTs

```
let nfts = glipWallet.fetchNFTs()
```


### transferNFT
Transfer a NFT from the wallet of one user to another user.
```
glipWallet.transferNFT(walletIdTo,  nftId,  amount);
```
### createSellOrder

Start a sell order for token from the wallet. P2P sale.
```
glipWallet.createSellOrder(nftId,  amount,  currencyId,  currencyAmount);
```
### createBuyOrder
Make a buy order from the wallet

```
glipWallet.createBuyOrder(nftId, nftAmount, currencyId, currencyAmount);
```
-->
