## 3.2 - Item identifying parameter

You have 3 choices of item identifying parameters on how you want to add your items:

1. `item` **(recommended)** - The item's full name. For example: `Max's Severed Head`
2. `sku` **(recommended)** - The item "Stock Keeping Unit".
3. `name` - Must be the item based name (without any quality/effect/Killstreak and etc)
4. `defindex` - The item definition index. You can find it [here](https://wiki.alliedmods.net/Team_Fortress_2_Item_Definition_Indexes) or [here](https://docs.google.com/spreadsheets/d/11bv5J-l1UCNjvTF2FyiqivbQds8LxBCQj0QBpw6Ukec/edit#gid=0)

## 3.2.1 - `item` parameter

This is a new parameter added to the v4.0.0 update. You can just simply add an item with its full name.
Example:
- `Max's Severed Head`
- `Taunt: The Schadenfreude`
- `Terror-Watt Stately Steel Toe`
- `Specialized Killstreak Powerjack`
- `Strange Frozen Aurora Shortstop (Factory New)`
- `Bill's Hat (Paint: The Bitter Taste of Defeat and Lime)`

**Note**: Please report to our Discord server if you're unable to add any item because the return `sku` was invalid.

===

## 3.2.2 - `sku` parameter

This parameter is recommended because you will no longer need to use the sub-parameters in [Table 3.2](#3.2.1---`name`-and-`defindex`-parameters).
So how can I find the sku of a specific item?

#### Using marketplace.tf
-   Go to [Marketplace.tf](https://marketplace.tf/).
-   In the search bar, type in the item name or Unusual effect, or anything related.
-   If "No items found", simply click on the "In stock" button two to the right of the search bar and it will change to "Not In Stock".
-   If your desired item appeared, click on it and take a look at the URL. The item sku is right at the end of the URL.
<div align="center"><img src="https://media.giphy.com/media/Pj78znBQro1BZu0CiE/giphy.gif" alt="listings" style="display: block; margin-left: auto; margin-right: auto;"></div>

#### Using `!sku` command
-   You can use the !sku command in the steam chat to obtain the sku. You will need to use the full item name.
-   Example: <div align="center"><img src="https://cdn.discordapp.com/attachments/666909760666468377/845365874151653396/unknown.png" alt="listings" style="display: block; margin-left: auto; margin-right: auto;"></div>


### General `sku` format

`defindex;quality[;uncraftable[;untradable[;australium[;festive[;strange[;kt-#[;u#[;p#[;pk#[;w#[;td-#[;n-#[;c-#[;od-#[;oq-#]]]]]]]]]]]]]]]`

- Compulsory parts:
    - `defindex`: The defindex of an item; and
    - `quality`: The quality of an item.
- Optional parts:
    - `uncraftable`: Parameter `craftable`, if included, then the item is Non-Craftable.
    - `untradable`: If included, then the item is Non-Tradable.
    - `australium`: Parameter `australium`, for **Australium** items.
    - `festive`: Parameter `festive`, for **Festivized** items.
    - `strange`: For any Strange as second quality, i.e. **Strange Unusual**, **Strange Haunted**, **Strange Genuine** and etc.
    - `kt-#`: Parameter `killstreak` level, replace `#` with either 1, 2, or 3.
    - `u#`: Parameter `effect`, replace `#` with a valid Unusual Effect ID.
    - `p#`: Parameter `paint`, replace `#` with a valid [Paint Decimal number or Paint partial sku](./Library#paints-).
    - `pk#`: Parameter `paintkit`, replace `#` a valid Paint Kit ID.
    - `w#`: Parameter `wear`, replace `#` with a number, 1 (Factory New) - 5 (Battle Scarred).
    - `td-#`: Parameter `target`, replace `#` with targeted item defindex.
    - `n-#`: (not yet supported) Item with number #.
    - `c-#`: Parameter `crateseries`, replace `#` with crate number.
    - `od-#`: Parameter `output`, replace `#` with output item defindex.
    - `oq-#`: Parameter `outputQuality`, replace `#` with a valid Quality ID.

===

## 3.2.3 - `name` and `defindex` parameters (not recommended)

These two parameters act the same since the defindex (in integer form) is just a replacement for the name of an item (if the bot failed to choose the item, so it needs more specific detail of an item). There are 14 _optional_ sub-parameters under these two item identifying parameters:

_Table 3.2: Sub-parameters for `name` and `defindex`._

|   Parameter  |    Type   | Default  | Description |
| :----------: | :-------: | :------: | :---------- |
|  `quality`   | `string`  | `Unique` | Normal/ Genuine/ Vintage/ Unusual/ Unique/ Community/ Valve/ Self-made/ Strange/ Haunted/ Collector's/ Decorated (this is case sensitive). If not stated, it will default to `Unique`. |
| `craftable`  | `boolean` |  `true`  | Set to `false` if you want the item to be a Non-Craftable. |
| `australium` | `boolean` | `false`  | Set to `true` if you want that item to be an Australium (Australium-able weapons only). |
|   `effect`   | `string`  |  `null`  | An Unusual effect name, for example: `Sunbeams` or `Green Confetti`. |
| `killstreak` | `number\|string`  |   `0`    | This should be killstreak type. Types: `1` or `Killstreak`, `2` or `Specialized Killstreak`, and `3` or `Professional Killstreak`. |
|  `festive`   | `boolean` | `false`  | Set to `true` if the item is Festivized. |
|  `quality2`  | `boolean` |  `false` | Set to `true` if you want to add Strange as second quality item, i.e., Strange Unusual, Strange Haunted and etc. |
|  `paintkit`  | `string`  |  `null`  | When adding a decorated weapon/skin. This should be the War Paint name (sell order only). |
|    `wear`    | `number\|string`  |  `null`  | When adding a decorated weapon/skin. This should be wear type (i.e., `1` for `Factor New`, or can just be `Factory New`). |
|   `paint`    | `string`  | `null` | Include this if you want to add a painted item to sell. Should be the full name of the paint that you want (i.e., `After Eight`) |
|   `target`   | `number\|string` | `null` | You will need to include this if you want to add `Unusualifier`, `Strangifier`, `Kit`, or `Fabricator` to the pricelist. It should be the targeted item name or defindex. For example for adding `Killstreak Scattergun Kit`, it will be `target=Scattergun` or `target=200` |
|  `output`    | `number\|string`  |  `null`  | When adding any targeted item with output (i.e., `Fabricator`, `Chemistry Set`), this must be included. |
| `outputQuality` | `string` | `null` | The same as `quality` parameter, but this one is for `Collector's Chemistry Set`, which should be always `Collector's` |
| `crateseries` | `number` | `null` | Specify crate series, usually only use for Mann Co. Supply Crate and Mann Co. Salvaged Supply Crate |



Continue: [Listing settings parameters](./Listing-settings-parameters)