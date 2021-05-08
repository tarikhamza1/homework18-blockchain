# homework18-blockchain

![download](https://user-images.githubusercontent.com/74984280/117550377-0089e580-b00e-11eb-9f5c-caff6d0f78ba.jpg)

## Set up
Create a directory containing all the blockchain tools file (geth - puppeth)

Open the terminal and CD into that directory you just created

Create accounts for two nodes for the network with a separate datadir for each using geth.

./geth --datadir node1 account new

./geth --datadir node2 account new

![Screenshot](https://user-images.githubusercontent.com/74984280/117550440-6b3b2100-b00e-11eb-983c-3240ca0a50bb.png)


## Puppeth

Run puppeth, name your network, and select the option to configure a new genesis block.

Choose the Clique (Proof of Authority) consensus algorithm.

Paste both account addresses from the first step one at a time into the list of accounts to seal.

Paste them again in the list of accounts to pre-fund. 

Choose no for prefunding with WEI

Export genesis configurations. This will fail to create two of the files, but you only need networkname.json.

With the genesis block creation completed, we will now initialize the nodes with the genesis' json file.

![Screenshot1](https://user-images.githubusercontent.com/74984280/117550441-71c99880-b00e-11eb-9393-3afe29598945.png)


## Initialize Nodes

Using geth, initialize each node with the new networkname.json.

./geth --datadir node1 init networkname.json

./geth --datadir node2 init networkname.json

## Run the Nodes

Run the nodes in separate terminal windows with the commands:

./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock

./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
Type password and hit enter

![Screenshot 3 - Initiate nodes](https://user-images.githubusercontent.com/74984280/117550449-7c842d80-b00e-11eb-82c1-af1a8e1f5be0.png)


## Open MyCrypto:

Click "Add Custom Node", then add the custom network information that you set in the genesis.

Type ETH in the Currency box.

In the Chain ID box, type the chain id you generated during genesis creation.

In the URL box type: http://127.0.0.1:8545.  This points to the default RPC port on your local machine.

Finally, click Save & Use Custom Node

Select the View & Send option from the left menu panel, then click Keystore file

On the next screen, click Select Wallet File, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click Unlock.

This will open your account wallet inside MyCrypto.

![Screenshot 4](https://user-images.githubusercontent.com/74984280/117550467-90c82a80-b00e-11eb-9069-d1efbbde80be.png)
![Screenshot 5](https://user-images.githubusercontent.com/74984280/117550469-91f95780-b00e-11eb-80a7-85416c892e88.png)


In the To Address box, type the account address from Node2, then fill in an arbitrary amount of ETH:

Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.

![Screenshot 6](https://user-images.githubusercontent.com/74984280/117550462-89088600-b00e-11eb-9386-6f6e148e4988.png)

