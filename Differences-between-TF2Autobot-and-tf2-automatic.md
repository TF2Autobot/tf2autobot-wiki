## Difference between TF2Autobot and tf2-automatic

TF2Autobot adds advantageous features on top of the original features in the tf2-automatic repository. Let me list some notable features in the original tf2-automatic and some that have been added in TF2Autobot:

### Original tf2-automatic

-   Free auto pricing (using prices from [prices.tf](https://prices.tf/)) and unlimited listings (only limited by your backpack.tf listings cap).
-   Automatically craft/smelt pure metal (to maintain supply in all metal types).
-   Dupe check on items that are more than a certain amount of keys (you decide/set the number of keys).
-   Trade offer review (if you were offered an invalid value/item, the item is overstocked, or the item is duped).

### TF2Autobot version

-   All tf2-automatic features
-   **Discord Webhook:**
    -   Use Discord Webhooks for your bot to send accepted trade summaries, pending trade offer reviews, and/or private messages to a Discord server.
    -   Disable mention owner on pending trade offers with `INVALID_VALUE`.
-   **Autokeys:**
    -   Enable Autokeys (to maintain ample refined metal stock) and key banking.
-   **Manual review:**
    -   Send the trade partner a summary of their offer if it needs to be reviewed.
    -   Automatically accept trades that underpay by a certain amount of refined with `INVALID_VALUE exception` (you decide/set the amount of refined and can be enabled only for certain item qualities).
    -   Automatically decline (skip manual review) **ONLY** `INVALID_VALUE` trade (if it does not meet the set requirements for `INVALID_VALUE exception`).
    -   Automatically accept (skip manual review) `INVALID_ITEMS` or `OVERSTOCKED` trades if the trade partner offers to overpay (will mention owner on Discord Webhook).
    -   New `UNDERSTOCKED` and `DISABLED_ITEMS` reasons for manual review.
    -   Option to automatically decline `OVERSTOCKED` or `UNDERSTOCKED` reason.
    -   List all reasons and items for each trade offer review.
-   **Support craft weapons as currency:**
    -   Set craft weapons as currency (0.05 ref) and automatically craft duplicated craftable weapons and matched class weapons into metal (if not in pricelist).
-   **Option to only accept full uses items:**
    -   Dueling Mini-Game check - only accept 5 Uses!
    -   Noise Maker check - only accept 25 Uses!
-   **Custom Listing Note:**
    -   Set a custom buy or sell order listing note for any item of your choice!
-   **Items Grouping in pricelist:**
    -   Set a group for specific items in your pricelist so it will be easy to manage, such as if you only want to update `intent=bank` to `intent=sell` to only "craftHats" items group!
-   **Support creating separate listings for painted items!**
    -   You have an option to make your bot recognize painted items as different than other non-painted items.
-   **Customs:**
    -   Set your own custom greeting, success/failed messages, and/or trade offer review notes.
    -   Set your custom playing game name.
    -   Option to only play Team Fortress 2.
    -   Disable "show only metal" in the trade summary (it will show x keys, y ref instead of just x ref on the original version).
    -   Option to disable accept friend requests and disable invite people to join Steam groups.
    -   Option to recognize Strange as Second Quality (such as Strange Unusual, Strange Genuine and etc) as usual single Quality and vice versa.
    -   Option to recognize Festivized items as non-Festivized.
-   **Improvements:**
    -   Request price check to prices.tf after every successful trade on each item involved in the trade (except craft weapons and pure).
    -   Option to request for `INVALID_ITEMS` (items that are not in your pricelist) to be priced by Prices.TF.
    -   Automatically add accepted `INVALID_ITEMS` to the pricelist (if priced with prices.tf and not from ADMINS) with autoprice set to true and intent to sell, which when sold, will be automatically removed.
    -   Notify the owner if someone traded high-valued items (spelled, user-selected sheens, killstreakers, strange parts, and paints).
    -   Automatically inform the owner and temporarily disable item bought if it contains high-valued.
    -   Use the infinity symbol (∞) for infinite stock (maximum set to -1).
    -   Able to promote sell orders (Backpack.tf Premium only)!
    -   Able to create **sell orders** for specific Mann Co. Supply Crate, Mann Co. Supply Munition and, Salvaged Mann Co. Supply Crate series and Skins/War Paint!
    -   Support **buy orders** for targeted specific items such as Crates, Unusualifier, Strangifier, Killstreak Kit, Killstreak Kit Fabricator and Chemistry set!
    -   Added the ability to donate to Backpack.tf with `!donatebptf` command!
-   **Others:**
-   emojis on almost all messages.
-   newly added commands: "!pure", "!time", "!delete", "!check", "!block", "!unblock", "!autokeys", "!refreshautokeys", "!refreshlist", "!find", "!inventory", and more!

More info in the [Releases](https://github.com/TF2Autobot/tf2autobot/releases) note pages.

## Added features

### Discord Webhook feature

Instead of your bot sending trade summaries, trade offer reviews, and messages to you via Steam Chat, your bot is able to send it to different channels in your Discord server!
If you want to interact with the trade offer reviews and messages sent by your Discord Webhook, you must install [tf2-autocord](https://github.com/TF2Autobot/tf2-autocord).

Screenshots:

-   Trade summary (or live-trades) -

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/89725250-1434fb00-da40-11ea-8ccc-8755b1af89c6.PNG" alt="trade-summary" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   Offer review (when trade partner sent wrong value/overstocked/etc) -

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/85020166-80168800-b1a2-11ea-99f2-04766677fdf7.PNG" alt="Offer-review" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   Messages (when the trade partner uses "!message" command -

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581313-9cb56780-ae12-11ea-9dcf-2d660d8ae184.PNG" alt="Messages" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   Price update (Discord Only) - Show the price changes for each item on your pricelist -

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/83712639-cc1ce500-a658-11ea-855d-5de43b39ff2f.png" alt="price-update" style="display:block;margin-left:auto;margin-right:auto;"></div>

You can also set it to send only the trade summary via Discord and have others (like Offer review and Messages) still sent to you via Steam Chat.

Note: it's also an option to show key rate/pure stock/quick links on each Webhook message.

If you want to use this feature, you must use the [ecosystem.template.json](https://github.com/TF2Autobot/tf2autobot/blob/master/template.ecosystem.json) from this version. It contains many more variables for you to fill in.

### Autokeys (auto-buy or sell keys) feature

When this feature is enabled, your bot will automatically buy or sell keys depending on the amount of pure your bot currently has. You'll need to set your minimum/maximum keys and minimum/maximum refined metals in your options.json file. Additional explanation can be found [here](./Configure-your-options.json-file#-autokeys-settings-).

```
.____________________________________________________________.  ._______________________________.
|       **Buying Keys**       |       **Selling Keys**       |  |       **Banking Keys**        |
|       ***************       |       ****************       |  |       ****************        |
|        <———————————○        |            ○————————————>    |  |            ○————————————>     |
| Keys -----|--------|----->  |  Keys -----|--------|----->  |  |  Keys -----|--------|----->   |_______________________________.
|                    ○———>    |         <——○                 |  |            ○————————○         |          **Disabled**         |
| Refs -----|--------|----->  |  Refs -----|--------|----->  |  |  Refs -----|--------|----->   |          ************         |
|          min      max       |           min      max       |  |           min      max        |         <——●                  |
|_____________________________|______________________________|  |______________________________.|  Keys -----|--------|----->   |
                |         **Disabled**        |                 |    **Buying when more ref**   |         <———————————●         |
                |         ************        |                 |          ************         |  Refs -----|--------|----->   |
                |        <——●————————●···>    |                 |         <——●                  |           min      max        |
                | Keys -----|--------|----->  |                 |  Keys -----|--------|----->   |_______________________________|
                |           ●————————●···>    |                 |            ○————————————>     |
                | Refs -----|--------|----->  |                 |  Refs -----|--------|----->   |
                |          min      max       |                 |           min      max        |
                |_____________________________|                 |_______________________________|
```

Some screenshots:

-   When your bot has enough keys to sell (when your ref < minimum) OR enough ref to buy more keys (when your ref > maximum and keys < max):

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581306-9a530d80-ae12-11ea-9bd5-3a988ac447d9.png" alt="autokeys1" style="display:block;margin-left:auto;margin-right:auto;"></div>

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581309-9b843a80-ae12-11ea-8374-0f7d3c631fa6.png" alt="autokeys2" style="display:block;margin-left:auto;margin-right:auto;"></div>

-   When your bot doesn't have enough keys to sell, Autokeys will not be active:

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84581310-9c1cd100-ae12-11ea-80fa-085ad8bff73e.png" alt="autokeys3" style="display:block;margin-left:auto;margin-right:auto;"></div>

You can see the code of this feature [here](https://github.com/TF2Autobot/tf2autobot/blob/master/src/classes/Autokeys/Autokeys.ts).

### Emojis and more commands added

#### Admin commands

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/92323077-5d409500-f068-11ea-8d44-4a6a127fbb10.png" alt="newlook-command-admin" style="display:block;margin-left:auto;margin-right:auto;"></div>

#### Trade partner commands

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/89725439-244dda00-da42-11ea-9ea8-f3e159c19cea.png" alt="newlook-command-partner" style="display:block;margin-left:auto;margin-right:auto;"></div>

### Offer review summary on the trade partner side

![review-note-trade-partner](https://user-images.githubusercontent.com/47635037/85020170-8147b500-b1a2-11ea-96b5-1805ad8cc31c.PNG)

### INVALID_VALUE exception

If you're having your bot trade  Unusuals or Australiums (which the value, as we know, is more than 5 keys), and someone sends a trade offer with 0.11 ref underpay, your bot will skip this offer and send you a notification to review this offer. With this exception, your bot will accept the trade as long as the underpay is less than the exceptional value that you've set. To use this feature, you'll need to set the exception value on both `INVALID_VALUE_EXCEPTION_SKUS` and `INVALID_VALUE_EXCEPTION_VALUE_IN_REF`. See [here](./Configuring-the-bot-using-the-environment-file#manual-review-settings).

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84966884-38adde80-b145-11ea-9aac-d28daf9a74e6.PNG" alt="Invalid_value_exception2" style="display:block;margin-left:auto;margin-right:auto;width:540px;height:450px;"></div>

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/84966887-39df0b80-b145-11ea-9d81-021d302e7cf0.PNG" alt="Invalid_value_exception2" style="display:block;margin-left:auto;margin-right:auto;"></div>

### New bot reply when adding/updating an item

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/99592362-13dad180-2a2b-11eb-83fb-1c1fb194211c.png" alt="new_bot_reply" style="display:block;margin-left:auto;margin-right:auto;"></div>

### Support buy orders for specific targeted items

<div align="center"><img src="https://cdn.discordapp.com/attachments/715362558256873492/777353181713399828/unknown.png" alt="buy_order_specific_targeted_items" style="display:block;margin-left:auto;margin-right:auto;"></div>

### Support sell orders as well as buy orders for Crates/Skins/War paints

_This was not possible on tf2-automatic._

<div align="center"><img src="https://cdn.discordapp.com/attachments/699642379266686997/775584447956254720/unknown-1.png" alt="sell_orders" style="display:block;margin-left:auto;margin-right:auto;"></div>

### High value items

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/99593484-adef4980-2a2c-11eb-97e6-7b538e62d0f9.png" alt="sell_orders" style="display:block;margin-left:auto;margin-right:auto;"></div>
