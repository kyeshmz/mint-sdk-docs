---
id: "modules"
title: "@kyuzan/mint-sdk-js"
sidebar_label: "Table of contents"
custom_edit_url: null
hide_title: true
---

# @kyuzan/mint-sdk-js

## Table of contents

### Classes

- [MintSDK](classes/mintsdk.md)
- [WrongNetworkError](classes/wrongnetworkerror.md)

### Interfaces

- [AccountInfo](interfaces/accountinfo.md)
- [ItemShippingInfo](interfaces/itemshippinginfo.md)
- [RegisterItemShippingInfoRequestBody](interfaces/registeritemshippinginforequestbody.md)

## Type aliases

### BigNumber

Ƭ **BigNumber**: ethers.BigNumber

Defined in: [src/types/BigNumber.ts:3](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/BigNumber.ts#L3)

___

### CurrencyUnit

Ƭ **CurrencyUnit**: *typeof* currencys[*number*]

Defined in: [src/types/CurrencyUnit.ts:3](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/CurrencyUnit.ts#L3)

___

### Item

Ƭ **Item**: *object*

Item is the master data.

[Token](modules.md#token) is the ERC721 Token equivalent of an Item, when bought or withdrawn.

#### Type declaration:

| Name | Type | Description |
| :------ | :------ | :------ |
| `authorAddress` | *string* | The wallet address of the Item creator.  |
| `buyerAddress` | *string* \| ``null`` | If the buyer address is not null, the value is either `sold` or `withdrawn`. |
| `chainType` | ``"ethereum"`` | - |
| `collectionId` | *string* | - |
| `createdBy` | *string*[] | Creator of the Item. The IPFS item data property `createdBy`. |
| `currentBidderAddress?` | *string* \| ``null`` | The wallet address of the latest bidder against the item. Only holds a value when tradeType === 'auction or autoExtensionAuction`. |
| `currentPrice?` | *number* | The current bidding price against the item in `ether`.  Only holds a value when tradeType === 'auction or autoExtensionAuction`. |
| `defaultEndAt?` | Date | The default ending date of the auction. Only holds a value when tradeType === 'auction or autoExtensionAuction`. |
| `description` | *string* | The item description. The IPFS item data property `description`. |
| `endAt?` | Date | The ending date of the auction. If autoExtensionAuction is true, it automatically updates. Only holds a value when tradeType === 'auction or autoExtensionAuction`. |
| `feeRatePermill` | *number* | - |
| `metadata.image` | *string* | ipfs://xxxx |
| `imageURIHTTP` | *object* | imageURI for browser preview https://xxxx |
| `imageURIHTTP.mimeType` | *string* | - |
| `imageURIHTTP.url` | *string* | - |
| `initialPrice?` | *number* | Auction starting price. Only holds a value when tradeType === 'auction` |
| `itemId` | *string* | - |
| `minBidPercentage?` | *number* | The minimum bid price ratio against the item. minBidPrice can be calculated by `currentPrice * minBidPercentage`. Only holds a value when tradeType === 'auction or autoExtensionAuction`. |
| `minBidPrice?` | *number* | The latest minimum bid against the item. Only holds a value when tradeType === 'auction or autoExtensionAuction`. |
| `mintContractAddress` | *string* | - |
| `mintShopContractAddress` | *string* | - |
| `name` | *string* | The name of the item. The IPFS item data property `name`. |
| `networkId` | [*NetworkId*](modules.md#networkid) | The network that the Item belongs to. 1 === Ethereum main network, 4 === Ethereum Rinkeby network,  137 ===  Polygon main network, 80001 === Matic Mumbai network |
| `physicalOrderStatus?` | ItemsPhysicalOrderStatus | Only holds a value when type === 'nftWithPhysicalProduct'. addressIsBlank: Awaiting further action from end user to complete address input, wip: Awaiting further shipping action from Mint moderators, shipped: Already Shipped |
| `previews` | { `mimeType`: *string* ; `url`: *string*  }[] | Preview image or video is inserted. When there is no value, it returns an empty array. |
| `price?` | *number* | Value of the Item in `ether`. Only holds a value when tradeType === 'fixedPrice` の時だけ値が入る |
| `startAt?` | Date | Auction starting date. Only holds a value when tradeType === 'auction or autoExtensionAuction'. |
| `tokenId` | *number* | tokenId against an `Item` that is ERC721 compliant. The tokenId of a Token after `Item ` is sold or withdrawn. |
| `tokenURI` | *string* | ipfs://xxxx |
| `tokenURIHTTP` | *string* | tokenURI for browser preview https://xxxx |
| `tradeType` | [*ItemTradeType*](modules.md#itemtradetype) | - |
| `type?` | [*ItemsType*](modules.md#itemstype) | nftWithPhysicalProduct === 物理アイテム付きアイテム If there is no type, it is an regular NFT Item, otherwise can be a NFT with a physical product attached. |
| `withdrawableAt?` | Date | The withdrawable date of the Item. `sendTxMakeSuccessfulBid` can be called after this date to withdraw the Token . Only holds a value when  tradeType === 'autoExtensionAuction`. |
| `yearCreated` | *string* | The created year of the Item. The IPFS item data property `yearCreated`. |

Defined in: [src/types/Item.ts:10](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/Item.ts#L10)

___

### ItemLog

Ƭ **ItemLog**: *object*

#### Type declaration:

| Name | Type |
| :------ | :------ |
| `accountAddress` | *string* |
| `createAt` | Date |
| `price` | *number* |
| `transactionHash` | *string* |
| `type` | ``"bought"`` \| ``"bid"`` |

Defined in: [src/types/ItemLog.ts:1](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/ItemLog.ts#L1)

___

### ItemTradeType

Ƭ **ItemTradeType**: *typeof* itemsTradeTypes[*number*]

Defined in: [src/types/ItemTradeType.ts:6](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/ItemTradeType.ts#L6)

___

### ItemsType

Ƭ **ItemsType**: *typeof* itemsTypes[*number*]

Defined in: [src/types/ItemsType.ts:5](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/ItemsType.ts#L5)

___

### NetworkId

Ƭ **NetworkId**: ``1`` \| ``4`` \| ``80001`` \| ``137``

Defined in: [src/types/NetworkId.ts:1](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/NetworkId.ts#L1)

___

### Residence

Ƭ **Residence**: *typeof* residenceList[*number*]

Defined in: [src/types/Residence.ts:2](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/Residence.ts#L2)

___

### Token

Ƭ **Token**: *object*

Token expresses ERC721 Standard Token.
Item:Token = 1:1

#### Type declaration:

| Name | Type | Description |
| :------ | :------ | :------ |
| `authorAddress` | *string* | https://ipfs.io/ipfs/xxxx |
| `contractAddress` | *string* | - |
| `description` | *string* | - |
| `imageURI` | *string* | ipfs:// |
| `imageURIHTTP` | *object* | imageURI for browser preview https://xxxx |
| `imageURIHTTP.mimeType` | *string* | - |
| `imageURIHTTP.url` | *string* | - |
| `item` | [*Item*](modules.md#item) | Item that originates the Token |
| `name` | *string* | - |
| `previews` | { `mimeType`: *string* ; `url`: *string*  }[] | Preview image or video is inserted. When there is no value, it returns an empty array. |
| `tokenId` | *number* | - |
| `tokenURI` | *string* | ipfs://xxxx |
| `tokenURIHTTP` | *string* | tokenURI for browser preview https://xxxx |

Defined in: [src/types/Token.ts:6](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/Token.ts#L6)

___

### WalletInfo

Ƭ **WalletInfo**: *object*

#### Type declaration:

| Name | Type |
| :------ | :------ |
| `address` | *string* |
| `balance` | [*BigNumber*](modules.md#bignumber) |
| `unit` | [*CurrencyUnit*](modules.md#currencyunit) |

Defined in: [src/types/WalletInfo.ts:4](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/WalletInfo.ts#L4)

___

### WalletSetting

Ƭ **WalletSetting**: *object*

#### Type declaration:

| Name | Type |
| :------ | :------ |
| `fortmatic` | *object* |
| `fortmatic.key` | *string* |

Defined in: [src/types/WalletSetting.ts:1](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/WalletSetting.ts#L1)
