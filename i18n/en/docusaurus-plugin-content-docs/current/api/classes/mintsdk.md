---
id: "mintsdk"
title: "Class: MintSDK"
sidebar_label: "MintSDK"
custom_edit_url: null
hide_title: true
---

# Class: MintSDK

## Constructors

### constructor

\+ **new MintSDK**(`accessToken`: _string_, `networkIds`: [_NetworkId_](../modules.md#networkid)[], `walletSetting`: [_WalletSetting_](../modules.md#walletsetting), `devOption?`: { `backendUrl?`: _string_ ; `jsonRPCUrl?`: _string_ }): [_MintSDK_](mintsdk.md)

#### Parameters:

| Name                    | Type                                           |
| :---------------------- | :--------------------------------------------- |
| `accessToken`           | _string_                                       |
| `networkIds`            | [_NetworkId_](../modules.md#networkid)[]       |
| `walletSetting`         | [_WalletSetting_](../modules.md#walletsetting) |
| `devOption?`            | _object_                                       |
| `devOption.backendUrl?` | _string_                                       |
| `devOption.jsonRPCUrl?` | _string_                                       |

**Returns:** [_MintSDK_](mintsdk.md)

Defined in: [src/index.ts:97](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L97)

## Properties

### getWalletInfo

• **getWalletInfo**: () => _Promise_<[_WalletInfo_](../modules.md#walletinfo)\>

Can get the transactional history and other account information.

**Required**

- Requires the wallet to be connected.

**`returns`**

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
await sdk.connectWallet()  // required
await sdk.getWalletInfo()
```

#### Type declaration:

▸ (): _Promise_<[_WalletInfo_](../modules.md#walletinfo)\>

**Returns:** _Promise_<[_WalletInfo_](../modules.md#walletinfo)\>

Defined in: [src/index.ts:206](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L206)

Defined in: [src/index.ts:206](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L206)

---

### walletStrategy

• `Private` **walletStrategy**: WalletStrategy

Defined in: [src/index.ts:97](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L97)

## Methods

### addEthereumChain

▸ **addEthereumChain**(`networkId`: `80001` \| `137`): _Promise_<void\>

Adds a specified network to the wallet.
137 => Polygon production network
80001 => Polygon development / test network

**Required**
sdk.isInjectedWallet() => must be true (Requires the use of Metamask)

#### Parameters:

| Name        | Type             |
| :---------- | :--------------- |
| `networkId` | `80001` \| `137` |

**Returns:** _Promise_<void\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
await sdk.addEthereumChain(137)
```

Defined in: [src/index.ts:1125](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L1125)

---

### connectWallet

▸ **connectWallet**(): _Promise_<void\>

Connects to a wallet.
If Metamask is installed in the default browser, it will utilize Metamask, otherwise will use Fortmatic.
If a wallet is connected, it will return Resolve, otherwise will return Reject.

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
await sdk.isWalletConnect() // false
await sdk.connectWallet()
await sdk.isWalletConnect()  // true
```

**Returns:** _Promise_<void\>

Defined in: [src/index.ts:171](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L171)

---

### disconnectWallet

▸ **disconnectWallet**(): _Promise_<void\>

Disconnects the wallet.
When utilizing Fortmatic, it disconnects from the service.
When utilizing Metamask, **nothing will happen**.

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
await sdk.disconnectWallet()
```

**Returns:** _Promise_<void\>

Defined in: [src/index.ts:187](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L187)

---

### getAccountInfo

▸ **getAccountInfo**(`arg`: { `walletAddress`: _string_ }): _Promise_<[_AccountInfo_](../interfaces/accountinfo.md)\>

Returns the account information pertaining to the wallet such as display name or profile picture.
If there is nothing set, will return a blank string.

#### Parameters:

| Name                | Type     |
| :------------------ | :------- |
| `arg`               | _object_ |
| `arg.walletAddress` | _string_ |

**Returns:** _Promise_<[_AccountInfo_](../interfaces/accountinfo.md)\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
const accountInfo = await sdk.getAccountInfo({ walletAddress: '0xxxxxxxx' })
```

Defined in: [src/index.ts:941](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L941)

---

### getConnectedNetworkId

▸ **getConnectedNetworkId**(): _Promise_<number\>

Returns the connected network id.

**Returns:** _Promise_<number\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
await sdk.getConnectedNetworkId()
```

Defined in: [src/index.ts:790](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L790)

---

### getItemById

▸ **getItemById**(`itemId`: _string_): _Promise_<[_Item_](../modules.md#item)\>

Returns the Item from the specified itemId.

#### Parameters:

| Name     | Type     | Description                             |
| :------- | :------- | :-------------------------------------- |
| `itemId` | _string_ | itemId of an [Item](../modules.md#item) |

**Returns:** _Promise_<[_Item_](../modules.md#item)\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemById('item.itemId')
```

Defined in: [src/index.ts:355](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L355)

---

### getItemByToken

▸ **getItemByToken**(`token`: [_Token_](../modules.md#token)): _Promise_<[_Item_](../modules.md#item)\>

Returns the originating Item associated with the Token

#### Parameters:

| Name    | Type                           |
| :------ | :----------------------------- |
| `token` | [_Token_](../modules.md#token) |

**Returns:** _Promise_<[_Item_](../modules.md#item)\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemByToken(token)
```

Defined in: [src/index.ts:372](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L372)

---

### getItemLogs

▸ **getItemLogs**(`itemId`: _string_, `paging?`: { `page`: _number_ = 1; `perPage`: _number_ = 30 }): _Promise_<{ `accountAddress`: _string_ ; `createAt`: Date ; `price`: _number_ ; `transactionHash?`: _string_ ; `type`: ItemLogTypeEnum }[]\>

Returns the item transactional history.
It will return starting from the most recent.

#### Parameters:

| Name             | Type     | Default value | Description                         |
| :--------------- | :------- | :------------ | :---------------------------------- |
| `itemId`         | _string_ | -             | [Item](../modules.md#item)の itemId |
| `paging`         | _object_ | -             | -                                   |
| `paging.page`    | _number_ | 1             | -                                   |
| `paging.perPage` | _number_ | 30            | -                                   |

**Returns:** _Promise_<{ `accountAddress`: _string_ ; `createAt`: Date ; `price`: _number_ ; `transactionHash?`: _string_ ; `type`: ItemLogTypeEnum }[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemLogs('Item.itemId')
```

Defined in: [src/index.ts:399](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L399)

---

### getItemShippingInfo

▸ **getItemShippingInfo**(`arg`: { `itemId`: _string_ }): _Promise_<InlineResponse2006\>

Returns the shipping info linked to the NFT item with a corresponding physical item.

{@link Items}From a security perspective, a Sign from the user is necessary

**Required**

- Requires a wallet to be connected.
- The users [Item](../modules.md#item) `type` must be `nftWithPhysicalProduct`
- [Item](../modules.md#item) must be either withdrawn or bought. Must also have a corresponding [Token](../modules.md#token)
- The user's [Item](../modules.md#item) `physicalOrderStatus` must be either `wip` or `ship`.
- The user must be the owner of the [Token](../modules.md#token).

#### Parameters:

| Name         | Type     | Description                                      |
| :----------- | :------- | :----------------------------------------------- |
| `arg`        | _object_ | itemId = itemId of an [Item](../modules.md#item) |
| `arg.itemId` | _string_ | -                                                |

**Returns:** _Promise_<InlineResponse2006\>

Defined in: [src/index.ts:889](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L889)

---

### getItems

▸ **getItems**(`__namedParameters?`: { `itemType?`: `"nft"` \| `"nftWithPhysicalProduct"` ; `networkId?`: [_NetworkId_](../modules.md#networkid)[] ; `onSale?`: _boolean_ ; `page`: _number_ ; `perPage`: _number_ ; `sort?`: { `order`: `"asc"` \| `"desc"` ; `sortBy`: `"endAt"` \| `"startAt"` \| `"price"` } ; `tradeType?`: `"fixedPrice"` \| `"auction"` \| `"autoExtensionAuction"` }): _Promise_<[_Item_](../modules.md#item)[]\>

Returns the Items with the flag `Items.openStatus === 'open'`,
The status of the items can be changed from the admin panel

#### Restrictions

Please take caution of the following restrictions

- If specified as `tradeType === 'fixedPrice'`, it cannot be sorted by `'endAt' | 'startAt'`.
- If specified as `tradeType === 'auction'`, it cannot be sorted by `price`.
- If specified as`onSale`, it cannot be sorted by `startAt`.

#### Parameters:

| Name                            | Type                                                      | Description                                                                                                                                                                              |
| :------------------------------ | :-------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `__namedParameters`             | _object_                                                  | -                                                                                                                                                                                        |
| `__namedParameters.itemType?`   | `"nft"` \| `"nftWithPhysicalProduct"`                     | -                                                                                                                                                                                        |
| `__namedParameters.networkId?`  | [_NetworkId_](../modules.md#networkid)[]                  | If there is no specification, the constructor value will be used.                                                                                                                        |
| `__namedParameters.onSale?`     | _boolean_                                                 |                                                                                                                                                                                          |
| `__namedParameters.page`        | _number_                                                  | Amount of pages.                                                                                                                                                                         |
| `__namedParameters.perPage`     | _number_                                                  | Amount of items per page. Default to 30.                                                                                                                                                 |
| `__namedParameters.sort?`       | _object_                                                  | `'endAt','startAt'` is valid when Item is on sale as an auction. It can be sorted from the starting or ending auction time. `price` is valid only when Item is on sale as a fixed price. |
| `__namedParameters.sort.order`  | `"asc"` \| `"desc"`                                       | -                                                                                                                                                                                        |
| `__namedParameters.sort.sortBy` | `"endAt"` \| `"startAt"` \| `"price"`                     | -                                                                                                                                                                                        |
| `__namedParameters.tradeType?`  | `"fixedPrice"` \| `"auction"` \| `"autoExtensionAuction"` | -                                                                                                                                                                                        |

**Returns:** _Promise_<[_Item_](../modules.md#item)[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)

const items = await sdk.getItems({
    page: 1,
    perPage: 100,
    // below args are optional
    // filter
    tags: 'a,b,c',
    // sort
    sort: {
      sortBy: 'price',
      sortDirection: 'desc',
    },
  })
```

Defined in: [src/index.ts:261](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L261)

---

### getBiddedItemStocks

```typescript
const tokens = getSdk().getBiddedItemStocksByWalletAddress({
  walletAddress,
  page: 1,
  perPage: 100,
});
```

---

### getBoughtOrWithdrawItemStocks

```typescript
const itemStocks = await getSdk().getBoughtItemStocksByWalletAddress({
  walletAddress: bidderAddress,
  page: 1,
  perPage: 1000,
});
```

---

### getItemsByBidderAddress

▸ **getItemsByBidderAddress**(`address`: _string_): _Promise_<[_Item_](../modules.md#item)[]\>

Returns the bidding history of a specified address.

#### Parameters:

| Name      | Type     | Description    |
| :-------- | :------- | :------------- |
| `address` | _string_ | wallet address |

**Returns:** _Promise_<[_Item_](../modules.md#item)[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemsByBidderAddress('0x1111......')
```

Defined in: [src/index.ts:332](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L332)

---

### getServerUnixTime

▸ **getServerUnixTime**(): _Promise_<number\>

Returns the server date in unix time.

**Returns:** _Promise_<number\>

unix time (ms)

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
await sdk.getServerUnixTime()  // ex) 1615444120104
```

Defined in: [src/index.ts:733](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L733)

---

### getTokensByAddress

▸ **getTokensByAddress**(`address`: _string_): _Promise_<[_Token_](../modules.md#token)[]\>

Returns a list of tokens acquired using MINT from the specified address.

#### Parameters:

| Name      | Type     | Description         |
| :-------- | :------- | :------------------ |
| `address` | _string_ | Address of a wallet |

**Returns:** _Promise_<[_Token_](../modules.md#token)[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...
const tokens = await sdk.getTokensByAddress({
  walletAddress,
  page: 1,
  perPage: 100,
})
```

Defined in: [src/index.ts:431](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L431)

---

### isCorrectNetwork

▸ **isCorrectNetwork**(): _Promise_<boolean\>

Returns if a network is appropriate.

**Returns:** _Promise_<boolean\>

Returns true, if appropriate.

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.isCorrectNetwork() // true
```

Defined in: [src/index.ts:766](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L766)

---

### isInjectedWallet

▸ **isInjectedWallet**(): _boolean_

Validates if utilizing MetaMask.

**Returns:** _boolean_

Returns true if utilizing MetaMask.

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.isInjectedWallet() // true
```

Defined in: [src/index.ts:750](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L750)

---

### isWalletConnect

▸ **isWalletConnect**(): _Promise_<boolean\>

Returns if an account is valid.

**Returns:** _Promise_<boolean\>

If a wallet is connected, returns true

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
await sdk.isWalletConnect()
```

Defined in: [src/index.ts:153](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L153)

---

### onAccountsChange

▸ **onAccountsChange**(`callback`: (`accounts`: _string_[]) => _any_): _void_

Set a callback when the account has been changed.

#### Parameters:

| Name       | Type                              |
| :--------- | :-------------------------------- |
| `callback` | (`accounts`: _string_[]) => _any_ |

**Returns:** _void_

void

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
sdk.onAccountsChange((accounts: string[]) => {
   // some thing
})
```

Defined in: [src/index.ts:659](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L659)

---

### onConnect

▸ **onConnect**(`callback`: () => _any_): _void_

Set a callback when the wallet is connected.

#### Parameters:

| Name       | Type        |
| :--------- | :---------- |
| `callback` | () => _any_ |

**Returns:** _void_

void

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
sdk.onConnect(() => {
   // some thing
})
```

Defined in: [src/index.ts:684](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L684)

---

### onDisconnect

▸ **onDisconnect**(`callback`: () => _any_): _void_

Set a callback when the wallet is disconnected.

#### Parameters:

| Name       | Type        |
| :--------- | :---------- |
| `callback` | () => _any_ |

**Returns:** _void_

void

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
sdk.onDisconnect(() => {
   // some thing
})
```

Defined in: [src/index.ts:709](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L709)

---

### registerItemShippingInfo

▸ **registerItemShippingInfo**(`arg`: { `itemId`: _string_ ; `shippingInfo`: _Omit_<[_RegisterItemShippingInfoRequestBody_](../interfaces/registeritemshippinginforequestbody.md), `"tokenId"` \| `"signedData"` \| `"chainType"` \| `"networkId"` \| `"contractAddress"`\> }): _Promise_<void\>

Registers the shipping info for an Item associated with a physical item.
Please prepare a form for the user to input their shipping info.

**Required**

- Requires a wallet to be connected.
- The user [Item](../modules.md#item) `type` must be `nftWithPhysicalProduct`.
- [Item](../modules.md#item) must be withdrawn or bought. Must be associated with（[Token](../modules.md#token))
- The user [Item](../modules.md#item) `physicalOrderStatus` must be `shippingInfoIsBlank`.
- The user must be the owner of the [Token](../modules.md#token).

#### Parameters:

| Name               | Type                                                                                                                                                                                           | Description                                                                                         |
| :----------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------- |
| `arg`              | _object_                                                                                                                                                                                       | itemId = the itemId of an [Item](../modules.md#item), shippingInfo = the shipping info of the Item. |
| `arg.itemId`       | _string_                                                                                                                                                                                       | -                                                                                                   |
| `arg.shippingInfo` | _Omit_<[_RegisterItemShippingInfoRequestBody_](../interfaces/registeritemshippinginforequestbody.md), `"tokenId"` \| `"signedData"` \| `"chainType"` \| `"networkId"` \| `"contractAddress"`\> | -                                                                                                   |

**Returns:** _Promise_<void\>

Defined in: [src/index.ts:809](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L809)

---

### sendTxBid

▸ **sendTxBid**(`itemId`: _string_, `bidPrice`: _number_): _Promise_<TransactionResponse\>

Creates a transaction from the specified bid price.
The total amount of the bid is passed through the `bidPrice` argument.

**Required**

- Requires a wallet to be connected.

#### Parameters:

| Name       | Type     | Description                         |
| :--------- | :------- | :---------------------------------- |
| `itemId`   | _string_ | [Item](../modules.md#item)の itemId |
| `bidPrice` | _number_ | unit is in ether                    |

**Returns:** _Promise_<TransactionResponse\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
await sdk.connectWallet() // required
try {
 const tx = await sdk.sendTxBid('item.itemId', 2)
 // show loading
 await tx.wait()
 // success transaction
} catch (err) {
 // display error message
}
```

Defined in: [src/index.ts:466](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L466)

---

### sendTxBuyItem

▸ **sendTxBuyItem**(`itemId`: _string_, `userResidence?`: `"unknown"` \| `"jp"`): _Promise_<TransactionResponse\>

Creates a transaction for buying an Item at a fixed price.
Requires a UI that asks for the users residence for accommodating for consumption tax purposes.

**Required**

- Requires a wallet to be connected.

#### Parameters:

| Name            | Type                  | Default value | Description                                                         |
| :-------------- | :-------------------- | :------------ | :------------------------------------------------------------------ |
| `itemId`        | _string_              | -             | The itemid of an [Item](../modules.md#item)                         |
| `userResidence` | `"unknown"` \| `"jp"` | 'unknown'     | [Residence](../modules.md#residence) Specifies the buyers residence |

**Returns:** _Promise_<TransactionResponse\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
await sdk.connectWallet() // required
try {
 const tx = await sdk.sendTxBuyItem('item.itemId', 'jp')
 // show loading
 await tx.wait()
 // success transaction
} catch (err) {
 // display error message
}
```

Defined in: [src/index.ts:595](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L595)

---

### sendTxMakeSuccessfulBid

▸ **sendTxMakeSuccessfulBid**(`itemId`: _string_, `userResidence?`: `"unknown"` \| `"jp"`): _Promise_<TransactionResponse\>

オークションで勝利したアイテムを引き出すトランザクションを発行
ユーザーの居住地を問う UI を合わせて実装必要です。居住地を設定することで消費税に関する会計処理などがスムーズに行えます

**Required**

- Requires a wallet to be connected.
- **If automatic extension for the auction is enabled, withdrawing is only avaliable after `withdrawableAt`.**

#### Parameters:

| Name            | Type                  | Default value | Description                                                         |
| :-------------- | :-------------------- | :------------ | :------------------------------------------------------------------ |
| `itemId`        | _string_              | -             | The itemId of [Item](../modules.md#item)                            |
| `userResidence` | `"unknown"` \| `"jp"` | 'unknown'     | [Residence](../modules.md#residence) Specifies the buyers residence |

**Returns:** _Promise_<TransactionResponse\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
await sdk.connectWallet() // required
try {
 const tx = await sdk.sendTxMakeSuccessfulBid('item.itemId', 'jp')
 // show loading
 await tx.wait()
 // success transaction
} catch (err) {
 // display error message
}
```

Defined in: [src/index.ts:530](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L530)

---

### updateAccountInfo

▸ **updateAccountInfo**(`arg`: { `avatarImageId`: _string_ ; `bio`: _string_ ; `displayName`: _string_ ; `homepageUrl`: _string_ ; `instagramAccountName`: _string_ ; `twitterAccountName`: _string_ }): _Promise_<void\>

Can update the wallet address image and display name.
All items are optional, but should not be set as blank string.
The return value of `avatarImageId` is `sdk.uploadImg`.

**Required**

- Requires a wallet to be connected.

#### Parameters:

| Name                       | Type     |
| :------------------------- | :------- |
| `arg`                      | _object_ |
| `arg.avatarImageId`        | _string_ |
| `arg.bio`                  | _string_ |
| `arg.displayName`          | _string_ |
| `arg.homepageUrl`          | _string_ |
| `arg.instagramAccountName` | _string_ |
| `arg.twitterAccountName`   | _string_ |

**Returns:** _Promise_<void\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
const imgId = await sdk.uploadAvatarImg()
await sdk.updateAccountInfo({ imgId, .... })
```

Defined in: [src/index.ts:970](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L970)

---

### uploadAccountInfoAvatar

▸ **uploadAccountInfoAvatar**(`arg`: { `file`: File }): _Promise_<{ `imgId`: _string_ ; `uploadedImgUrl`: _string_ }\>

Returns the `imgId` from the `sdk.updateAccountInfo`.
uploadedImgUrl is a read-only URL for the uploaded image.

**Required**

- Requires a wallet to be connected.

#### Parameters:

| Name       | Type     |
| :--------- | :------- |
| `arg`      | _object_ |
| `arg.file` | File     |

**Returns:** _Promise_<{ `imgId`: _string_ ; `uploadedImgUrl`: _string_ }\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
const { imgId, uploadedImgUrl } = await sdk.uploadAccountInfoAvatar({ file })
```

Defined in: [src/index.ts:1045](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L1045)

---

### waitForTransaction

▸ **waitForTransaction**(`txHash`: _string_): _Promise_<void\>

When the transaction is successful, it returns a Resolve.

**Required**

- Requires a wallet to be connected.

#### Parameters:

| Name     | Type     | Description                                                                                                                                                                                                                                                                                                                                             |
| :------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `txHash` | _string_ | The hash property of {@link ethers.providers.TransactionResponse} `typescript import { MintSDK } from '@kyuzan/mint-sdk-js' const sdk = await MintSDK.initialize(...) await sdk.connectWallet() // required try { const tx = await sdk.sendTxBuyItem('item.itemId') await tx.wait() // success transaction } catch (err) { // display error message } ` |

**Returns:** _Promise_<void\>

Defined in: [src/index.ts:231](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L231)

---

### formatEther

▸ `Static`**formatEther**(`bg`: _BigNumber_): _string_

Returns an BigNumber that is formatted as an ether.

#### Parameters:

| Name | Type        |
| :--- | :---------- |
| `bg` | _BigNumber_ |

**Returns:** _string_

Returns an ether parsed as a string.

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
await sdk.connectWallet()  // required
const walletInfo = await sdk.getWalletInfo()
MintSDK.formatEther(walletInfo.balance) // 3.2
```

Defined in: [src/index.ts:83](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L83)

---

### parseEther

▸ `Static`**parseEther**(`ether`: _string_): _BigNumber_

Returns the ether price as a BigNumber.

#### Parameters:

| Name    | Type     | Description            |
| :------ | :------- | :--------------------- |
| `ether` | _string_ | Shown as an ether unit |

**Returns:** _BigNumber_

Returns an ether that is parsed as a BigNumber.

```typescript
import { MintSDK } from "@kyuzan/mint-sdk-js";

MintSDK.parseEther("3.2"); // BigNumber
```

Defined in: [src/index.ts:64](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L64)
