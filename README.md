# Creating Your Sandbox Blockchain


## Installs:
- Download MyCrypto
- Install GoEthereum "Geth & Tools 1.9.7" under stable releases

![Geth & Tools](/images/gethtools.png)

- Once Geth & Tools 1.9.7 is downloaded, open your downloads folder and find the filed named "geth-alltools-darwin-amd64-1.9.7-a718daa6.tar.gz"

- Decompress the file, then rename the whole folder as "sandbox-blockchain-tools" in a easy to access location from the terminal. 


## Setting up Test Blockchain PoA Network:

- Open up a text editor to copy and paste important information 

- Open up MyCrypto

- Open up 2 Terminal windows

- Open directory where you installed "sandbox-blockchain-tools" folder in one terminal window 


1. In MyCrypto, create a new wallet, and then click "generate  a wallet". You'll then be prompted to generate a Mnemonic Phrase. (make sure there are no duplicate words, if there are regenerate your phrase) Confirm your phrase, write them down and copy and paste this phrase into your text editor for future test use. 

![Mnemonic Phrase](/images/mnemonic.png)

2. In the first terminal window, change directory into "sandbox-blockchain-tools" then run the following code:
- ./geth --datadir node1 account new
- ./geth --datadir node2 account new

![Node Setup](/images/nodeaccountsetup.png)

3. Copy and paste your addresses and secret information into your text file for both nodes 1 & 2

4. Next run ./puppeth to set up your Proof of Authority network

5. Name the network "sandboxnet"

6. Then select the following (see screenshot below) for the addresses, use the 2 addresses you copied for nodes 1 & 2, use the same addresses for prefunding so you can begin your blockchain with testETH. Then export

![PoA Setup](/images/poasetup.png)
![Export](/images/finishexport.png)

7. Once step 6 is complete Cntl C to end then, initalize your nodes with the following: 



- ./geth --datadir node1 init networkname.json

- ./geth --datadir node2 init networkname.json

![Write Genesis Block](/images/genesis.png)

8. Get your nodes running with the following commands and type in your password to run:
- ./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock



- be sure to copy your enode address from node1 and input it into the "SEALER_ONE_ENODE_ADDRESS" field below when you initialize your second node. (put this in your text file as well)

![Initalize Node 1](/images/enode1.png)

- ./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock 

![Initalize Node 2](/images/initalizenode2.png)

9. You should now see your nodes running and mining like so:

![Mining](/images/mineonnode2.png)

10. Once the nodes are running and mining. Open up MyCrypto and click on change network on the bottom left, click "add custom node" then enter the following:

- Node Name "sandbox"
- Network "custom"
- Network Name "sandboxnet"
- Currency "ETH"
- Chain ID "1234"
- URL "http://127.0.0.1:8545"
- The hit Save & Use Custom Node

11. Now you should see a new network.

12. Then sign into your wallet using your Keystore file in your node1 folder>keystore until you see your address with your prefunded account. 

![Sandboxnet](/images/sandboxnet.png)

13. Now lets try sending a transaction to ourselves

![Send TX to self](/images/sendtxtoself.png)


14. Then check that the transaction was sucessful on your nodes and in MyCrypto

![MyCrypto Check](/images/checkselftx.png)

![Success](/images/checktrans.png)

![Node Check](/images/checktx.png)

15. Now let's try to send something to our alternate address

![Alt Address](/images/altaddress.png)


# Congrats, you've successfully set up your own private Blockchain! :white_large_square: :link: :white_large_square: :link: