# check-edge
 Checks the status of Edge host node and posts it to a Telegram bot

<img src="https://github.com/befranz/check-edge/blob/master/img/edge-bot.jpg">

This script executes a procedure to check the local Edge node installation as part of the [Edge Network](https://edge.network/en/). If it finds any failed status it will send a message to a Telegram Bot server. The script avoids sending recurring messages with the same status.

## Telegram Bot Server
There's already a working Telegram Bot server you can use and which is set as default.

If you want to install your own Bot server, check this repository: [EdgeTelegramBot](https://github.com/maxxar92/EdgeTelegramBot)

## Setup of check-edge

### Requirements
This script was tested on Debian, Ubuntu and Raspbian. You may try to install it on other platforms, feedback is appreciated.

To install and run this script, **cURL** has to be installed on your machine. If you are not sure about this, just run these commands which install cURL if it's not already done:

```
sudo apt update
sudo apt install curl
```

The check procedure itself (`edge-cli check`) needs to run as **root** therefore it's necessary for check-edge too.

### Installation
Start the installation with this one-line command:

```
curl -s https://raw.githubusercontent.com/befranz/check-edge/master/install-check-edge|bash&&source $HOME/.profile
```

This install script
- creates a folder in the root home folder (`/root/scripts`)
- downloads the script into this folder
- adds the path of this folder to the existing path in `/root/.profile`

### First Start of the Script
When you start the script the first time by:

```
check-edge
```

a configuration file (`/root/scripts/check-edge.cfg`) is created which is ready if you want to use the Edge Community Bot server.

Copy your **DEVICE-ID**, you will need it to register your node on the Telegram Bot.

### Register your Node on the Telegram Bot
Connect to the **Edge Community Bot** (@edge_community_bot) and register your Device-ID:

```
/register xxxxxxxxxx
```

### Usage
Now you're ready to get your first message from your node on Telegram. To post a message even if there's no issue, run the script with the additional command **post**:

```
check-edge post
```

### Run Script via Cron
With the following command you create a Crontab entry which will start the script every 30 minutes:

```
check-edge setcron
```

Changes to this default settings can be made by `crontab -e` but please be cautious to use the right syntax.

### Other Commands
Further commands are shown by `check-edge help`.

## Contact
Error reports and suggestions please via Github/Issues or PM on Telegram (@befranz)
