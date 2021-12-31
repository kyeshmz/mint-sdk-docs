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

\+ **new MintSDK**(`accessToken`: *string*, `networkIds`: [*NetworkId*](../modules.md#networkid)[], `walletSetting`: [*WalletSetting*](../modules.md#walletsetting), `devOption?`: { `backendUrl?`: *string* ; `jsonRPCUrl?`: *string*  }): [*MintSDK*](mintsdk.md)

#### Parameters:

| Name | Type |
| :------ | :------ |
| `accessToken` | *string* |
| `networkIds` | [*NetworkId*](../modules.md#networkid)[] |
| `walletSetting` | [*WalletSetting*](../modules.md#walletsetting) |
| `devOption?` | *object* |
| `devOption.backendUrl?` | *string* |
| `devOption.jsonRPCUrl?` | *string* |

**Returns:** [*MintSDK*](mintsdk.md)

Defined in: [src/index.ts:97](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L97)

## Properties

### getWalletInfo

• **getWalletInfo**: () => *Promise*<[*WalletInfo*](../modules.md#walletinfo)\>

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

▸ (): *Promise*<[*WalletInfo*](../modules.md#walletinfo)\>

**Returns:** *Promise*<[*WalletInfo*](../modules.md#walletinfo)\>

Defined in: [src/index.ts:206](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L206)

Defined in: [src/index.ts:206](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L206)

___

### walletStrategy

• `Private` **walletStrategy**: WalletStrategy

Defined in: [src/index.ts:97](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L97)

## Methods

### addEthereumChain

▸ **addEthereumChain**(`networkId`: ``80001`` \| ``137``): *Promise*<void\>

Adds a specified network to the wallet.
137 => Polygon production network
80001 => Polygon development / test network

**Required**
sdk.isInjectedWallet() => must be true (Requires the use of Metamask)

#### Parameters:

| Name | Type |
| :------ | :------ |
| `networkId` | ``80001`` \| ``137`` |

**Returns:** *Promise*<void\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
await sdk.addEthereumChain(137)
```

Defined in: [src/index.ts:1125](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L1125)

___

### connectWallet

▸ **connectWallet**(): *Promise*<void\>

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

**Returns:** *Promise*<void\>

Defined in: [src/index.ts:171](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L171)

___

### disconnectWallet

▸ **disconnectWallet**(): *Promise*<void\>

Disconnects the wallet.
When utilizing Fortmatic, it disconnects from the service.
When utilizing Metamask, **nothing will happen**.


```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
await sdk.disconnectWallet()
```

**Returns:** *Promise*<void\>

Defined in: [src/index.ts:187](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L187)

___

### getAccountInfo

▸ **getAccountInfo**(`arg`: { `walletAddress`: *string*  }): *Promise*<[*AccountInfo*](../interfaces/accountinfo.md)\>

Returns the account information pertaining to the wallet such as display name or profile picture.
If there is nothing set, will return a blank string.


#### Parameters:

| Name | Type |
| :------ | :------ |
| `arg` | *object* |
| `arg.walletAddress` | *string* |

**Returns:** *Promise*<[*AccountInfo*](../interfaces/accountinfo.md)\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
const accountInfo = await sdk.getAccountInfo({ walletAddress: '0xxxxxxxx' })
```

Defined in: [src/index.ts:941](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L941)

___

### getConnectedNetworkId

▸ **getConnectedNetworkId**(): *Promise*<number\>

Returns the connected network id.

**Returns:** *Promise*<number\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
await sdk.getConnectedNetworkId()
```

Defined in: [src/index.ts:790](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L790)

___

### getItemById

▸ **getItemById**(`itemId`: *string*): *Promise*<[*Item*](../modules.md#item)\>

Returns the Item from the specified itemId.

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `itemId` | *string* | itemId of an [Item](../modules.md#item) |

**Returns:** *Promise*<[*Item*](../modules.md#item)\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemById('item.itemId')
```

Defined in: [src/index.ts:355](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L355)

___

### getItemByToken

▸ **getItemByToken**(`token`: [*Token*](../modules.md#token)): *Promise*<[*Item*](../modules.md#item)\>

Returns the originating Item associated with the Token

#### Parameters:

| Name | Type |
| :------ | :------ |
| `token` | [*Token*](../modules.md#token) |

**Returns:** *Promise*<[*Item*](../modules.md#item)\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemByToken(token)
```

Defined in: [src/index.ts:372](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L372)

___

### getItemLogs

▸ **getItemLogs**(`itemId`: *string*, `paging?`: { `page`: *number* = 1; `perPage`: *number* = 30 }): *Promise*<{ `accountAddress`: *string* ; `createAt`: Date ; `price`: *number* ; `transactionHash?`: *string* ; `type`: ItemLogTypeEnum  }[]\>

Returns the item transactional history.
It will return starting from the most recent.


#### Parameters:

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `itemId` | *string* | - | [Item](../modules.md#item)のitemId |
| `paging` | *object* | - | - |
| `paging.page` | *number* | 1 | - |
| `paging.perPage` | *number* | 30 | - |

**Returns:** *Promise*<{ `accountAddress`: *string* ; `createAt`: Date ; `price`: *number* ; `transactionHash?`: *string* ; `type`: ItemLogTypeEnum  }[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemLogs('Item.itemId')
```

Defined in: [src/index.ts:399](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L399)

___

### getItemShippingInfo

▸ **getItemShippingInfo**(`arg`: { `itemId`: *string*  }): *Promise*<InlineResponse2006\>

Returns the shipping info linked to the NFT item with a corresponding physical item.

{@link Items}From a security perspective, a Sign from the user is necessary

**Required**
- Requires a wallet to be connected.
- The users [Item](../modules.md#item) `type` must be `nftWithPhysicalProduct`
- [Item](../modules.md#item) must be either withdrawn or bought. Must also have a corresponding [Token](../modules.md#token)
- The user's [Item](../modules.md#item) `physicalOrderStatus` must be either `wip` or `ship`.
- The user must be the owner of the [Token](../modules.md#token).

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `arg` | *object* | itemId = itemId of an [Item](../modules.md#item) |
| `arg.itemId` | *string* | - |

**Returns:** *Promise*<InlineResponse2006\>

Defined in: [src/index.ts:889](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L889)

___

### getItems

▸ **getItems**(`__namedParameters?`: { `itemType?`: ``"nft"`` \| ``"nftWithPhysicalProduct"`` ; `networkId?`: [*NetworkId*](../modules.md#networkid)[] ; `onSale?`: *boolean* ; `page`: *number* ; `perPage`: *number* ; `sort?`: { `order`: ``"asc"`` \| ``"desc"`` ; `sortBy`: ``"endAt"`` \| ``"startAt"`` \| ``"price"``  } ; `tradeType?`: ``"fixedPrice"`` \| ``"auction"`` \| ``"autoExtensionAuction"``  }): *Promise*<[*Item*](../modules.md#item)[]\>

Returns the Items with the flag `Items.openStatus === 'open'`,
The status of the items can be changed from the admin panel


#### Restrictions

Please take caution of the following restrictions

- If specified as `tradeType === 'fixedPrice'`, it cannot be sorted by `'endAt' | 'startAt'`.
- If specified as `tradeType === 'auction'`, it cannot be sorted by `price`.
- If specified as`onSale`, it cannot be sorted by `startAt`.

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `__namedParameters` | *object* | - |
| `__namedParameters.itemType?` | ``"nft"`` \| ``"nftWithPhysicalProduct"`` | - |
| `__namedParameters.networkId?` | [*NetworkId*](../modules.md#networkid)[] | If there is no specification, the constructor value will be used.|
| `__namedParameters.onSale?` | *boolean* |  |
| `__namedParameters.page` | *number* | Amount of pages.  |
| `__namedParameters.perPage` | *number* | Amount of items per page. Default to 30.  |
| `__namedParameters.sort?` | *object* | `'endAt','startAt'` is valid when Item is on sale as an auction. It can be sorted from the starting or ending auction time. `price` is valid only when Item is on sale as a fixed price. |
| `__namedParameters.sort.order` | ``"asc"`` \| ``"desc"`` | - |
| `__namedParameters.sort.sortBy` | ``"endAt"`` \| ``"startAt"`` \| ``"price"`` | - |
| `__namedParameters.tradeType?` | ``"fixedPrice"`` \| ``"auction"`` \| ``"autoExtensionAuction"`` | - |

**Returns:** *Promise*<[*Item*](../modules.md#item)[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)

const items = await sdk.getItems({ onSale: true })
```

Defined in: [src/index.ts:261](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L261)

___

### getItemsByBidderAddress

▸ **getItemsByBidderAddress**(`address`: *string*): *Promise*<[*Item*](../modules.md#item)[]\>

Returns the bidding history of a specified address.

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `address` | *string* | wallet address |

**Returns:** *Promise*<[*Item*](../modules.md#item)[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
const item = await sdk.getItemsByBidderAddress('0x1111......')
```

Defined in: [src/index.ts:332](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L332)

___

### getServerUnixTime

▸ **getServerUnixTime**(): *Promise*<number\>

Returns the server date in  unix time.

**Returns:** *Promise*<number\>

unix time (ms)

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet() 
await sdk.getServerUnixTime()  // ex) 1615444120104
```

Defined in: [src/index.ts:733](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L733)

___

### getTokensByAddress

▸ **getTokensByAddress**(`address`: *string*): *Promise*<[*Token*](../modules.md#token)[]\>

Returns a list of tokens acquired using MINT from the specified address.


#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `address` | *string* | Address of a wallet |

**Returns:** *Promise*<[*Token*](../modules.md#token)[]\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...
const tokens = await sdk.getTokensByAddress('0x11111...')
```

Defined in: [src/index.ts:431](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L431)

___

### isCorrectNetwork

▸ **isCorrectNetwork**(): *Promise*<boolean\>

Returns if a network is appropriate.


**Returns:** *Promise*<boolean\>

Returns true, if appropriate.


```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.isCorrectNetwork() // true
```

Defined in: [src/index.ts:766](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L766)

___

### isInjectedWallet

▸ **isInjectedWallet**(): *boolean*

Validates if utilizing MetaMask.

**Returns:** *boolean*

Returns true if utilizing MetaMask.


```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.isInjectedWallet() // true
```

Defined in: [src/index.ts:750](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L750)

___

### isWalletConnect

▸ **isWalletConnect**(): *Promise*<boolean\>

Returns if an account is valid.

**Returns:** *Promise*<boolean\>

If a wallet is connected, returns true

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
await sdk.isWalletConnect()
```

Defined in: [src/index.ts:153](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L153)

___

### onAccountsChange

▸ **onAccountsChange**(`callback`: (`accounts`: *string*[]) => *any*): *void*

Set a callback when the account has been changed.


#### Parameters:

| Name | Type |
| :------ | :------ |
| `callback` | (`accounts`: *string*[]) => *any* |

**Returns:** *void*

void

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
sdk.onAccountsChange((accounts: string[]) => {
   // some thing
})
```

Defined in: [src/index.ts:659](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L659)

___

### onConnect

▸ **onConnect**(`callback`: () => *any*): *void*

Set a callback when the wallet is connected.

#### Parameters:

| Name | Type |
| :------ | :------ |
| `callback` | () => *any* |

**Returns:** *void*

void

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
sdk.onConnect(() => {
   // some thing
})
```

Defined in: [src/index.ts:684](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L684)

___

### onDisconnect

▸ **onDisconnect**(`callback`: () => *any*): *void*

Set a callback when the wallet is disconnected.


#### Parameters:

| Name | Type |
| :------ | :------ |
| `callback` | () => *any* |

**Returns:** *void*

void

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'
const sdk = await MintSDK.initialize(...)
sdk.onDisconnect(() => {
   // some thing
})
```

Defined in: [src/index.ts:709](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L709)

___

### registerItemShippingInfo

▸ **registerItemShippingInfo**(`arg`: { `itemId`: *string* ; `shippingInfo`: *Omit*<[*RegisterItemShippingInfoRequestBody*](../interfaces/registeritemshippinginforequestbody.md), ``"tokenId"`` \| ``"signedData"`` \| ``"chainType"`` \| ``"networkId"`` \| ``"contractAddress"``\>  }): *Promise*<void\>

Registers the shipping info for an Item associated with a physical item.
Please prepare a form for the user to input their shipping info. 

**Required**
- Requires a wallet to be connected.
- The user [Item](../modules.md#item) `type` must be `nftWithPhysicalProduct`.
- [Item](../modules.md#item) must be withdrawn or bought. Must be associated with（[Token](../modules.md#token))
- The user [Item](../modules.md#item) `physicalOrderStatus` must be `shippingInfoIsBlank`.
- The user must be the owner of the [Token](../modules.md#token).

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `arg` | *object* | itemId = the itemId of an [Item](../modules.md#item), shippingInfo = the shipping info of the Item. |
| `arg.itemId` | *string* | - |
| `arg.shippingInfo` | *Omit*<[*RegisterItemShippingInfoRequestBody*](../interfaces/registeritemshippinginforequestbody.md), ``"tokenId"`` \| ``"signedData"`` \| ``"chainType"`` \| ``"networkId"`` \| ``"contractAddress"``\> | - |

**Returns:** *Promise*<void\>

Defined in: [src/index.ts:809](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L809)

___

### sendTxBid

▸ **sendTxBid**(`itemId`: *string*, `bidPrice`: *number*): *Promise*<TransactionResponse\>

Creates a transaction from the specified bid price.
The total amount of the bid is passed through the `bidPrice` argument.


**Required**
- Requires a wallet to be connected.

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `itemId` | *string* | [Item](../modules.md#item)のitemId |
| `bidPrice` | *number* | unit is in ether |

**Returns:** *Promise*<TransactionResponse\>

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

___

### sendTxBuyItem

▸ **sendTxBuyItem**(`itemId`: *string*, `userResidence?`: ``"unknown"`` \| ``"jp"``): *Promise*<TransactionResponse\>

Creates a transaction for buying an Item at a fixed price.
Requires a UI that asks for the users residence for accommodating for consumption tax purposes.


**Required**
- Requires a wallet to be connected.

#### Parameters:

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `itemId` | *string* | - | The itemid of an [Item](../modules.md#item) |
| `userResidence` | ``"unknown"`` \| ``"jp"`` | 'unknown' | [Residence](../modules.md#residence) Specifies the buyers residence |

**Returns:** *Promise*<TransactionResponse\>

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

___

### sendTxMakeSuccessfulBid

▸ **sendTxMakeSuccessfulBid**(`itemId`: *string*, `userResidence?`: ``"unknown"`` \| ``"jp"``): *Promise*<TransactionResponse\>

オークションで勝利したアイテムを引き出すトランザクションを発行
ユーザーの居住地を問うUIを合わせて実装必要です。居住地を設定することで消費税に関する会計処理などがスムーズに行えます

**Required**
- Requires a wallet to be connected.
- **自動延長オークションは、`withdrawableAt`以降に引き出し可能です**

#### Parameters:

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `itemId` | *string* | - | The itemId of [Item](../modules.md#item) |
| `userResidence` | ``"unknown"`` \| ``"jp"`` | 'unknown' | [Residence](../modules.md#residence) Specifies the buyers residence |

**Returns:** *Promise*<TransactionResponse\>

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

___

### updateAccountInfo

▸ **updateAccountInfo**(`arg`: { `avatarImageId`: *string* ; `bio`: *string* ; `displayName`: *string* ; `homepageUrl`: *string* ; `instagramAccountName`: *string* ; `twitterAccountName`: *string*  }): *Promise*<void\>

Can update the wallet address image and display name. 
All items are optional, but should not be set as blank string.
The return value of `avatarImageId` is `sdk.uploadImg`.

**Required**
- Requires a wallet to be connected.

#### Parameters:

| Name | Type |
| :------ | :------ |
| `arg` | *object* |
| `arg.avatarImageId` | *string* |
| `arg.bio` | *string* |
| `arg.displayName` | *string* |
| `arg.homepageUrl` | *string* |
| `arg.instagramAccountName` | *string* |
| `arg.twitterAccountName` | *string* |

**Returns:** *Promise*<void\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
const imgId = await sdk.uploadAvatarImg()
await sdk.updateAccountInfo({ imgId, .... })
```

Defined in: [src/index.ts:970](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L970)

___

### uploadAccountInfoAvatar

▸ **uploadAccountInfoAvatar**(`arg`: { `file`: File  }): *Promise*<{ `imgId`: *string* ; `uploadedImgUrl`: *string*  }\>


Returns the `imgId` from the `sdk.updateAccountInfo`.
uploadedImgUrl is a read-only URL for the uploaded image.

**Required**
- Requires a wallet to be connected.

#### Parameters:

| Name | Type |
| :------ | :------ |
| `arg` | *object* |
| `arg.file` | File |

**Returns:** *Promise*<{ `imgId`: *string* ; `uploadedImgUrl`: *string*  }\>

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = MintSDK.initialize(...)
await sdk.connectWallet()
const { imgId, uploadedImgUrl } = await sdk.uploadAccountInfoAvatar({ file })
```

Defined in: [src/index.ts:1045](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L1045)

___

### waitForTransaction

▸ **waitForTransaction**(`txHash`: *string*): *Promise*<void\>

When the transaction is successful, it returns a Resolve.

**Required**
- Requires a wallet to be connected.

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `txHash` | *string* | The hash property of {@link ethers.providers.TransactionResponse}  ```typescript import { MintSDK } from '@kyuzan/mint-sdk-js' const sdk = await MintSDK.initialize(...) await sdk.connectWallet() // required try {  const tx = await sdk.sendTxBuyItem('item.itemId')  await tx.wait()  // success transaction } catch (err) {  // display error message } ``` |

**Returns:** *Promise*<void\>

Defined in: [src/index.ts:231](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L231)

___

### formatEther

▸ `Static`**formatEther**(`bg`: *BigNumber*): *string*

Returns an BigNumber that is formatted as an ether.

#### Parameters:

| Name | Type |
| :------ | :------ |
| `bg` | *BigNumber* |

**Returns:** *string*

Returns an ether parsed as a string. 

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

const sdk = await MintSDK.initialize(...)
await sdk.connectWallet()  // required
const walletInfo = await sdk.getWalletInfo()
MintSDK.formatEther(walletInfo.balance) // 3.2
```

Defined in: [src/index.ts:83](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L83)

___

### parseEther

▸ `Static`**parseEther**(`ether`: *string*): *BigNumber*

Returns the ether price as a BigNumber.

#### Parameters:

| Name | Type | Description |
| :------ | :------ | :------ |
| `ether` | *string* | Shown as an ether unit |

**Returns:** *BigNumber*

Returns an ether that is parsed as a BigNumber.

```typescript
import { MintSDK } from '@kyuzan/mint-sdk-js'

MintSDK.parseEther('3.2') // BigNumber
```

Defined in: [src/index.ts:64](https://github.com/KyuzanInc/annapurna-sdk-js/blob/5eef657/src/index.ts#L64)
