# blockchainGenesis

Setting up the blockchain:

1. Create a new directory for your new network and screenshot folder for screenhots of your steps.

2.Open git bash and navigate to your new directory and have puppeth in that folder and create accounts for two nodes for the network with a separate datadir for each using         following command:
  ./geth --datadir node1 account new
  ./geth --datadir node2 account new
  This should give you Public key address and Path to the secret key to the file. Save these.
	
3. Run puppeth, name your network, and select the option to configure a new genesis block and choose Proof of Authority as your consemsus algorithm.

4. Paste both account addresses from the first step one at a time into the list of accounts to seal.

5. Paste them again in the list of accounts to pre-fund.

6. Follow the prompts and choose the "Manage existing genesis", "Export genesis configurations", create chain Id  and press Enter to see your_networkname.json file.

7. Initialize each node with the new networkname.json by running following command:
    ./geth --datadir node1 init networkName.json
    ./geth --datadir node2 init networkName.json
		
8. Run the first node to unlock the account and mine with RPC port by following command and it will generate enode which we will need to run second node.
    ./geth --datadir node1 --unlock "NODE1_PUBLIC_ADDRESS_KEY" --mine --rpc --allow-insecure-unlock
		
9. Open another git bash and run second node and use first node's enode address as botnode flag.
    ./geth --datadir node2 --unlock "NODE2_PUBLIC_ADDRESS_KEY" --mine --port 30304 --bootnodes "enode://ENODE1_HERE@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
		
10. If successfully connected we should see both nodes producing blocks.

Testing  transaction on My Crypto:
1. Go to My Crypto and create a custom network by icluding chain ID and ETH as currency.

2. Import the keystore file from the node1/keystore directory into MyCrypto. 

3. Send a transaction from the node1 account to the node2 account.

4. After completion you should see message "Successful" by clicking on "TX Status".




