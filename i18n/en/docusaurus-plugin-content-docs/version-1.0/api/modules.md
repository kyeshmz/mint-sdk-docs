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

---

### CurrencyUnit

Ƭ **CurrencyUnit**: _typeof_ currencys[*number*]

Defined in: [src/types/CurrencyUnit.ts:3](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/CurrencyUnit.ts#L3)

---

### Item

Ƭ **Item**: _object_

Item is the master data.

[Token](modules.md#token) is the ERC721 Token equivalent of an Item, when bought or withdrawn.

#### Type declaration:

| Name                      | Type                                         | Description                                                                                                                                                                                                                      |
| :------------------------ | :------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `authorAddress`           | _string_                                     | The wallet address of the Item creator.                                                                                                                                                                                          |
| `buyerAddress`            | _string_ \| `null`                           | If the buyer address is not null, the value is either `sold` or `withdrawn`.                                                                                                                                                     |
| `chainType`               | `"ethereum"`                                 | -                                                                                                                                                                                                                                |
| `collectionId`            | _string_                                     | -                                                                                                                                                                                                                                |
| `createdBy`               | _string_[]                                   | Creator of the Item. The IPFS item data property `createdBy`.                                                                                                                                                                    |
| `currentBidderAddress?`   | _string_ \| `null`                           | The wallet address of the latest bidder against the item. Only holds a value when tradeType === 'auction or autoExtensionAuction`.                                                                                               |
| `currentPrice?`           | _number_                                     | The current bidding price against the item in `ether`. Only holds a value when tradeType === 'auction or autoExtensionAuction`.                                                                                                  |
| `defaultEndAt?`           | Date                                         | The default ending date of the auction. Only holds a value when tradeType === 'auction or autoExtensionAuction`.                                                                                                                 |
| `description`             | _string_                                     | The item description. The IPFS item data property `description`.                                                                                                                                                                 |
| `endAt?`                  | Date                                         | The ending date of the auction. If autoExtensionAuction is true, it automatically updates. Only holds a value when tradeType === 'auction or autoExtensionAuction`.                                                              |
| `feeRatePermill`          | _number_                                     | -                                                                                                                                                                                                                                |
| `imageURI`                | _string_                                     | ipfs://xxxx                                                                                                                                                                                                                      |
| `imageURIHTTP`            | _object_                                     | imageURI for browser preview https://xxxx                                                                                                                                                                                        |
| `imageURIHTTP.mimeType`   | _string_                                     | -                                                                                                                                                                                                                                |
| `imageURIHTTP.url`        | _string_                                     | -                                                                                                                                                                                                                                |
| `initialPrice?`           | _number_                                     | Auction starting price. Only holds a value when tradeType === 'auction`                                                                                                                                                          |
| `itemId`                  | _string_                                     | -                                                                                                                                                                                                                                |
| `minBidPercentage?`       | _number_                                     | The minimum bid price ratio against the item. minBidPrice can be calculated by `currentPrice * minBidPercentage`. Only holds a value when tradeType === 'auction or autoExtensionAuction`.                                       |
| `minBidPrice?`            | _number_                                     | The latest minimum bid against the item. Only holds a value when tradeType === 'auction or autoExtensionAuction`.                                                                                                                |
| `mintContractAddress`     | _string_                                     | -                                                                                                                                                                                                                                |
| `mintShopContractAddress` | _string_                                     | -                                                                                                                                                                                                                                |
| `name`                    | _string_                                     | The name of the item. The IPFS item data property `name`.                                                                                                                                                                        |
| `networkId`               | [_NetworkId_](modules.md#networkid)          | The network that the Item belongs to. 1 === Ethereum main network, 4 === Ethereum Rinkeby network, 137 === Polygon main network, 80001 === Matic Mumbai network                                                                  |
| `physicalOrderStatus?`    | ItemsPhysicalOrderStatus                     | Only holds a value when type === 'nftWithPhysicalProduct'. addressIsBlank: Awaiting further action from end user to complete address input, wip: Awaiting further shipping action from Mint moderators, shipped: Already Shipped |
| `previews`                | { `mimeType`: _string_ ; `url`: _string_ }[] | Preview image or video is inserted. When there is no value, it returns an empty array.                                                                                                                                           |
| `price?`                  | _number_                                     | Value of the Item in `ether`. Only holds a value when tradeType === 'fixedPrice` の時だけ値が入る                                                                                                                                |
| `startAt?`                | Date                                         | Auction starting date. Only holds a value when tradeType === 'auction or autoExtensionAuction'.                                                                                                                                  |
| `tokenId`                 | _number_                                     | tokenId against an `Item` that is ERC721 compliant. The tokenId of a Token after `Item ` is sold or withdrawn.                                                                                                                   |
| `tokenURI`                | _string_                                     | ipfs://xxxx                                                                                                                                                                                                                      |
| `tokenURIHTTP`            | _string_                                     | tokenURI for browser preview https://xxxx                                                                                                                                                                                        |
| `tradeType`               | [_ItemTradeType_](modules.md#itemtradetype)  | -                                                                                                                                                                                                                                |
| `type?`                   | [_ItemsType_](modules.md#itemstype)          | nftWithPhysicalProduct === 物理アイテム付きアイテム If there is no type, it is an regular NFT Item, otherwise can be a NFT with a physical product attached.                                                                     |
| `withdrawableAt?`         | Date                                         | The withdrawable date of the Item. `sendTxMakeSuccessfulBid` can be called after this date to withdraw the Token . Only holds a value when tradeType === 'autoExtensionAuction`.                                                 |
| `yearCreated`             | _string_                                     | The created year of the Item. The IPFS item data property `yearCreated`.                                                                                                                                                         |

Defined in: [src/types/Item.ts:10](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/Item.ts#L10)

---

### ItemLog

Ƭ **ItemLog**: _object_

#### Type declaration:

| Name              | Type                  |
| :---------------- | :-------------------- |
| `accountAddress`  | _string_              |
| `createAt`        | Date                  |
| `price`           | _number_              |
| `transactionHash` | _string_              |
| `type`            | `"bought"` \| `"bid"` |

Defined in: [src/types/ItemLog.ts:1](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/ItemLog.ts#L1)

---

### ItemTradeType

Ƭ **ItemTradeType**: _typeof_ itemsTradeTypes[*number*]

Defined in: [src/types/ItemTradeType.ts:6](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/ItemTradeType.ts#L6)

---

### ItemsType

Ƭ **ItemsType**: _typeof_ itemsTypes[*number*]

Defined in: [src/types/ItemsType.ts:5](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/ItemsType.ts#L5)

---

### NetworkId

Ƭ **NetworkId**: `1` \| `4` \| `80001` \| `137`

Defined in: [src/types/NetworkId.ts:1](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/NetworkId.ts#L1)

---

### Residence

Ƭ **Residence**: _typeof_ residenceList[*number*]

Defined in: [src/types/Residence.ts:2](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/Residence.ts#L2)

---

### Token

Ƭ **Token**: _object_

Token expresses ERC721 Standard Token.
Item:Token = 1:1

#### Type declaration:

| Name                    | Type                                         | Description                                                                            |
| :---------------------- | :------------------------------------------- | :------------------------------------------------------------------------------------- |
| `authorAddress`         | _string_                                     | https://ipfs.io/ipfs/xxxx                                                              |
| `contractAddress`       | _string_                                     | -                                                                                      |
| `description`           | _string_                                     | -                                                                                      |
| `imageURI`              | _string_                                     | ipfs://                                                                                |
| `imageURIHTTP`          | _object_                                     | imageURI for browser preview https://xxxx                                              |
| `imageURIHTTP.mimeType` | _string_                                     | -                                                                                      |
| `imageURIHTTP.url`      | _string_                                     | -                                                                                      |
| `item`                  | [_Item_](modules.md#item)                    | Item that originates the Token                                                         |
| `name`                  | _string_                                     | -                                                                                      |
| `previews`              | { `mimeType`: _string_ ; `url`: _string_ }[] | Preview image or video is inserted. When there is no value, it returns an empty array. |
| `tokenId`               | _number_                                     | -                                                                                      |
| `tokenURI`              | _string_                                     | ipfs://xxxx                                                                            |
| `tokenURIHTTP`          | _string_                                     | tokenURI for browser preview https://xxxx                                              |

Defined in: [src/types/Token.ts:6](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/Token.ts#L6)

---

### WalletInfo

Ƭ **WalletInfo**: _object_

#### Type declaration:

| Name      | Type                                      |
| :-------- | :---------------------------------------- |
| `address` | _string_                                  |
| `balance` | [_BigNumber_](modules.md#bignumber)       |
| `unit`    | [_CurrencyUnit_](modules.md#currencyunit) |

Defined in: [src/types/WalletInfo.ts:4](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/WalletInfo.ts#L4)

---

### WalletSetting

Ƭ **WalletSetting**: _object_

#### Type declaration:

| Name            | Type     |
| :-------------- | :------- |
| `fortmatic`     | _object_ |
| `fortmatic.key` | _string_ |

Defined in: [src/types/WalletSetting.ts:1](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/types/WalletSetting.ts#L1)
