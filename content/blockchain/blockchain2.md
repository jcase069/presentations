## Blockchain for Healthcare

### Dan Hedges

### (Prologue)
<!-- .element class="fragment" -->

Note:
It's a beautiful day as I walk into Bank of America.  I say, "I would like to
open an account".

The gentleman behind the desk says, "That's great.  We have many great options
to choose from.  We have competitive interest rates; they're measured in
microns."

I say, "Do you have designer checks with images from the Empire Strikes Back?"

He says, "Why, yes, yes we do!  And we have a website available 24/7 so you can
get your balance and view your transactions."

I say, "About that: I have a better idea -- you guys process the checks and all
the transactions, but I have a website available 24/7 that *you* can access to
check *my* balance.  Then, when a new transaction comes in, you access my
RESTful API to see if I have the funds to cover it, and if I do, you register
the new transaction, also with my API."

He thinks it over, and says, "Well, we would have a few issues with that.  First
of all, what would stop you from just always programming your balance to return
a million billion dollars?"

I say: "I still don't see a problem."

"It just wouldn't be fair and equitable."

"Fair?  Equitable?" I say.  "Have you seen the fees you charge?  Like this one:
it's called 'Overdraft Fee', and it says you can charge me $35 for the crime of
not having much money.  How about you?  If you don't have enough money, can I
charge you a fee?  Because it says here that if a bank is big enough and doesn't
have enough money, that you can charge the federal government.  Essentially,
you're charging me again.  Does that seem fair and equitable to you?"

My question might have been a bit too philosophical for Guy Working Behind the
Desk at a Bank.  So I leave the bank without my new account or Empire Strikes
Back checks, yet with a renewed sense of optimism.  I will find a bank willing to
compromise in order to open new accounts.

I'm going to try Wells Fargo next.



## Blockchain for Healthcare

- Blockchain
- Bitcoin
- Cryptography
- Decentralized Applications

Note:
Welcome!  I'm Dan Hedges.

We're here to discuss two things: Blockchain and healthcare.  And yes, we are
also going to talk about Bitcoin and cryptography.  We are going to attempt to
get it all done in an hour, even though the overview of cryptography itself
deserves more than that.  We have a lot of ground to cover.  Steele yourself:
I'm going to go fast.

This audience has a mix of people, some technical and some very very technical.
If I'm talking about something that's just a little too mathy for you, take a
deep breath, it won't last long and I'll win you back in a minute or two.


### Blockchain and Healthcare
#### The Hype

![Economist](/content/blockchain/images/EconomistScreenShot.png)
<!-- .element class="fragment" width="30%" -->
![ulaHealth Summit](/content/blockchain/images/ulahealth.jpeg)
<!-- .element class="fragment" width="30%" -->
![ONC Logo](/content/blockchain/images/logo-dept-hhs.jpg)
<!-- .element class="fragment" width="30%" -->

Note:
So what is blockchain doing in healthcare?

There is a great deal of hype.  The Economist did a cover
story on Blockchain applications, and featured healthcare as a major target
for disruption.  There have been multiple summits specifically for healthcare
blockchain apps, including one here in Austin.  Google "blockchain healthcare"
and you get over 600K results.  This year, the ONC -- the Department of Health and Human
Services' Office of the National Coordinator for Health Information Technology --
issued a whitepaper challenge on blockchain in healthcare and got 70 submissions,
including the 15 winners which have now been published on their site.

There is a healthcare revolution brewing that will happen over the next
decade or so.

So, what is it?

The first thing you need to understand is that it all goes back to 2009, when
the blockchain was invented as part of an innovative new financial invention
known as Bitcoin.



## What is Bitcoin?


### Bitcoin

<h3>
<span class="fragment">Distributed</span>
<span class="fragment">Crypto</span><span class="fragment">Currency</span>
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

Traits of hashing: <!-- .element class="fragment" -->
- Collision Resistance <!-- .element class="fragment" -->
- Hiding <!-- .element class="fragment" -->
- Puzzle-Friendliness <!-- .element class="fragment" -->

Note:
I said before that Bitcoin depends on Cryptography to prove its safety.  What,
precisely does it need?

Hashing is a fast algorithm to take as input a digital document of
any length and output a fixed-length number.  Any change to the document, no matter how small, must
cause the new output to be markedly different, to the point that no one can
successively approach a target value by subtly adjusting the document.  This
is necessary for proof-of-work above, and also for chaining together the
blockchain.

Collision-resistance means it is intractable to find two documents that hash to
the same number.  It's possible, but you and I will never see the day.

Hiding means that if I gave you a hash, there is no feasible way you can find
a document that would give me the hash.

And puzzle-friendliness means essentially that any change to the document results
in a completely unpredictable change to the number.  It looks like a random number
for every different message.

The most common application of hashing is passwords on websites.  Sites do not
store your password, they essentially store a hash of your password, and when
you enter your password the site hashes the password and compares the number
to the stored hash.

The hash is very important in constructing the data structure known as the
blockchain.



## What is a Blockchain?

### Blockchain

The centralized ledger of transactions, copied to every node in the Bitcoin
network.

![Bitcoin Logo](/content/blockchain/images/bitcoin.jpg)
<!-- .element  class="fragment" height="35%" -->

![Blockchain Imagined](/content/blockchain/images/blockchain.svg.png)
<!-- .element  class="fragment" height="35%" style="background-color: #FFFFFF"-->

Note:
So, what is a blockchain?

When you hear blockchain, you should think of Bitcoin: the world's first
successful distributed cryptocurrency.  Bitcoin was invented in 2009 by an
unknown person under the pseudonym Satoshi Nakamoto, and one of the innovations
it created was the blockchain.  The term "blockchain" can be used to describe
the Bitcoin implementation, or the  technology.

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
    - Reward halves from time to time <!-- .element class="fragment" -->


### Consensus

But first... <!-- .element class="fragment" -->

Note:
And that brings us to the topic of consensus, that is, how do nodes agree on
what is officially in the ledger?

Sadly, we are not ready to answer that question yet.  We need more mathy stuff.



## Cryptography Part 2

- Signing <!-- .element class="fragment" -->
- Encryption <!-- .element class="fragment" -->

Note:
We've already discussed cryptographic hashing, and how it is used in blockchains
to ensure immutability and provide proof-of-work.  That's all great, but what
you really want to know is: can cryptography help me to commit murder?

To find out, we're going to discuss two primitives: signing and encryption.


![Sarah Bernhardt as Hamlet](/content/blockchain/images/Bernhardt_Hamlet2.jpg)

Note:
You are the ruling king of Denmark, and Prince Hamlet is being an insufferable
bother, always whining "My uncle killed my dad and married my mom, blah, blah,
blah..."  It would be nice if he were out of the picture.  So, you get two
sycophants to accompany Hamlet on an all-expense-paid trip to visit England.
With them, you send a diplomatic pouch for the queen, asking the queen to
execute Hamlet for you.

Well, sadly, on a long boatride, Hamlet sneaks a look at the letter while the
sycophants are sleeping.  He gets wise to the plan.  He's not happy with it.  
Then he substitutes his own letter, asking the queen instead to execute
Rosencrantz and Gildenstern, sealing it with his own ring -- inherited from his
father, it is a copy of the official royal seal of the king of Denmark.
Rosencrantz and Guildenstern deliver the pouch as requested, and when the queen
can't tell the letter is forged, they get a final nasty surprise.  Dangit.

The question is, can we use modern cryptography to help the king of Denmark
kill Hamlet and thus avoid the poetic meanderings from the second half of the
play?

(Image: Sarah Bernhardt as Hamlet, from wikipedia:
https://en.wikipedia.org/wiki/Hamlet#/media/File:Bernhardt_Hamlet2.jpg )


### Public-Private Key Cryptography

Everyone must have:
- A secret key
- A public key

Note:
Before we begin, we need everyone in the system to have two things: a secret
(or private) key that is kept completely secret, known only to the holder, and a
public key that you could print on a business card for all we care.  They both
boil down to very, very big numbers.

It should be noted that these two keys are related mathematically.  Here's an
oversimplification that may be helpful: imagine that the private key is a giant
prime number.  We have algorithms that can generate giant prime numbers pretty
quickly.  Now, take your secret giant prime number, your secret key, and
multiply it by another giant prime number of about the same size.  You get
an even bigger super-giant composite number with two prime factors.  That's your
public key.  If anyone could take your public key and find a number that divides
it evenly, your secret key would be lost.  Thankfully, that's not possible.  You
would die before a brute-force attack would find the number, and in fact the
universe would probably die too.

Suffice to say, if anyone could devise a way to calculate the private key from
the public key, all of Bitcoin would fail.  Thankfully, a lot of really smart
people think that's not possible.


### Signing

- Queen's Keys:
    - QS (queen secret)
    - QP (queen public)
- King's Keys:
    - KS (king secret)
    - KP (king public)
- Signing: <!-- .element class="fragment" -->
    - Signature := Sign(Message, KS)
- Verifying: <!-- .element class="fragment" -->
    - Verify(Message, Signature, KP)

Note:
One problem from the Hamlet story is that Hamlet was able to sign the document,
and that forgery was undetected by the queen.  So our first step will be, how
can the queen detect a forgery?

To do that, we first calculate the signature.  The sign function takes two
parameters -- the message and our secret key.  No one can calculate the signature
without knowing the secret key.

When the queen receives the message, she verifies the signature.  The verify
function takes the message, and the signature, and the king's public key.  If
the signature checks out, then only the king could have signed it.  There is no
way Hamlet could have computed the signature, unless he stole the king's secret
key.

If you think about it, digital signing is actually more secure than old-fashioned
handwriting paper signatures.  If you look at a document I signed, you could
study my handwriting and learn how I used my pen.  You could cut out my signature
and paste it physically to a document you fax off somewhere.  But digital signing
is different.  Even if you have a document I signed digitally, you can't copy
my signature onto a different document.  The Sign function takes a message and
computes a completely different signature for every message.

Both the Sign and Verify functions are fast.


### Encryption

- Queen's Keys:
    - QS (queen secret)
    - QP (queen public)
- King's Keys:
    - KS (king secret)
    - KP (king public)
- EncryptedMessage := Encrypt(Message, QP) <!-- .element class="fragment" -->
- DecryptedMessage := Decrypt(EncryptedMessage, QS) <!-- .element class="fragment" -->

Note:
So now, Hamlet cannot forge a new letter without getting detected.  That's pretty
good, but we can do better.  Hamlet could still read the message in transit, and
if he does that, he might make other travel arrangements.  What can we do about
that?

Enter encryption.  Say the king wants to encrypt a message that only the queen
can read.  For this operation, we leave the king's keys alone -- we don't need
them.  That makes sense, since anyone could encrypt a message for the queen.
The encryption function takes the message and the queen's public key, and outputs
an encrypted message.  That encrypted message gets delivered to the queen.  The
queen runs the Decrypt function, which takes the encrypted message and her secret
key, and then she views the DecryptedMessage, which exactly matches the message
the king started with.

In our murder plot, we should also use a combination of both encryption and
signing.  Which function should we apply first?  Should we sign an encrypted
message, or perhaps encrypt a signed message?  It actually doesn't matter.
The queen will be able to read and verify the message both ways.

I should mention at this point that Bitcoin doesn't use encryption.  I mention
it here because blockchain applications of the future might.



## Back to Bitcoin

![Node Network](/content/blockchain/images/NodeNetwork.svg)

![Blockchain Structure](/content/blockchain/images/BlockchainStructure.png)

Note:
Now, with Hamlet finally dead, let's go back to Bitcoin.  How can all the nodes
in the Bitcoin network all agree on what blocks are officially on the blockchain?
That is a process called consensus.


### Consensus

A node must:
- Validate all transactions in a block. <!-- .element class="fragment" -->
    - Did the owners really sign the transactions? <!-- .element class="fragment" -->
    - Did they really own the  coins?  (Double-spend problem) <!-- .element class="fragment" -->
- Find the longest valid chain of blocks. <!-- .element class="fragment" -->
- Propose a new block that points back to that chain. <!-- .element class="fragment" -->

Note:
So, how does a node decide what is officially on the ledger?  Remember, there is
no centralized storage -- all the storage is shared (duplicated) on all the
nodes.  A compliant node is one that is running an official version of the open-source
software.

That's all you need to achieve consensus.


### Malicious Attacks
#### Stealing Bitcoins

![Malicious Transaction](/content/blockchain/images/MaliciousTransaction.svg)

Note:
What if you attack the system, by proposing a block that transfers everyone's
Bitcoins to you?  Well, the transaction would not be signed by the owners of the
Bitcoins, so compliant nodes would recognize your transactions are invalid, and
they would build their blockchains on other blocks.  So you would never achieve
consensus of your proposed transactions


### Malicious Attacks
#### Transaction Preference

![Node Network With Malicious Node](/content/blockchain/images/NodeNetworkWithMalicious.svg)
![Person I Hate](/content/blockchain/images/jfurnish.jpeg) <!-- .element class="fragment" -->

Note:
Say there is a particular person that I despise, and I want to manipulate the
currency to make him miserable.  Specifically, I don't want to recognize
any transaction that gives him Bitcoins.  I could propose a block that includes
every transaction except his.  I might even get my block accepted as the
next block in the chain.  But I won't get every block, and eventually a
compliant node will propose the winning block that will have his transaction.

In addition, I might not recognize any block containing a transaction of his
to be valid.  But in that case, all the other nodes will disagree with my node,
until my node becomes unable to keep a chain as long as the others, and then
vanishes into irrelevance.


### Malicious Attacks
#### Hackers in the Network

There is no such thing. <!-- .element class="fragment" -->

Note:
So, what if hackers attack the network?  They are in the network.  The network
invites you to try to hack into it.  That's not what makes the system secure.
It's the rules of cryptography, paired with the magic of consensus, that keeps
the system functioning.


### Rethinking Security

![Password Policy](/content/blockchain/images/password-policy.jpg)

Note:
We have preconceptions about how security should work.  There is a centralized
service.  You log in to the centralized service, with a username and password,
maybe if you're lucky 2-factor authentication.  Then, the centralized service
allows you access to what you can do, and prevents you from doing what you
shouldn't.  You protect against hackers with security professionals keeping them
out of the network, playing Red Team/Blue Team games and the like.

Bitcoin is different.  There is no centralized anything.  You create transactions
with your private signature, so we know that it's you.  And you can do anything
with those transactions that the consensus of the network allows.  Hackers
are welcome in the network -- there is nothing they can steal nor havoc they can
wreak.

That is a paradigm shift.

(Image: Twitter \@DanielAHedges:
https://twitter.com/DanielAHedges/status/779439458022154240)



## Why Blockchain?

Note:
So why would anyone want to use a blockchain?  Sometimes, people talk about
it as a specific kind of database.  Well, what kind?


### Blockchain as a Database

- Storage: replicated on every node <!-- .element class="fragment" -->
- Computation: amazingly inefficient <!-- .element class="fragment" -->
- Immutable.  So fixing errors is out. <!-- .element class="fragment" -->
- Hard to update. <!-- .element class="fragment" -->
- Distributed in implementation. <!-- .element class="fragment" -->
- Centralized conceptually. <!-- .element class="fragment" -->



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
forcibly evicted while her children were at school, while her house was
demolished.

This story happened in Honduras, and it is not uncommon in developing countries.
In the U.S., we sometimes take for granted that our government doesn't
routinely give in to corruption and bribes.

So, what can the Blockchain do for Mariana?


## Public Records

- Land and property titles
- Vehicle registrations

Note:
These things called Bitcoins are really just artificial constructs.  They could
be anything.  Bitcoin balances are just fixed-point numbers with eight digits
after the decimal point.  But that's just a convention.  You could trade multiple
currencies, commodities or equities in the same blockchain.  You can bet 300
quatloos on the newcomer.  It doesn't even have to be a number -- you can own
arbitrary strings.  Maybe that string could be a VIN number to legally prove
you own a car.


## Attestation

- Proof of insurance
- Proof of ownership
- Document notarization



## Blockchain 3.0

### Applications


### Proof of Existence

A logo for Acme Corp:

![Logo for Acme Corp](/content/blockchain/images/LogoA.png)

Note:
Say you're a freelance graphic designer, and you're about to pitch your idea for
a new logo to the big bad Acme corp.  Well, you might be worried that the
company will see your idea, not buy it, but then go ahead and use it anyway,
just saying it was their idea.  Is there anything you can do?  You could take
them to court, which might work, but can you be sure you can *prove* that it
was your idea?

(Image: Wikimedia
https://commons.wikimedia.org/wiki/File:Logo_of_alliance_of_the_libertarian_left.svg )


### Proof of Existence

Hash(document) -> Blockchain

![Blockchain Structure](/content/blockchain/images/BlockchainStructure.png)

Note:
Well, one idea is that you can take a hash of your document and put it in the
blockchain.  The blockchain is immutable and timestamped, so if you have the
document, you can prove that the document existed at the time of the meeting.
So at least if they say it was their idea at a later date, you can prove
they're lying.  And that's not nothing.



## So, What About Healthcare?

Note:
At this point, I haven't mentioned any use cases for healthcare.  Well, let's
talk about healthcare.  But first, let's talk about Roadhouse.


![Road House, 1989](/content/blockchain/images/Roadhouse.jpg)
<!-- .element width="45%" -->

Note:

Hat tip to Shahryar Sedghi, Blockchain Solutions Architect for IBM for the idea.
He says there are lots of references to this movie, but I haven't found them.

Road House was a surprisingly-not-unwatchable movie from 1989 (obviously), about
a bouncer who travels from town to town cleaning up dive bars that have become
pools of violence and corruption.  He's a bit of a bad-ass.

At one point in the movie, he gets cut in a bar fight, which is not unusual in
his line of work.  And when he goes to the hospital to get some stitches, the
doctor asks him about his medical history, and this happens:

(Image credit: IMDB http://www.imdb.com/title/tt0098206/mediaviewer/rm4134765824 )


![Road House Medical Record](/content/blockchain/images/RoadHouseMedicalRecord.gif)
<!-- .element width="70%" -->

Note:
He hands over his entire medical record, which he keeps in a folder in the trunk
of his car.  Now, as a moviegoer, you are supposed to be impressed at how tough,
yet practical, he is, and admire his character.

But, stop and think for a moment about this.  What are we actually seeing here?
This is a patient who is completely in charge of his own medical record.  Think
about what this means -- is it good for the patient?  Well, it's inconvenient
to carry your own medical record, and you might lose it.  But maybe he keeps
his own copy.

How about for the doctor?  Actually, the doctor had no qualms, in fact she
appreciated it so much, the two characters actually ended up together.

The EMR?  Well, there is no EMR in this scenario.  It was 1989.  And the front
desk staff didn't have any contact with the record, so they didn't mind.  Maybe
it was less work for them.

How about a hacker who wants to steal medical records?  I would say that it's
easier to steal *his* record -- you could open his trunk with a tire iron.  But
there would be no way to take, say, the nearly 40 million medical records that
were stolen from Anthem in 2015.  You would need to breach 40 million trunks,
which is labor-intensive.

What about a clinician who wants to run analytics on a population to predict
who will get the flu?  You cannot run those analytics on paper records kept by
the patient.

In fact, maybe the patient has too much power in this situation.  Presumably,
if he was embarrassed by his chlamydia prescription from back in college, he
could conveniently "lose" that page.  Then you'd get an inaccurate medical
history.

Keep this in your mind, because it's kind of key to understanding why the EMR
use case is considered the holy grail of blockchain healthcare applications.

And now, finally, let's talk about healthcare.



## And Now Finally

### Healthcare

![ONC Logo](/content/blockchain/images/logo-dept-hhs.jpg)
<!-- .element class="fragment" -->

Note:
So, what can Blockchain do for healthcare?

As I mentioned in the very beginning, the ONC -- the Department of Health and Human
Services' Office of the National Coordinator for Health Information Technology --
asked that very question, when it issued a
[whitepaper challenge](https://www.hhs.gov/about/news/2016/08/29/onc-announces-blockchain-challenge-winners.html)
on blockchain in
healthcare and got 70 submissions, including the 15 winners which have now been
published on their site.

I have been reading them slowly.  I have almost finished reading the winners.
There are a lot of them.  They make for rather dry reading.

One takeaway I have is that there is a great deal of variety in the submissions.
The good news is that means there are a lot of things we could do.  The bad news
is there is not any obvious choice on what we in the industry should do first.

In the next few slides, I will compare and contrast principles from multiple
papers, to give you an idea of the possibilities.

Please understand these are mostly my opinions.


### Medical Records Protected by the Blockchain

![Road House Medical Record](/content/blockchain/images/RoadHouseMedicalRecord.gif)
<!-- .element width="70%" class="fragment" -->

Note:
Almost all the papers are founded on the premise that we want to get medical
records secured by the blockchain.  If we can get that, then everything else
tends to fall into place.

Remember Road House Healthcare?  Keep it in mind.  Patient control over medical
data is a recurring theme.  Securing it in a blockchain system is constant.


### On- or Off-Chain?

![Blockchain Structure](/content/blockchain/images/BlockchainStructure.png)

Note:
In Bitcoin, all relevant data is on the blockchain, or "on-chain".  However,
Bitcoin is only a ledger of transactions.  If medical data were contained in
a blockchain system, the data itself is probably not stored on the blockchain.
One reason is that the blockchain is replicated on every single node.  You can't
have every patient's medical imaging results copied that many times.  It's
ridiculous.

Most, but not all, papers agree that medical data should be stored off-chain.
You would use the blockchain to store transactions, such as "I give this doctor
read and write access to my records."  Most of them.  One paper suggests storing
data on-chain in CCDAs.


### Incentives

- Using clinical trials to pay for system upkeep <!-- .element class="fragment" -->
    - [MIT OPAL/Enigma paper](https://www.healthit.gov/sites/default/files/1-78-blockchainandhealthitalgorithmsprivacydata_whitepaper.pdf) <!-- .element class="fragment"-->
        - Charge for running aggregate queries <!-- .element class="fragment"-->
    - MedRec paper
        - Clinical trials serve as miners
        - Are compensated in aggregate data

Note:
Bitcoin works on incentives.  Proof-of-work is crucial to distributed consensus,
and as a result the best miners are compensated in the most obvious currency --
newly minted Bitcoin.

In a centralized EMR, it is clear that the providers pay for the service.  But if
that service is decentralized, there is no clear EMR owner -- they all share
the same network.  So, who pays for the servers?

One common answer is clinical trials.  These are currently very expensive.  They
have plenty of money.  Now, imagine everyone's medical record is protected by the
blockchain.  You could write a bot that has permission to access people's
anonymized records, and only returns aggregate results.  You could see how many
people took this drug and then had a heart attack within six months, without any
access to private health records.


### The Role of EMRs

- Siloed Data Lakes <!-- .element class="fragment" -->
- Interoperability

Note:
If the data is completely patient-controlled, and secured in a non-proprietary
blockchain system, then EMRs no longer own and control the data.  In this way,
they would function more as siloed data lakes.  When someone requests a file
and has a valid access token, you surrender the file.  You no longer have
access to the file itself, except through the blockchain if you can get permission,
just like everybody else.

It would be possible for an EMR to be compensated nominal amounts for each
transaction.  Remember, after all, this all started with cryptocurrency.

The EMR still would provide a user interface for providers, and/or for patients.
There is still work to be done.  But that interface would work on any data
that came from any EMR.

We still need to fix interoperability.  Speaking of which...


### Proof of Interoperability

#### A Possible Replacement for Proof-of-Work

Note:
One of the papers had an interesting idea of replacing the Bitcoin proof-of-work
concept with a proof-of-interoperability, heavily leaning on FHIR.  Interesting.


### Clinical Decision Making

What if we could give Watson access to complete, anonymized health records,
including genomes?



## Current Status (December, 2016)

Total number of healthcare blockchain apps in production: <span class="fragment">0</span><!-- .element class="fragment"-->

Expect to hear more from startups during 2017.<!-- .element class="fragment"-->
