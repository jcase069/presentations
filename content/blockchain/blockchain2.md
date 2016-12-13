## Blockchain for Healthcare

### Dan Hedges

Note: 1



## Hype

![Economist](/content/blockchain/images/EconomistScreenShot.png)
<!-- .element class="fragment" width="30%" -->
![ulaHealth Summit](/content/blockchain/images/ulahealth.jpeg)
<!-- .element class="fragment" width="30%" -->
![ONC Logo](/content/blockchain/images/logo-dept-hhs.jpg)
<!-- .element class="fragment" width="30%" -->

Note:
So what is blockchain doing in healthcare?

In a word, hype.  There is a great deal of hype.  The Economist did a cover
story on Blockchain applications, and featured healthcare as a major target
for disruption.  There have been multiple summits specifically for healthcare
blockchain apps, including one here in Austin.  Google "blockchain healthcare"
and you get over 600K results.  The ONC -- the Department of Health and Human
Services' Office of the National Coordinator for Health Information Technology --
issued a whitepaper challenge on blockchain in healthcare and got 70 submissions,
including the 15 winners which have now been published on their site.

There is a healthcare revolution brewing that will happen over the next
decade or so.

So, what is it?



## What is Bitcoin?


### Bitcoin

<h3>
<span class="fragment">Distributed</span>
<span class="fragment">Crypto</span>
<span class="fragment">Currency</span>
</h3>

Note:
Bitcoin is a distributed crypto currency.  "Currency" because it can be
used as money.  But money only works if people trust it.  "Crypto" because its
legitimacy can be derived from the rules of cryptography.  And "Distributed"
because there is no centralized authority -- no central bank or central
database.


### Bitcoin Network

![Node Network](/content/blockchain/images/NodeNetwork.svg)

Note:
The revolutionary idea of Bitcoin is how it can achieve a digital currency on
a completely distributed network of nodes.  Anyone can create a node on the
network -- they are all running open-source software.  And at first, that
doesn't seem safe.  After all, could I take the software and re-write it so
that all the bitcoin are transferred into my account?  Well, you can try but
you're going to fail.

The implementation of bitcoin is completely distributed.  At any moment, you
could have thousands of nodes on the network.  As of late 2016, there are
roughly 5000 listening nodes.  If a natural disaster took out most of the nodes,
the network would survive just fine.  There might be a hiccup, but there would
be no major disruption in service.  So the network, the storage, and the
computation work are all completely distributed.

(Image created in draw.io)


### Centralized Ledger

![Accounting Ledger](/content/blockchain/images/Ledger.jpg)

Note:
All of the nodes on the network have a copy of all of the bitcoin transactions
covering the entire history of the currency.  As of November 2016, the size of
all transactions unindexed is approaching 90 gigabytes.  When new transactions
are proposed, all the nodes in the network can judge their validity, and as a
group the network will achieve consensus on which new transactions will be added
to the ledger.  It is this consensus mechanism that creates a conceptually
centralized ledger.

So when people say that Bitcoin is distributed, yes, the network is distributed.
But the genius is that the distributed network can create a conceptually
centralized ledger.

(Image from flickr user Edinburgh City of Print:
https://www.flickr.com/photos/30239838@N04/4268190563)



## Cryptography Part 1


### Hashing

#### (Document) => (Number)

Note:
I said before that Bitcoin depends on Cryptography to prove its safety.  What,
precisely does it need?

- Hashing is a fast (constant-time) algorithm to compute a digital document of
any length into a number.  Any change to the document, no matter how small, must
cause the new output to be markedly different, to the point that no one can
successively approach a target value by subtly adjusting the document.  This
is necessary for proof-of-work above, and also for chaining together the
blockchain.



## What is a Blockchain?

Note:
So, what is a blockchain?  

The Bitcoin ledger I hinted at before contains every bitcoin transaction in
history.  Every node on the blockchain has a copy of the ledger, and the
ledger is kept in a data structure called the Blockchain.


### A Blockchain is Like This

![Simplified Blockchain](/content/blockchain/images/Blockchain_simple.png)

But this can still be hacked!
<!-- .element class="fragment" -->

Note:
This is not what a real blockchain looks like, but imagine the following
data structure.  Every block contains new transactions, and at the end, it
has the cryptographic hash of the previous block.  Now, assume someone wants
to change a transaction that happened in the past.  By changing any bits in
the transaction, you change the cryptographic hash of the entire block, so
now the next block's previous hash value is incorrect.  Any node in the
network can see that this blockchain has been tampered with.  Anyone who wants
to rewrite history would need to rewrite all the hashes of all the subsequent
blocks.

Well, that sounds doable.  How can we make it intractable to do that?


### Proof of Work

This is closer to what an actual blockchain looks like.

![Blockchain Structure](/content/blockchain/images/BlockchainStructure.png)

- Every block must have a hash less than a target value.
<!-- .element class="fragment" -->
- If it does not, pick a new nonce and try again.
<!-- .element class="fragment" -->

Note:
What if every block on the chain took a lot of work?  If we could ensure that
every block on the chain required hours or weeks or months of intense
computation work, we can make it intractable to rewrite the thousands of blocks
it would take to rewrite history.  And while the malicious actor is trying to
rewrite history, more blocks are being generated, making it even harder as time
goes on.  This mechanism is called "Proof of Work".


### Compensating Proof of Work

- Each node competes to add a new block to the ledger<!-- .element class="fragment" -->
- A node needs to be the first to find a valid block<!-- .element class="fragment" -->
- A node earns a reward for adding each block<!-- .element class="fragment" -->
    - 12 Btc (2016)<!-- .element class="fragment" -->
    - Reward halves from time to time<!-- .element class="fragment" -->


### Blockchain

The centralized ledger of transactions, copied to every node in the Bitcoin
network.

![Bitcoin Logo](/content/blockchain/images/bitcoin.jpg)
<!-- .element  class="fragment" height="35%" -->

![Blockchain Imagined](/content/blockchain/images/blockchain.svg.png)
<!-- .element  class="fragment" height="35%" style="background-color: #FFFFFF"-->

Note: When you hear blockchain, you should think of Bitcoin: the world's first
successful distributed cryptocurrency.  Bitcoin was invented in 2009 by an
unknown person under the pseudonym Satoshi Nakamoto, and one of the innovations
it created was the blockchain.  The term "blockchain" can be used to describe
the Bitcoin implementation, or the  technology.


## Blockchain Applications

Note:
So now that Bitcoin is out, can we do anything with the technology other than
a nerd cryptocurrency?  Well, we can.  We can do a lot.


### Blockchain Application Evolution
<div style="float:right; width: 25%">
![Blockchain book cover](/content/blockchain/images/BlockchainBookCover.png)
</div>
<div style="width: 70%">
    <ul>
        <li class="fragment">
            Blockchain 1.0: Currency
            <ul>
                <li class="fragment">
                    Bitcoin
                </li>
            </ul>
        </li>
        <li class="fragment">Blockchain 2.0: Contracts</li>
        <ul class="fragment">
            <li>Mortgages, Titles, Smart Property, Smart Contracts</li>
        </ul>
        <li class="fragment">Blockchain 3.0: Applications</li>
        <ul class="fragment">
            <li>Government, Culture, Art, Healthcare</li>
        </ul>
    </ul>
</div>

Note:

Source: Blockchain: Blueprint for a New Economy, by Melanie Swan, O'Reilly 2015



## Blockchain 1.0

### Currency


## Terms

- Digital currency -- think of a Starbucks gift card, or rewards card
<!-- .element  class="fragment" height="35%" -->
- Cryptocurrency -- a digital currency that relies on cryptography
<!-- .element  class="fragment" height="35%" -->
- Distributed Cryptocurrency -- Bitcoin was the first
<!-- .element  class="fragment" height="35%" -->


## Blockchain 2.0

### Contracts


## Property

![Mariana Catalina Izaguirre](/content/blockchain/images/Catalina_Villanueva_Alcaldia.jpg "Mariana Catalina Izaguirre. // Photo: Revistazo")

Mariana Catalina Izaguirre. Photo: Revistazo

Source: [*The Economist*](http://www.economist.com/news/briefing/21677228-technology-behind-bitcoin-lets-people-who-do-not-know-or-trust-each-other-build-dependable)

Note:
This is Mariana Catalina Izaguirre.  In 2009, the police came to evict her from
the house she was living in, at the request of the registered owner, who would
tear it down and rebuild.  Trouble was, Izaguirre, who had lived there for
thirty years, actually owned the land.  She had the deed to prove it.  The
Property Institute held fraudulent documentation filed by a criminal "owner".
Fortunately, Izaguirre had documentation -- an official title and deed to the
land -- so thankfully it was all straigtened out.  But only after she was
forcibly evicted while her children were at school, and her house was
demolished.

This story happened in Honduras, and it is not uncommon in developing countries.
In the U.S., we sometimes take for granted that our government doesn't
routinely give in to corruption and bribes.

So, what can the Blockchain do for Mariana?


## Public Records
