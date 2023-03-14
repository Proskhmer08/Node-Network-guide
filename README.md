# Node-Network-guide
Script Network Lightning Node

Access Official Script Doc at: https://whitepaper.script.tv/nodes 
## Tutorial on Script Lightning Node Setup For Linux
### Lightning Node Overview
Lightning nodes help protect the security of Script blockchain as a second layer of defense against potential malicious attackers. They seal blocks and check on maclicious or non-functional Validator Nodes. Running a Script node will help secure the Script blockchain
    
Minimum token to stake is 10,000 SCPT

Minimum Hardware Requirements are:

  * Internet speed: 5mbps +/-
  * CPU: 4 cores
  * Memory: 8GB

#### Setting Up Dependencies
     sudo apt-get update
     sudo apt-get upgrade -y
     sudo apt-get install build-essential -y
     sudo apt-get install git
     sudo apt install screen
### Install Go
     wget https://go.dev/dl/go1.19.2.linux-amd64tar.gz
     sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.19.2.linux-amd64.tar.gz
    
#### Add PATH variable
#### Here you add /usr/local/go/bin to the PATH environment variable. Can also use the following: $HOME/.profile or /etc/profile
     sudo nano .profile
     export PATH=$PATH:/usr/local/go/bin
     
#### To apply changes immediately, run: 
     $HOME/.profile
     
#### Check go version that you've installed
     go version
### Build and Install (Copy line by line is best practice)
     $GOPATH/src/github.com/scripttoken/script
     sudo git clone https://github.com/scriptnetwork/Node-Network-guide.git
     $GOPATH/src/github.com/scripttoken/script
     export SCRIPT_HOME=$GOPATH/scrc/github.com/scripttoken/script
     cd $SCRIPT_HOME
    
### Build Script binaries under $GOPATH/bin
     sudo cp -r ./integration/scriptnet../scriptnet
     sudo chomd -R 777 /usr/local/go
     git config --global --add safe.directory /usr/local/go/src/github.com/scripttoken/script
     make install

### Next we open 3 screens. Can also use tmux. 
###### To detach from screen, use "Control A" then "D". To reattach to screen, use "screen -r node" or whichever screen name you used. "node" "client" or "detail"
     screen -S node
     /usr/local/go/bin/script start --config=../scriptnet/node
#### Screen 2:
     screen -S client
     /usr/local/go/bin/scriptcli daemon start --port=16889
#### Screen 3:
     screen -S detail
     /usr/local/go/bin/scriptcli query lightning
     
#### Next you will need to go to https://wallet.script.tv/ to create a new wallet. You will need 10,001 SCPT in your wallet. Once you have your Script address, you can claim token from Discord faucet

#### Next you can access your wallet using the Keystore file that should've been stored on your computer locally when setting up your wallet. You will also need the wallet password.

#### Once you have signed in, press Stake on the left hand side and then select deposit stake option. Then click on lightning stake.

#### Next, enter the node address which you have gotten from the previous command and enter 10000 SCPT

#### Last, enter wallet password to confirm transaction
     
    
