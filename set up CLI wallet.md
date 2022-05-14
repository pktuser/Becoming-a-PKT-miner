###### NOTES FOR SHARING ######
Wallet install and setup for Linux (Debian/Ubuntu)
1. download installer, paste into terminal:
`wget https://github.com/pkt-cash/pktd/releases/download/pktd-v1.5.1/pktd-v1.5.1-linux.deb`

2. install deb package, paste into terminal:
`dpkg pktd-v1.5.1-linux.deb`

After `deb` install:

1. Create or recover wallet to current machine, paste into terminal:
`/bin/pktwallet --create --wallet NAME_YOUR_WALLET`

(if you don't want multiple wallets you can paste or type only: `/bin/pktwallet --create`

  a. when prompted to enter passphrase, paste:
`PASS PHRASE FROM WALLET TO BE RESTORED OR NEW PASS FOR NEW WALLET`
  
  b. when prompted to enter seedphrase, paste: 
`YOUR SEED PHRASE FROM PREVIOUS WALLET OR NEW SEED PHRASE TO CREATE NEW WALLET`
  
  c. Once this is done, run pktwallet in a new terminal window. Paste into terminal:
`/bin/pktwallet --wallet YOUR_WALLET_NAME`

(if you only have a single unnamed wallet, paste or type only: `/bin/pktwallet`

  d. allow this to run in the background. It should say "wallet opened" - once it does, just wait. The next steps can take some time without any updates.

2. Open another terminal window. check associated addresses with the opened wallet, paste into terminal:
`/bin/pktctl --wallet getaddressbalances 1 1`

  a. this should return all addresses associated with wallet.
  
  b. if the wallet you're restoring has multiple addresses, or you want to associate a new address with this wallet, paste into terminal:
`/bin/pktctl --wallet getnewaddress`
  
  - then check balances again to see if the addresses were pulled in, paste this into terminal:
`/bin/pktctl --wallet getaddressbalances 1 1`
  
  - repeat this procedure until all addressses are present
  
  - don't worry if you create extra addresses, they don't hurt anything. They are generated deterministically and will always generate in the same order.

3. Only after all addresses show up should you resync the wallet. Paste this into terminal:
`/bin/pktctl --wallet resync`

  a. This will take about 12 hours to complete
  
  b. You will know it's complete when the updates slow down on the screen to one new line every 30-90 seconds instead of multiple per second.
