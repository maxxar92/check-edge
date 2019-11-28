#check-edge
 Checks the status of edge-cli and posts it to a Telegram bot

<img src="https://github.com/befranz/check-edge/blob/master/img/edgebot_img.jpeg" width="200">

This script executes a procedure to check the local Edge node installation as part of the [Edge Network](https://edge.network/en/). If it finds any failed status it will send a message to a Telegram Bot server. The script avoids sending recurring messages with the same status.

##Telegram Bot Server
There's already a working Telegram Bot server you can use. Ask the Edge Community on [Telegram](https://t.me/edgenetwork) or [Discord](https://discord.gg/GmaxgsK) for the specific URL of this server.

If you want to install your own Bot server, check this repository: [EdgeTelegramBot](https://github.com/maxxar92/EdgeTelegramBot)

##Setup of check-edge

###Requirements
This script was tested on Debian, Ubuntu and Raspbian. You may try to install it on other platforms, feedback is appreciated.

To install and run this script, *cURL* has to be installed on your machine. If you are not sure about this, just run these commands which install cURL if it's not already done:

```
sudo apt update
sudo apt install curl
```

The check procedure itself (edge-cli check) needs to run as *root** there it's necessary for check-edge too.

###Installation
Start the installation with this one-line command:

```
curl -s https://raw.githubusercontent.com/befranz/check-edge/master/install-check-edge|bash&&source $HOME/.profile
```

This install script
- creates a folder in the root home folder (/root/scripts)
- downloads the script into this folder
- adds the path of this folder to the existing path in .profile

###First Start of the Script
When you start the script the first time by:

```
check-edge
```

a configuration file is created which you have to edit by

```
nano /root/scripts/check-edge.cfg
```

Change *SERVERURL* to the URL you got from the Edge community.
Copy your *DEVICEID*, you will need it to register your node on the Telegram Bot.
Save the file by `CTRL-X Y <Enter>`.

###Register your Node on the Telegram Bot
Connect to the *Edge Community Bot* (@edge_community_bot) and register your Device-ID:

```
/register xxxxxxxxxx
```

###Usage
Now you're ready to get your first message from your node on Telegram. To post a message even if there's no issue, run the script with the additional command *post*:

```
check-edge post
```

###Run Script via Cron
With the following command you create a Crontab entry which will start the start every 30 minutes:

```
check-edge setcron
```

Changes to this default settings can made by `crontab -e` but please be cautious to use the right syntax.

###Other Commands
Further commands which are shown by `check-edge help`.

##Contact
Error reports and suggestions please via Github/Issues or PM on Telegram (@befranz)

