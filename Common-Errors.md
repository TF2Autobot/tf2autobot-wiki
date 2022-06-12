This page contains common errors and ways to fix them.

# Table of Contents

- [Startup errors](#startup-errors)
   - [Missing required enviroment variable](#missing-required-enviroment-variable)
      - [ecosystem.json](#ecosystemjson)
      - [.env](#env)
   - [Unknown SteamID input format](#unknown-steamid-input-format)
   - [Access denied](#access-denied)
   - [Ratelimit exceeded](#ratelimit-exceeded)
   - [Could not get account limitations](#could-not-get-account-limitations)
   - [TypeError: input.match is not a function](#typeerror-inputmatch-is-not-a-function)
- [Other errors](#other-errors)
   - [Corrupted JSON file](#corrupted-json-file)
      - [polldata.json](#polldatajson-corruption)
      - [pricelist.json](#pricelistjson-corruption)
      - [options.json](#error-in-optionsjson)
   - [Reason: Failed to accept mobile confirmation.](#reason-failed-to-accept-mobile-confirmation)
   - [warn: Socket connection error xhr poll error](#warn-socket-connection-error-xhr-poll-error)

# Startup errors
## Missing required environment variable
When updating your environmental variables, almost make sure you restart the bot with the `--update-env` option if you are using PM2. As explained [here](https://github.com/idinium96/tf2autobot/wiki/Updating-the-bot#updating-the-environment-file) 
### `ecosystem.json`
You need to make sure your file is **NOT** called `ecosystem.template.json`. It needs to be `ecosystem.json`.  

### `.env`
Before trying to fix this error, you should [enable viewing file extensions](https://fileinfo.com/help/windows_10_show_file_extensions).  
**MAKE SURE THE FILE IS NOT CALLED** `config.env` OR `bot.env` OR ANYTHING. JUST `.env` (a dot and "env").  
If your computer does not allow you to name it `.env`, simply call it `.env.` (with the extra `.`).

![image](https://cdn.discordapp.com/attachments/666909760666468377/872319195814178846/unknown.png)

## Unknown SteamID input format
In your `.env` or `ecosystem.json`, the `ADMINS` and `KEEP` options need to have valid SteamID64's in them. For example: `76561198144346135` is a valid SteamID64.  
You can find this on [SteamRep](https://steamrep.com/) or on your [Backpack.tf profile](https://backpack.tf/my)

## Access denied
Your Steam account(s) needs to be [unlimited](https://support.steampowered.com/kb_article.php?ref=3330-IAGK-7663). To make your Steam account(s) unlimited you need to add $5 or more to the Steam account(s) [here](https://store.steampowered.com/steamaccount/addfunds) (remember to be logged into the bot(s)' account). If you're using another currency than USD, you might need to add more than $5 due to conversion rates.

## Ratelimit Exceeded
You have logged in too many times (possibly due to it crashing and restarting too often). Stop the bot for an hour and then start it again.

## Could not get account limitations
As it says in the console with the message about the error, set `SKIP_ACCOUNT_LIMITATIONS` to `true` in your `.env` or `ecosystem.json`.

## TypeError: input.match is not a function
The error looks like this:
![https://i.imgur.com/fZ9bFLr.png](https://i.imgur.com/fZ9bFLr.png "error")

This is caused, by not adding `" "` between the SteamID64 you added in your `ITEM_STATS_WHITELIST` variable inside your environment file (on Windows: `.env` - on Linux: `ecosystem.json`).

The array should look like this: `["SteamID64"]` 
You can also leave it empty if you are the only person who should use that command. This is because you, as the owner, can use this command no matter what's inside that array.

# Other errors

## Corrupted JSON file
These errors are usually caused by either your `polldata.json` or your `pricelist.json` being corrupted. You should examine the error in your log and see if it matches the one of the [polldata.json corruption](#polldatajson-corruption) or the [pricelist.json corruption](#pricelistjson-corruption).

### polldata.json corruption
There are multiple cases where this may happen. If your error looks somewhat like this: ![https://cdn.discordapp.com/attachments/666909760666468377/844357949723246612/unknown.png](https://cdn.discordapp.com/attachments/666909760666468377/844357949723246612/unknown.png "error")  
Then something went wrong with your `polldata.json` file. This is located in the `tf2autobot/files/{your steamid}/` folder. Simply deleting it will fix the issue.

### pricelist.json corruption
If your error looks somewhat like this: ![https://cdn.discordapp.com/attachments/699642379266686997/846110244782473286/hf3f2tK.png](https://cdn.discordapp.com/attachments/699642379266686997/846110244782473286/hf3f2tK.png "error")

Then your `pricelist.json` is corrupted which is very bad because it holds all of the items you added to your pricelist. You **should not** delete this file and instead ask in the discord server for help.

**Making a regular backup of your `pricelist.json` file is always recommended.**

### Error in options.json
If your error looks somewhat like this:

![https://cdn.discordapp.com/attachments/745410459212972173/785284924650553344/unknown.png](https://cdn.discordapp.com/attachments/745410459212972173/785284924650553344/unknown.png "error")

You should check out the mentioned line (here: line 27) in your options.json file to see if there are any syntax errors (here: missing quotes around Team Shine).

### Unexpected token in JSON error
If you get an error somewhat like this:
```cmd
SyntaxError: Unexpected token o in JSON at position 1
    at JSON.parse (<anonymous>)
    at new Bot (C:\Users\Name\Desktop\Edited\dist\classes\Bot.js:74:72)
```
Or something similar, then you did not set your `ALERTS` properly in your `.env` or `ecosystem.json`.  
It is supposed to look like `["trade"]` or `["none"]`. This error usually happens if you forget the `[]` brackets.

---

## Reason Failed to accept mobile confirmation
The bot may produce this error when a user attempts to trade using the !buy or !sell commands.  
This issue occurs when SDA is left open. Please close SDA.

## warn: Socket connection error xhr poll error
If your error looks like this:  
![https://i.imgur.com/m6w2Yyj.png](https://i.imgur.com/m6w2Yyj.png)

Then you are using a node version that is not supported.  

To fix the issue;  
On Windows: Uninstall NodeJS then download the LTS version from https://nodejs.org/en/  
On Ubuntu(Linux): 
```bash
npm i -g n && n lts
```
then
```bash
node -v
```
and make sure output starts with `v14`