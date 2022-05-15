###### NOTES FOR SHARING ######

### INSTALL

Wallet install and setup for Linux (Debian/Ubuntu)
1. download installer, paste into terminal:
`wget https://github.com/pkt-cash/pktd/releases/download/pktd-v1.5.1/pktd-v1.5.1-linux.deb`

2. install deb package, paste into terminal:
`dpkg pktd-v1.5.1-linux.deb`

You are now done installing, next step is to create a database for your wallet on your local machine.

### CREATE WALLET

1. Create or recover wallet to current machine, paste into terminal:
`/bin/pktwallet --create --wallet NAME_YOUR_WALLET`

(if you don't want multiple wallets you can paste or type only: `/bin/pktwallet --create`

  a. when prompted to enter passphrase, paste:
`PASS PHRASE FROM WALLET TO BE RESTORED OR NEW PASS FOR NEW WALLET`
  
  b. when prompted to enter seedphrase, paste: 
`YOUR SEED PHRASE FROM PREVIOUS WALLET OR NEW SEED PHRASE TO CREATE NEW WALLET`

You have now created your local wallet database. Now the database needs to be updated to match the blockchain.

### RUN WALLET AND PERFORM ACTIONS ON IT

1. Run pktwallet in a new terminal window. Paste into terminal:
`/bin/pktwallet --wallet YOUR_WALLET_NAME`

(if you only have a single unnamed wallet, paste or type only: `/bin/pktwallet`

  a. allow this to run in the background. It should say "wallet opened" - once it does, just wait. The next steps can take some time without any updates.

2. Open another terminal window. Now we will check addresses associated with the opened wallet, paste into terminal:
`/bin/pktctl --wallet getaddressbalances 1 1`

  a. this should return all addresses associated with wallet, even addresses with 0 PKT.
  
  b. if the wallet you're restoring has multiple addresses, or you want to associate a new address with this wallet, paste into terminal:
`/bin/pktctl --wallet getnewaddress`
  
  c. Now check balances again to see if the addresses were pulled in, paste this into terminal:
`/bin/pktctl --wallet getaddressbalances 1 1`
  
  - repeat this procedure until all addressses are present
  
  - don't worry if you create extra addresses, they don't hurt anything. They are generated deterministically and will always generate in the same order.

##### IF THIS IS THE FIRST TIME YOU'VE SET UP THIS WALLET ON YOUR MACHINE, YOU WILL HAVE TO RUN RESYNC TO PULL ALL THE DATA OFF THE BLOCKCHAIN

3. Only after all addresses show up should you resync the wallet. Only resync on new wallet creation or recovery unless you like wasting time. Paste this into terminal:
`/bin/pktctl --wallet resync`

  a. This will take about 12-16 hours to complete
  
  b. You will know it's complete when the updates slow down on the screen to one new line every 30-90 seconds instead of multiple per second.

### PERFORM ACTIONS ON WALLET

1. Pktwallet must be running in the background or in a separate terminal window. All commands are run via pktctl.
  A. Useful commands:
    1) show all balances: `/bin/pktctl --wallet getaddressbalances 1 1`
    2) unlock wallet (#TIMEOUT - number of seconds before wallet automatically locks): `/bin/pktctl --wallet walletpassphrase YOUR_PASS_PHRASE #TIMEOUT`
    3) lock wallet: `/bin/pktctl --wallet walletlock`
    4) get wallet seed: `/bin/pktctl --wallet getwalletseed`
    5) show installed version: `/bin/pktctl -V`
    6) get wallet info: `/bin/pktctl --wallet getinfo`

2. If you mine and need to fold your coins, I highly suggest running my script `https://github.com/pktuser/fold`
  
### OTHER COMMANDS ###

uninstall: `sudo dpkg --remove pkgname` pkgname could be eg `pktd-v1.5.1-linux.deb`
(useful when needing to update to latest version)
