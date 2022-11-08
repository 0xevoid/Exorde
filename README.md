<p style="font-size:14px" align="right">
<a href="https://m.do.co/c/2cea00d4f9bble" target="_blank">Deploy your VPS using our referral link to get 100$ free bonus for 60 days <img src="https://user-images.githubusercontent.com/50621007/183284313-adf81164-6db4-4284-9ea0-bcb841936350.png" width="30"/></a>/
</p>
<p align="center">
<p style="font-size:85px" align="center"> Exorde Participation Module CLI v1.3.1 
<p align="center">
  <img height="50" height="auto" src="https://user-images.githubusercontent.com/112532410/200643438-8cea10cd-2c5e-40f6-8def-b30e5bd47e9f.jpeg">
</p>

# Exorde Participation Module CLI v1.3.1

[ This is a work in progress ](https://github.com/exorde-labs/ExordeModuleCLI/)

## Instructions
You have two choices to run the Exorde CLI : 
- create a **Conda** virtual environment: [conda guide](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)
- use **Docker** to build and run a container: [docker guide](https://docs.docker.com/engine/install/ubuntu)

## Hardware requirements

| Component | Minimum Requirements |
|----------|---------------------|
|CPU|Intel Core i3 or i5|
|RAMS|4 GB DDR4 RAM|
|Storage|500 GB HDD|

| Component | Recommended specifications |
|----------|---------------------|
|CPU|Intel Core i7-8700 Hexa-Core|
|RAM|64 GB DDR4 RAM|
|Storage|2 x 1 TB NVMe SSD|

## Software requirements

| Component | Minimum Requirements |
|----------|---------------------|
|Operating system|Ubuntu 16.04|

| Component | Recommended specifications |
|----------|---------------------|
|Operating system|Ubuntu 18.04 or higher|

# - BECAUSE I USED DOCKER TO RUN IT ME!! 
```
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    screen \
    git
```
### - Add official Docker GPG key
```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
### - Repository settings
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
### - Docker install
First you need to have Docker installed on your machine.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
- Check you have docker correctly installed by typing on your terminal: 
```
docker --version
```
If it's the case you'll have something like that in output:  
`Docker version 20.10.20, build 9fdeb9c`

### - Download Exorde pack
```
git clone https://github.com/exorde-labs/ExordeModuleCLI.git
```
### - Go to Exorde folder
```
cd ExordeModuleCLI
```
### - BUILD Docker
```
docker build -t exorde-cli . 
```
### - Run Validator
- Open a new screen using `screen`
```
screen -Rd exorde
```
- Then run the command below

```
docker run -it exorde-cli -m YOUR_ETH_WALLET_ADDRESS -l LEVEL_LOGGING
```
**exanple**
```
docker run -it exorde-cli -m 0x0898xxxxx -l 4
```
For logging can be filled in 0, 1, 2, 3, 4 logging details I will explain
| Logging levels | Description |
|---------------|------------|
|0|No logs|
|1|Regular log|
|2|Validation log|
|3|Log validation and scrapping|
|4|Validation logs (details) + scrapping logs (for troubleshooting)|

> I recommend using Logging level 4 to make it easier to troubleshoot if there are problems

**NOTE:**
-If you want to exit the terminal press `CTRL + A + D`
-If you want to enter the terminal use the command 
```
screen -r exorde
```
### Logging 
**Level of logging wanted in console output.** 

> -l,  --logging LOGGING

Possible values: 
- 0 = no logs, 
- 1 = general logs
- 2 = validation logs
- 3 = validation + scraping logs
- 4 = detailed validation + scraping logs (e.g. for troubleshooting)

*Correct usage examples:*

    -l 2
or
    
    --logging=2

### Help 
**Help command to see all arguments.** 

> -h,  --help

*Correct usage examples:*

    -h
or
    
    --help

## When running

For example, if you run in conda mode with -l 2 (moderate amount of logs), you should see this in the console:

> (my_env) \...\user\ExordeModuleCLI>python Launcher.py -m 0x0000000000000000000000000000000000000001 -l 2 
> 
> Selected logging > Level:  2 .  (0 = no logs, 1 = general logs, 2 = validation logs, 3 =
> validation + scraping logs, 4 = detailed validation + scraping logs
> 
> [INITIAL MODULE SETUP] Downloading code modules on decentralized
> storage...
>         Code Sub-Module  1  /  4        Downloading...   https://bafybeibuxrjwffjeymrjlkd2r35r5rdlzxuavoeympqgr7xrxor6hp3bh4.ipfs.w3s.link/Transaction.py
>         Code Sub-Module  2  /  4        Downloading...   https://bafybeifqnq76utn767m4qbwd4j2jg6k3ypwcr2do7gkk3b26ooxfmzgc5e.ipfs.w3s.link/Scraper.py
>         Code Sub-Module  3  /  4        Downloading...   https://bafybeibbygfm276hjion7ocaoyp3wlfodszhlba6jy3b3fzd37zawkfbgi.ipfs.w3s.link/Validator.py
>         Code Sub-Module  4  /  4        Downloading...   https://bafybeicdgmxvetbi4yqjztzzroevcfvnwobk6zomsz5nh4lvb3dftyimxa.ipfs.w3s.link/App.py
> 
> [Init] UPDATING CONFIG [Init] READING CONFIG FILE [Init] Current Config :  {'ExordeApp': {'ERCAddress': '', 'MainERCAddress': '',  'Updated': 0, 'SendCountryInfo': 1, 'lastInfo': 'Hello, you are now an
> Exorder!', 'lastUpdate': '1.3.1'}}
> 
>  [Init] FIRST WORKER LAUNCH
>  
>  [Init] New Worker Local Address =  0x4A94c5D4C49597cd889eB569D0Bf4d6e2aC3aE29

> [Init] First funding of the worker wallet [Initial Auto Faucet] Top up

> sFuel & some EXDT to worker address... 

> [Faucet] selecting Auto-Faucet ...

The module is autonomous.

## Spontaneous updates

Sometimes, Exorde Labs needs to push some update in the code. The module will detect it, and kill itself.
This is important for the Exorde Network to remain hommogenous, so older versions have to be killed right away.

When this happens, the module will print a message & shut down.
