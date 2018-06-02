# Bot for Discord communties to facilitate crypto coin tipping!
(This README will be updated along with bot updates)
Features:

- Tipbot for any coin running the bitcoind client.
    - Help message `!tip`.
- Dynamic plugin loading with permission support.
- **out of the box Supported Coins**
    - Dogecoin (DOGE)
    - Ravencoin (RVN)
    - LBRY Credits (LBC)
    - Uniform Fiscal Object (UFO)
    - ~~Proton (PROTON)~~ Higgs(PROTON)
    - SECI

## Create a bot, get the bot's API Token, and invite the bot to your Discord with its client ID

Create your bot and grab it's API Token and CLient ID here: https://discordapp.com/developers/applications/me

Invite your bot to your discord channel by visiting the follow url and replacing the client id with your bot's client ID (different from API token). You can do this later if you wish, but the bot must be invited before it can come online in your server.

```https://discordapp.com/oauth2/authorize?client_id=CLIENTID&scope=bot```

## Install your wallet on the server machine

Wallet must be bitcoind based (ravend, secid, etc) (aka bitcoin-qt wallet).

## Auto-Installation Option (Manual Instructions Below)

This auto-install scrypt is for Windows Users Only!

### Setup your wallet config

In most cases, your wallets data folder can be found in `%appdata%` (default Roaming Folder), e.g. `C:\Users\USER\AppData\Roaming\COIN`.

Edit or create your `COIN.conf` file (Where "COIN" is the coin name) to include the following, where you should fill in the `rpcuser`, `rpcpassword`, and `rpcthreads`.

```
server=1
par=1
rpcbind=127.0.0.1
rpcallowip=127.0.0.1
rpcport=3335
rpcuser=<Same-as-you-set-in-config.json>
rpcpassword=<Same-as-you-set-in-config.json>
rpcclienttimeout=30
rpcthreads=<Number-of-Threads>
rpcworkqueue=1000
```

NOTE: if you are using a masternode coin you also need to add these to extra option into your wallets config file

```
staking=0
enableaccounts=1
```

Edit and rename the `default.json.example` file in `/config` to `default.json`

Edit the following according to your wallet's config options set in the previous step:

```
"ravend": {
    "port": 3335,
    "user": "username",
    "pass": "Do-Not-Use-This-Password-Youll-Be-Hacked-For-all-Teh-Moneys!"
},
```

(you can add more coins by following this format and using the `exampleTipper.js` file in `/bot/modules`)

Rename `ecosystem.config.js.example` to `ecosystem.config.js` and update the file paths in the file to the directories you want the log files to go to.

To start the install, run the `windows-install.bat` file!

And finally, run `pm2 start ecosystem.config.js`

The bot should come online in your channel, and you can run `!tiphelp` to get started!

ENJOY!

## Manual-Installation

## Requirements

- node > 8.0.0
- npm > 0.12.x
- yarn ( install with npm install -g yarn if not installed )

### Setup your wallet config

In most cases, your wallets data folder can be found in `%appdata%` (default Roaming Folder), e.g. `C:\Users\USER\AppData\Roaming\COIN`.

Edit or create your `COIN.conf` file (Where "COIN" is the coin name) to include the following, where you should fill in the `rpcuser`, `rpcpassword`, and `rpcthreads`.

```
server=1
par=1
rpcbind=127.0.0.1
rpcallowip=127.0.0.1
rpcport=3335
rpcuser=<Same-as-you-set-in-config.json>
rpcpassword=<Same-as-you-set-in-config.json>
rpcclienttimeout=30
rpcthreads=<Number-of-Threads>
rpcworkqueue=1000
```

NOTE: if you are using a masternode coin you also need to add these to extra option into your wallets config file

```
staking=0
enableaccounts=1
```

Edit and rename the `default.json.example` file in `/config` to `default.json`

Edit the following according to your wallet's config options set in the previous step:

```
"ravend": {
    "port": 3335,
    "user": "username",
    "pass": "Do-Not-Use-This-Password-Youll-Be-Hacked-For-all-Teh-Moneys!"
},
```

(you can add more coins by following this format and using the `exampleTipper.js` file in `/bot/modules`)

Rename `ecosystem.config.js.example` to `ecosystem.config.js` and update the file paths in the file to the directories you want the log files to go to.

Then run:

```
npm install
```

And finally:

```
pm2 start ecosystem.config.js
```

The bot should come online in your channel, and you can run `!tiphelp` to get started!

### Development

Be sure to run the command below before working on any code, this ensures
prettier goes to work and keeps code to our standard.

```
yarn install --production=false
```
to run prettier before submitting your code simply run the following in the bots root directory.

```
yarn precommit
```
