# homework18-blockchain

![download](https://user-images.githubusercontent.com/74984280/117550377-0089e580-b00e-11eb-9f5c-caff6d0f78ba.jpg)


Create a directory containing all the blockchain tools file (geth - puppeth)

Open the terminal and CD into that directory you just created

Create accounts for two nodes for the network with a separate datadir for each using geth.

./geth --datadir node1 account new

./geth --datadir node2 account new

Run puppeth, name your network, and select the option to configure a new genesis block.

Choose the Clique (Proof of Authority) consensus algorithm.

Paste both account addresses from the first step one at a time into the list of accounts to seal.

Paste them again in the list of accounts to pre-fund. 

Choose no for prefunding with WEI

Export genesis configurations. This will fail to create two of the files, but you only need networkname.json.

With the genesis block creation completed, we will now initialize the nodes with the genesis' json file.

Using geth, initialize each node with the new networkname.json.

./geth --datadir node1 init networkname.json

./geth --datadir node2 init networkname.json

Run the nodes in separate terminal windows with the commands:

./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock

./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
Type password and hit enter


Open MyCrypto:

Click "Add Custom Node", then add the custom network information that you set in the genesis.

Type ETH in the Currency box.

In the Chain ID box, type the chain id you generated during genesis creation.

In the URL box type: http://127.0.0.1:8545.  This points to the default RPC port on your local machine.

Finally, click Save & Use Custom Node

Select the View & Send option from the left menu panel, then click Keystore file

On the next screen, click Select Wallet File, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click Unlock.

This will open your account wallet inside MyCrypto.

In the To Address box, type the account address from Node2, then fill in an arbitrary amount of ETH:

Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.
