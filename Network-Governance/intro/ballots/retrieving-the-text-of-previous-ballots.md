# Retrieving the text of previous ballots

**How do I retrieve the text of previous ballots?**

At [https://voting.swarmnetwork.org](https://voting.swarmnetwork.org/?enableDumpMasternodeDetails=true) you will find the [{ballot-address}](https://archive.secure.vote/0x%7BTXID%7D.json) smart contract for each ballot when clicking the “i" icon of each ballot.

![Click the &quot;i&quot; icon on a ballot to see the smart contract address](../../.gitbook/assets/image%20%281%29.png)

![Address of the ballot smart contract ](../../.gitbook/assets/image%20%285%29.png)

Go to the "Events” tab in etherscan with [https://etherscan.io/address/](https://etherscan.io/address/%7Baddress%7D#events)[{ballot-address}](https://archive.secure.vote/0x%7BTXID%7D.json)\#events , then scroll down to the earliest transaction of the contract. Click the Txn Hash to see more details about the transaction.

![](../../.gitbook/assets/image%20%283%29.png)

The first event has details about the ballot instantiation. _Click to see More_. One of the data \(typically the last one\) will be the only one to have a 32 bytes [{TXID}](https://archive.secure.vote/0x%7BTXID%7D.json). It should be labelled _specHash_.  


![](../../.gitbook/assets/image%20%286%29.png)

Copy the hash and then go to [https://archive.secure.vote/0x{TXID}.json](https://archive.secure.vote/0x%7BTXID%7D.json)  
That will get you the “BallotSpec”, which you can download and open it with a text editor to see the details

