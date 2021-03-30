# Instructions:

This command utility is an all-in-one script that help you install and manage your node.
# >>>>> IMPORTANT: This is __NOT__ compatible with Docker Images!!! If you've installed your node with a Docker Image, this script can break your installation. <<<<< #
### 1. Requirements: ###
You need a VPS with the following minimum requirements:
- 4G RAM
- Quad Core
- Linux Operating system (Ubuntu, CentOS)

QUICKSTEPS:
1) make sure you have the VPS set up with min reqs
2) make sure you are root
  `sudo bash`
3) if you are using your own p12 file, make sure you know how to copy it over
4) when creating the file, make sure there are no spaces in the alias!!! (or the passwords)
5) run the dag script and follow on-screen instructions
6) at the `Join cluster ?` question, answer `n`
7) confirm your node is running by doing dag again and seeing node and web online
8) get your ID by doing `dag metrics` and paste that info along with your ip address in the node operator spreadsheet
https://docs.google.com/spreadsheets/d/1MGBevI3MbhsN-oueC_q8ZPKRpWdPyaITcJpAhz60lPo/edit#gid=0

9) wait for the next release to be announced. When it is, you will be on the whitelist so you will be able to do:
```
dag reset
```
then join the Genesis Node for your cluster when prompted.

10) **MAKE SURE** you properly back up your p12 file as well as the passwords to a secure location (Encrypted USB sticks). If you lose this, you're done. No more coins.


Also, if you have a p12 file you would like to use from a molly wallet, please make sure you copy it to the VPS prior to running the setup script. If you do not have one, the script will generate a p12 file for you.

***  WARNING *** It is assumed that the user you are running this with has root access and can write to /usr/local/bin as well as change file permissions.


### 2. Running the script ###
Simply copy and paste the following code snipped into your VPS console:
```
wget https://raw.githubusercontent.com/StardustCollective/validator-node-install/master/dag -O /usr/local/bin/dag && chmod +x /usr/local/bin/dag && dag
```
___

And follow the instructions on the screen!

## 3. If you are on testnet ##
just add `--testnet` after either your `dag reset` or `dag nodes` commands. 
i.e.:
```dag reset --testnet```
or
```dag join 13.23.145.23 --testnet```

___
# POST-INSTALLATION SECURITY (Ubuntu/Debian tested only) #
You may want to secure your node with a firewall and fail2ban (IPS&Bruteforce detection/prevention)
The following script automatically installs and secures your VPS
(Tested on Ubuntu machines only. Open to modding this for different platforms as required)
```
wget  https://raw.githubusercontent.com/StardustCollective/validator-node-install/master/config-security -O ~/config-security && chmod +x ~/config-security && ~/config-security
```

You will also need to manually set up an ufw firewall rule for port 9002 (in order to view your node in the browser)

```sudo ufw allow proto tcp from XXX.XXX.XX.XXX to any port 9002```

Replace the `XXX.XXX.XX.XXX` with your home internet/wifi IP address.

___
# For debugging ONLY #
This will overwrite the default logback.xml so that the org.constellation logging level is set to `debug` instead of `warn`.
```
wget https://raw.githubusercontent.com/StardustCollective/validator-node-install/master/logback.xml -O ~/constellation/logback.xml
```
# TESTNET INSTRUCTIONS: #
# >>>>> IMPORTANT: This is __NOT__ compatible with Docker Images!!! If you've installed your node with a Docker Image, this script can break your installation. <<<<< #
QUICKSTEPS:
- make sure you have the VPS set up with min reqs
- make sure you are root
  `sudo bash`
- make sure you read EVERYTHING properly. It's easy to make mistakes when you rush through things.

1. follow the instructions at the top and once you have the dag utility, just perform the same commands as described but add `--testnet` where required.

```dag reset --testnet```
or
```dag join 13.23.145.23 --testnet```

# UTILITIES #
checkCluster
```
wget https://raw.githubusercontent.com/StardustCollective/validator-node-install/master/checkCluster -O /usr/local/bin/checkCluster && chmod +x /usr/local/bin/checkCluster
```
usage: checkCluster [ip_address]
