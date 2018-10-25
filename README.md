# Bitblocks-Masternode Setup

If you just want the commands for VPS setup:
```
wget https://raw.githubusercontent.com/nashsclay/Bitblocks/master/bitblocks_mn_setup.sh
chmod +x bitblocks_mn_setup.sh  
./bitblocks_mn_setup.sh 
```

This Bitblocks-Masternode (MN) script will automatically install almost all of the MN for you. You just need to have your masternode genkey ready. This code comes from Zoldurs many many forks for MN scripts, visit his page here. https://github.com/zoldur  

Please note to run this script you MUST:  

1) Be root - better to login as root then use the sudo command  
2) Ubuntu 16.04 - I only tested this on that version but I'm sure others may work.  
3) A VPS server - You can use my referal link here --> https://www.vultr.com/?ref=7415368  
4) Digital Ocean is another provider you can use instead of Vultr. There are many more but these are very common to use. You can use any size due to the swap file that will be created if your server is below 2GB of memory.  
5) Optional - There may be other types of servers you can use but not listed here.  

Do note that this script does enable the MN to restart if it is somehow closed. It will only make it difficult to remove the MN if you decide to sell your MN. Best way is to delete all the MN files and to restart the MN. (for more information, please vist the coin's discord)  

## Setup Wallet on Local Computer

Download the newest wallet for your computer here: https://www.campuscoinproject.org/

Once downloaded run the wallet and allow it to fully sync <b>(nodes are hardcoded in the wallet)</b>
Once fully synced, encrypt your wallet. You can do this by selecting Settings --> Encrypt Wallet. Follow the prompts, also keeping your passphrase safe! This will allow you to send coins and make changes. Do NOT loose this passphrase. Once the wallet closes, give it a few minutes to finish encrypting (nothing will show) and restart the wallet.

Now that your wallet is encrypted, and synced, it's time to send your coins to your wallet. Send your coins to your wallet as you would with any other QT wallet. I personally create a generic address then create my MN address later.

Once the coins have arrived in your wallet, create a new MN address by going to Receive. Type in a label, MN1, then press Request payment. You will now have your new address for your MN.

Next go to Settings --> Options --> Wallet tab --> check Enable Coin Control features. This will allow you to easily send coins to your MN and choose ones incase you have other coins staking. Once done, restart the wallet.

Now create your MN private key. This is very important! NEVER, NEVER, did I say NEVER? show this to anyone. Never. Period. Go to Help --> Debug window --> console tab, and type in:  
`masternode genkey`

This is your MN private key. Keep this safe but close by as you will need it for the MN setup.

Now it's time to transfer your coins to your MN1 address. Go to Send. Then go to Inputs and select the coins you wish the wallet to choose from to send to your MN1 address. After you chose those coins, press ok. Go to Receive tab and double click on the MN1 below on that screen. Your address should appear. Copy this address and paste it on the Send screen and if done correctly the name of your MN should appear in the label box.

Next type in the amount of coins you wish to send to your MN (this coin should be 500000 CMPCO. NO more NO less). Once done, click Send

Once sent, please allow the transaction to FULLY confirm. You can see this by looking at the Transactions tab. Once your coins fully confirm you need to go back to the console (Help --> Debug window --> console tab) and type in:

`masternode outputs`

This will output your output of the transaction. If you do not see anything, then your coins have not fully confirmed yet or you did not send a correct amount of coins to use.

You need to copy the long hash and also the 1 or 0 at the end. Place these in the same file as your private key to find easily later. Now that is all done, we need to add the masternode to the masternode.conf file.

Now we need to update your masternode.conf file. Go to Tools --> Open Masternode Configuration File. When this loads it will be your masternode.conf file in a basic text editor (or your deafault editor.) If you get a message saying it does not know what program to use to edit this file, choose Notepad. Now edit the MN file in the exact same format as the example above except add no pound (#) symbol in front. That is used to comment the line, basically allowing the wallet not to use that line. Then add your own information to that file. Once done, go to file --> Save. Then restart the wallet.

Once reopen the wallet, go to the Masternode tab and press Update.

Eensure your MN appears, click Update if it does not appear. Now cointinue to the next section of this guide.

## To Install the CampusCoin-Masternode on VPS Server

Go through setting up the wallet and MN information on your computer. Then once that is ready to go, continue on to this guide. 

You will need a way to remote/ssh into your VPS server. I recommend using Putty. Putty can be downloaded for your system here:

https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

Pick from the top two file choices. Newer systems use 64 bit.

## Purchase Your VPS Server

I recommend using vultr. You can use my referal link if you wish. https://www.vultr.com/?ref=7415368
Make an account with them. Once that is complete, you need to purchase a server. Use these steps to purchase a server.
1) Click the blue circle button "Deploy New Server"
2) Choose the closest location.
3) Server Type - Make sure on 64 bit tab, then choose Ubuntu 16.04 x64.
4) Choose the $3.50 or $5 option. More you pay faster it will be.
NOTE: This setup DOES NOT support more than one masternode of the SAME coin on the same VPS. Not yet. But if you have other coins you need for a Masternode of a different coin, I would recommend $5 option. I would personally put no more than 3 or 4 Masternodes of different coins on the $3.50 server.
5) Choose Enable IPV6 in the Additional Features.
6) At the bottom, add Enter Server Label if you desire. Name it what you want as this will be easier to know which server is what when you buy more servers when you other coins to invest in or want a 2nd, 3rd, etc masternode of the same coin.
7) Click Deploy Server.

The initial setup takes only a few minutes, once it's complete, click on the server name and it will bring up your server information.

Now you have your server and Putty installed on the comptuer, open the Putty program. In the Host Name, type in your IP address to the server you purchased on Vultr or comparable service.

When you first connect to your server, you may get a pop up. Click Yes to allow your computer to connect. Then you need to enter your user name and password.

Username is: root
Password will be asked next. Go to your vultr page and copy the password, easiest way is to click on the page icon next to the password. When you do this, regular click on the putty screen to make it active, then right click on the putty screen to paste your password. In Linux, passwords don't appear but if you just right-click once, your password will paste. Then press Enter to log in.

Please copy and paste the following commands into you connection with your server. Most common would be to use Putty.
NOTE: Don't click on the links as that will only show you code. There is no need to do so.

```
wget https://raw.githubusercontent.com/nashsclay/CampusCoin/master/campuscoin_mn.sh 
chmod +x campuscoin_mn.sh  
./campuscoin_mn.sh 
```
You will need to copy and paste your masternode private key into putty when it asks. Then press Enter, when this is done, go back to your wallet, unlock your wallet in Settings. Once unlocked, start your masternode. Go to the Masternode tab, and try to start it, if it fails, try the command below in the NOTE. Once started go back to your VPS. type in

`cmpco-cli masternode status`

If it says, Masternode Successfully Started then congrats you are done!

NOTE: If you have trouble starting your masternode in the wallet itself (QT) run this command in the debug console.

`masternode start-missing (passphrase)`


### Other Commands and Informaiton
This information will be very useful once your MN is setup and ready.

Displays currention information about the masternode

`cmpco-cli getinfo`


You want to see status: "Masternode successfully started" and that will show your Masternode is ready to go.

`cmpco-cli masternode status`


Will stop your masternode and wil automatically restart

`cmpco-cli stop`


This will allow you to edit your masternode's wallet (not your computer's wallet). You can also you this command after the setup to fix if you input the incorrect MN key. Once open and done making changes, press Ctrl + o then Enter to save changes, then Ctrl + x to exit. Then run cmpco-cli stop to restart the MN.

`nano ~/.cmpco/cmpco.conf`


This is where your CampusCoin-Masternode program files are saved to

`cd /usr/local/bin`


Return to root home folder

`cd ~`


This will give you access to the folder of CampusCoin-Masternode files. Notice the period in front of the folder. If your are in the home folder and do **ls** command, it will not show the folder. Period means hidden. Correct command to display this folder in the home folder is **ls -al**

`cd ~/.cmpco`


You can alway DM me on discord at nashsclay#6809
