### Time filter inneficiency

Checking the [api docs](https://docs.etherscan.io/api-endpoints/accounts#get-a-list-of-normal-transactions-by-address) showed that our account request in `getEtherScanTxListForAddress` has a timestamp paramater available. 
So we can grab that value from our request instead of having to first grab the block from the `nodeProvider` -> compute time from the block timeStamp. 
This also allows us to filter our transactions by time earlier, which will reduce the number of txs we promise map through later, less times to getTransaction from the nodeProvider `await nodeProvider.getTransaction(etherscanTx.hash);`