# Factomd Control Panel

### Overview <a id="overview"></a>

The Factomd Control Panel is the graphical interface for a factomd node. It presents a lot of useful information such as the state of the node, blockchain sync status, connected federated servers, etc.

It also allows you to search for transactions’ IDs, block height, factoid and entry credit addresses, or other data points similar to using the Factom Explorer. A very useful tool to have for any Factom user or developer who wants to keep an eye on what’s going on when running factomd on their local machines.

The Control Panel is accessible after running factomd via command line at the following URL: [http://localhost:8090](http://localhost:8090/).

The Control Panel has two main windows which are shown below.

**The Main Status Page**

![Control Panel 1](https://docs.factom.com/images/wallet_122.png)

**The More Detailed Node Information Page**

![Control Panel 2](https://docs.factom.com/images/wallet_123.png)

More information on the two pages and their functionality follows below.

### Main Status Page <a id="main-status-page"></a>

For most users, this page will be the primary interface to their local factomd node where they can gather at a glance all the info necessary to check its status.

**1 - Main Status Page Tab**

Use this button to switch to the Main Status Page.

**2 - More Detailed Node Information Page Tab**

Use this button to switch to the More Detailed Node Information Page.

**3 - Search Bar**

The search bar allows you to search for a block height, transaction ID, factoid and entry credit address, chain ID, entries, etc, similar to the Factom Explorer.

This way you’ll be able to search using your local copy of the Factom blockchain instead of having to use the Factom Explorer online.

**4 - Node Status and Version Number**

This section shows if your factomd node is running or not as well as the version number which is handy to find out if you have the latest software release.

**5 - Git Build Number**

This section displays the local factomd Git Build Number. A build number is an identifying number assigned to a software release. This, as well as the Version Number above, allow you to check that you are running the latest version of factomd in case there are bug fixes and updates.

**6 - Blockchain Sync Status Information**

![Control Panel 3](https://docs.factom.com/images/wallet_124.png)

Starting from the top, this section displays “Your Block Height” which is the last block synced by your local factomd node, this will update progressively as the blockchain syncs to the last available block.

The “Node Sync Status” \(1st pass\) and \(2nd pass\) display a progress bar each \(in green\) indicating the percentage of the Factom Blockchain that has currently been synced \(downloaded\) locally. It starts at 0% and ends at 100% where the latter means your node is fully synced and up to date.

There are two “passes” to double check all blocks have successfully synced. The last information displayed is the number of Factom “Federated” and “Audit” servers connected to your local factomd node.

**7 - Federated Servers Connections**

![Control Panel 4](https://docs.factom.com/images/wallet_125.png)

This section displays the number of Federated Servers currently connected to your local factomd node, together with their IP Addresses, Status \(online/offline\), time connected \(duration\), data sent and received to and from them.

It also allows you to disconnect from a specific federated server when selecting the “Disconnect” button. This is handy in case one of the servers goes offline to try and re-establish a new connection.

**8 - Transactions & Entries**

The last section at the bottom of the Main Status Page is like a built-in Factom Explorer presenting information about Factoid transactions, Chain/Entry Commits, and the last Directory Block.

All this information is collected via the local copy of the Factom blockchain, since the time your factomd node has been turned on. Once you restart factomd, new information will become available.

The “Factoids” tab shows the most recent transactions, by clicking on any of them you’ll be redirected to the actual transaction info.

![Control Panel 5](https://docs.factom.com/images/wallet_126.png)

Click on a transaction and the actual transaction is shown, in this case, it is a confirmed transaction.

![Control Panel 6](https://docs.factom.com/images/wallet_127.png)

Selecting its Transaction ID loads further info such as the transaction Inputs and Outputs, Tx ID and Hash.

![Control Panel 7](https://docs.factom.com/images/wallet_128.png)

The “Chain/Entry Commits” tab shows the latest Factom chain and entry commits. To get more info on a particular transaction, simply click on its Entry Hash.

On the far right of the page, you will also see the “EC COST” which is the amount of Entry Credits used for a specific entry.

![Control Panel 8](https://docs.factom.com/images/wallet_129.png)

The “Latest Directory Block” tab shows the last Directory Block generated by the Factom blockchain. When selecting the KeyMR URL \(in blue\) further info for the particular block will be displayed.

![Control Panel 9](https://docs.factom.com/images/wallet_130.png)

### More Detailed Node Information Page <a id="more-detailed-node-information-page"></a>

The More Detailed Node Information page displays details about the local factomd node such as a summary, the process list, the print map, connections, as well as info about the Federated and Audit Servers currently connected to your local node.

Everything in this section is used by developers for debugging purposes. Any user looking at these pages isn’t expected to be able to read it, for most end users the “Main Status” page is all they will ever need to know.

A brief description of each of the tabs is below.

**Summary**

The “Summary” tab shows critical information describing the internal status of your node. For example “79879\[0falad\]” shows the number of directory blocks which have been saved to the database. They are only saved once they get past the first minute of the next block.

The three numbers separated by slashes 79877/79880/79881 describe the process lists. The three numbers bracket the different heights of process lists. The first number shows the lowest process list height that has been retained. The second number shows the process list height that is currently being built. The third number is the next height that the leaders will be building as well as the max process list which has been allocated. The “-/8” line shows which minute the leaders are on, minutes range from 0 to 9.

The following column is a series of counters for the different types of messages the local nodes or federated servers are handling. For example…

* Review: messages waiting to be reviewed
* Holding: any message that needs to be processed
* Acks: messages from Federated Servers
* MsgQueue: all messages that are in the queue
* InMsgQueue: if valid these messages go into “holding”
* APIQueue: API calls messages queue
* AckQueue: Federated Servers messages queue
* TimerMsgQueue: timer message queue
* NetworkOutMsgQueue: outgoing network messages queue
* NetworkInvalidMsgQueue: invalid network messages queue

![Control Panel 10](https://docs.factom.com/images/wallet_131.png)

**Process List**

The “Process List” is a list and ordering of messages which will go into the next block. The process list shows all the messages your local node is aware of that will be used to create a block. They are grouped by the different VMs \(Virtual Machines\), which map to the different servers.

The leftmost column is the item number in that specific VM’s process list for that block. The P indicates that the local node has processed that item in the list. When processed, it is valid per the local rules and updates the local state. Examples of this would be EC and FCT balances. It also changes the status of the TxID to TransactionACK.

The 3rd column with \[888888f0\] is the server identity which acknowledged the transaction.

The 4th column is the type of transaction: it can be REntry \(Reveal Entry\), CEntry \(Commit Entry\), DBSig \(Database Signature\) and EOM \(End of Minute\). The EOM tells the other servers that there will be no more messages from that server, and the next server can take over.

The “DBHt: 79880” is the block height followed by the message itself, for example:

_– Leader\[888888f053\] Entry\[f23149\] ChainID\[b4f80cf2d3\]_.

![Control Panel 11](https://docs.factom.com/images/wallet_132.png)

**Print Map**

The “PrintMap” tab shows which of the VMs are responsible for the different segments of the network for each minute over the 10-minute period. The columns show the different VMs. Different servers are responsible for different VMs during different 10-minute sessions. The rows are the different minutes in a single 10-minute segment.

![Control Panel 12](https://docs.factom.com/images/wallet_133.png)

**Servers/Authorities**

The “Servers/Authorities” tab displays information about all Federated and Audit servers visible to the local factomd node. A server identity is an identifier which is self-bootstrapped and required to be an audit or federated server. An identity is created with this program: [https://github.com/FactomProject/serveridentity](https://github.com/FactomProject/serveridentity) to this specification: [https://github.com/FactomProject/FactomDocs/blob/master/Identity.md](https://github.com/FactomProject/FactomDocs/blob/master/Identity.md).

Each server has their own identity, however, if the same identity is on the network at the same time due to an accident, one or both of the servers will panic. The identity is a more generic construct. It has four different levels of public/private keys, which can be used to replace lower level keys such as a Signing Key \(to sign transactions\) or an Anchor Key \(to anchor Merkle Roots of Factom chains in the Bitcoin blockchain\).

The “Management Chain” also known as Server Management Chain is more specific to the Federated and Audit servers and contains a key to sign the directory blocks and process list messages.

The “Matryoshka” is currently unused, but it will provide a form of deterministic randomness in future contention resolving systems.

![Control Panel 13](https://docs.factom.com/images/wallet_134.png)

**Servers/Identities**

The “Servers/Identities” tab displays information about all Federated and Audit servers as well as the “Skeleton Identity” used to add and remove servers from the network in Milestone 2 \(M2\). Normally servers fail over between Federated and Audit servers automatically, but adding and subtracting servers is done with the Skeleton Identity.

![Control Panel 14](https://docs.factom.com/images/wallet_135.png)

**Servers/My Node**

The “My Node” tab displays the local factomd node name \(FNode0\), its Identity ChainID and Signing Key.

![Control Panel 15](https://docs.factom.com/images/wallet_136.png)

**Connections/Raw**

The “Connections/Raw” tab displays all the servers and nodes that are connected to the local factomd node with their status and IP Address.

![Control Panel 16](https://docs.factom.com/images/wallet_137.png)

**Connections/Other**

The “Connections/Other” tab displays all the servers and nodes that are connected to the local factomd node with their status and Identity Hash.

![Control Panel 17](https://docs.factom.com/images/wallet_138.png)

The Control Panel is a great tool to visualize, search and gather data about the Factom Network, its Federated and Audit Servers as well as the local factomd node. It is of great help for both end users to quickly check the status of their nodes as well as for developers looking for more in-depth information to allow them to troubleshoot issues.
