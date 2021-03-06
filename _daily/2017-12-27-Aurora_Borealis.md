---
layout: post
unique_id: aurora_borealis
title: Aurora Borealis
categories: []
locations: 
---

YESTERDAY:
* KFC for lunch
  * prices were crazy!
* visited three museums
  * two of them were closed due to Christmas
  * Morris Thompson Cultural and Visitors Center is lovely and informative
* found a friendly guy carving amazing life-sized ice sculptures
* Chinese hot pot for dinner
  * excellent probably only because it was -12 degrees outside
* various water in cold temperature experiments
  * throwing boiling hot water into sub-zero air
  * supercooled water + vibration = ice formation
    * basically leave a partial bottle of distilled water in a car in freezing temperature overnight
    * give it a thwack and it'll crystallize
* saw the northern lights
  * trip goal achieved!

TODAY:
* Chenna Hot Springs!
  * we all forgot swimsuits and neither fred meyers nor walmart had them in stock
  * ended up borrowing used, laundered ones :P
  * 110 degree water + -10 degree air + lots of steam
  * easy to make interesting frozen hair styles
* ice sculpture museum
* short, cold hike
* udon + sushi for dinner

LEARNINGS:
* "chicken breast" insult in Chinese
  * white chicken meat is undesirable since dark meat is juicier and more tender
  * however, it's wasteful to just throw it out
  * hence, calling somebody "chicken breast" means they are undesirable but barely above the bar for being thrown out as waste
* Yaokai's explanation of how bitcoin works
  * block
    * the secret generated by a miner is used to encode transactions into a block
    * limited 1 mb block of transactions per 10 minute fixed intervals
  * chain
    * entire transaction history is couple gb now
    * entire transaction history is replicated on every bitcoin client
    * currently takes ~8 hours to bootstrap a new client
  * auction process
    * miner gets to choose which transactions get into the block
    * each transaction offers a fee (in bitcoin) which is given to the miner
    * so the miner usually picks the transactions with the highest fees to be recorded
  * anonymization
    * bitcoin accounts can be de-anonymized only through the exchanges which trade external currencies into bitcoin
    * bitcoin accounts that only transact within the block chain are anonymous
      * if USD came from bank account A and went to bitcoin account B to bitcoin account C to bitcoin account D to bank account E
      * we know A and B are probably the same person and D and E are the same
      * we don't know if C is actually the same as A or E, or maybe a completely different 3rd party
  * volatility
    * fixed 1 mb per 10 minutes was intended for "rare" transactions
    * current volatility means one can starve others out of transactions
    * segwit attempts to minimize the size of the transaction record in the block through space efficiency optimization
      * this only increases the number of transactions to be recorded by 4x though ...
