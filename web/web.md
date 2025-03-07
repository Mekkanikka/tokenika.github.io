# What is EOS?

EOS is a blockchain-based, decentralized operating system, designed to support commercial-scale decentralized applications by providing all of the necessary core functionality, enabling businesses to build blockchain applications in a way similar to web-based applications.

Source: [quora.com](https://www.quora.com/What-is-EOS-cryptocurrency), by Roee-Oren, July 2017

EOS is the blockchain for building commercial scale decentralized applications that are indistinguishable from centralized alternatives.

Source: [steemit.com](https://steemit.com/eos/@stellabelle/re-dantheman-re-kyriacos-re-dantheman-re-eosio-introducing-the-eos-blog-on-steemit-20170514t144829951z), by Dan Larimer, May 2017

The EOS.IO software introduces a new blockchain architecture designed to enable vertical and horizontal scaling of decentralized applications. This is achieved by creating an operating system-like construct upon which applications can be built. The software provides accounts, authentication, databases, asynchronous communication and the scheduling of applications across hundreds of CPU cores or clusters. The resulting technology is a blockchain architecture that scales to millions of transactions per second, eliminates user fees, and allows for quick and easy deployment of decentralized applications.

Source: [github.com](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md), Technical White Paper, June 2017

---

# Main features

For the complete description of all features please refer to [the Technical White Paper](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md). Below is the summary, as presented by [the official web page](https://eos.io/):

#### 1. Scalable

* Supports thousands of Commercial Scale DApps
* Parallel Execution
* Asynchronous Communication
* Separates Authentication from Execution

#### 2. Flexible

* Freeze and Fix Broken Applications
* Generalized Role-based Permissions
* Web Assembly

#### 3. Usable

* Web Toolkit for Interface Development
* Self Describing Interfaces
* Self Describing Database Schemes
* Declarative Permission Scheme

---

# Why EOS?

The most important thing about EOS is that it is built on the following premise: what really matters is what business needs, and not what technology can deliver. This approach is clearly manifested in [the Technical White Paper](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md) which starts with the following requirements for blockchain applications:

* Support Millions of Users
* Free Usage
* Easy Upgrades and Bug Recovery
* Low Latency
* Parallel vs. Sequential Performance

Below are six reasons why we think EOS is a good choice for building advanced blockchain applications:

#### 1. Processing power

While other DLT (Distributed Ledger Technology) solutions definitely require a second layer of processing to be able to handle real-life applications (e.g. Lightening Network in Bitcoin or Plasma in Ethereum), EOS offers enormous processing power in its primary layer. This is the result of the following features:

* EOS consensus mechanism (DPOS, Delegated Proof of Stake) introduces a fixed number of block producers. As a result, time intervals between blocks are exactly 3 seconds, and with an improved server infrastructure can be reduced even more. It's worth noting that despite this limited number of block producers, DPOS is the most decentralized system in existence - provided we apply [a rational measure of decentralization](http://bytemaster.github.io/article/2015/01/13/Decentralization-of-Nxt-vs-BitShares/). 
* EOS blockchain maintains *consensus over events* instead the common approach of *consensus over state*. As a result, it takes longer to restart a network node but on the other hand transaction processing is much quicker. This is a very fortunate trade-off, as node restarting is a rare event, while efficient transaction processing is needed most of the time.
* Currently all blockchains rely upon sequential processing of transactions; this fundamentally limits the throughput of a blockchain to the computational capacity of a single CPU core. EOS architecture has been designed as [multi-threaded on the very fundamental level](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md#deterministic-parallel-execution-of-applications). Not everything can be executed in this way, but those things which can (e.g. validating preconditions) are subject of parallel processing.
* EOS enables [partial evaluation of blockchain state](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md#partial-evaluation-of-blockchain-state). This means that an EOS node can selectively process transactions and ignore those which are of no interest for it. The assumption is that everyone should not have to run everything, especially if they only need to use a small subset of the applications.

#### 2. Much wider context

In EOS smart-contracts are treated as a very broad phenomena. As human errors in smart-contracts are unavoidable, there need to be built-in mechanisms which handle such cases. EOS has a binding constitution encoded in the blockchain, arbitration for resolving disputes and stakeholders voting on important decisions. Had *The DAO* incident happened on EOS, there would be a clear procedure to follow to resolve the issue in an orderly manner. It's clear that EOS is designed with the needs of serious businesses in mind: before they commit their resources and reputation to a large blockchain project, they need to be sure there is an emergency procedure in case things get out of control.

#### 3. Complete operating system

EOS is much more than just a decentralized computer. Actually, it is a full-blown  decentralized operating system. What this means is that there are features embedded right in the blockchain which can be utilized by any advanced application built on EOS. Those include:  databases, account permissions, account recovery, scheduling, authentication, inter-app communication. Thus application developers building on EOS only need to write code for what is unique for their application, whereas the fundamental functionality is delivered by the blockchain itself.

#### 4. Web Assembly as a compiler

Smart-contracts in EOS will be compiled to [WebAssembly](http://webassembly.org/), which is an emerging industry standard backed by Microsoft, Google, and Apple. The goal of this standard is to make it possible to run untrusted high-performance code in your browser. [WebAssembly is a big deal](https://medium.com/mozilla-tech/why-webassembly-is-a-game-changer-for-the-web-and-a-source-of-pride-for-mozilla-and-firefox-dda80e4c43cb), as it will enable high performance web applications such as video and image editing and games. It provides a universal compile target that enables applications to be developed in any language. Currently there are compilers for C, C++, and Rust. There is even work going on to compile Solidity to WebAssembly.

#### 5. No transaction fees (from the end-user's view point)

From the business point of view, it is hard to defend the paradigm of end-user being forced to pay for the mere fact of interacting with an application. Unfortunately, this is the standard case in the current crypto-space. A Steem-like application could not have survived in such a model. EOS offers a solution which prevails in business around the world: the cost of operating a business is born by the service producer (i.e. the smart-contract owner), and not by their client. The latter should have free access by default, unless the business owner opts for a different pricing strategy.

#### 6. Concept proved in practice

As generic solutions, all smart-contract platforms attempt to create an abstract space which will serve as a basis for concrete application implementations. All, except EOS, do it by starting with the abstraction layer. EOS goes the opposite way: it evolved from concreate implementations into a generic platform. The EOS creators have already built two blockchains which actually work and handle a bigger amount of transactions than Bitcoin and Ethereum. Thus EOS is a generalization of two very concrete (and very different) implementations. As a result EOS will most probably end up being a highly practical solution.

---

# Known limitations

While we are clear about our strong commitment for EOS, we still aim to remain objective. Below there are the things you need to be aware of, if you want to bet on EOS:

* When compared to Ethereum, at the current stage EOS is not widely popular among developers and blockchain start-ups. There is still a lot that needs to be done in this area in order to raise awareness and attract businesses to experiment with EOS. It remains to be seen how the EOS team handles that. What we can be sure of, is that the token distribution has been a large success so far, so they are definitely not short on funding.
* EOS is not live yet. The testnet is about to be launched, and the ETA for live version is Q3 2018. It's a long time in this industry, yet bear in mind that Steem (i.e. the previous project by the same development team) was created in less than four months, which is quite unprecedented in the blockchain space. The long time dedicated for testing EOS indicates that quality of code has utmost priority, and when the system does go live it will probably be very packed with features and quite stable.

---

# Token distribution

EOS token distribution is quite unique in many respects:

* When designing the EOS distribution system, the primary goal was ensuring as fair and wide of a distribution as possible. For more details explaining the rationale behind it, please refer to [this post](https://steemit.com/eos/@eosio/draft-eos-token-sale-smart-contract).


* As the EOS blockchain is not live yet, what is being distributed are ERC20-based tokens on the Ethereum platform, which will be mapped 1:1 to proper EOS tokens once the system is launched. 
* What it means is that you need to trust the company which runs the distribution ([BlockOne]((http://block.one/))) to fulfill their promise. They have very strong motivation to do so, as it is well explained [here](https://steemit.com/eos/@cob/shedding-some-light-on-the-eos-token-purchase-agreement).
* The distribution started in June 2017 and will last on a daily basis over a period of approximately one year, till June 2018. This coincides with the system going live.

For more details regarding the distribution and purchasing the EOS tokens on the primary market, please refer to [the official website](https://eos.io/instructions) and [this introductory post](https://steemit.com/eos/@trogdor/the-eos-ico-for-dummies). If in doubt you might want to use [this walk-through](https://steemit.com/eos/@ash/full-walkthrough-how-to-join-eos-ico), or if you're an advanced user refer to [this guide](https://steemit.com/eos/@sandwich/contributing-to-eos-token-sale-with-myetherwallet-and-contract-inner-workings).

---

# Token role

#### What does the token represent?

The token represents access to available resources (e.g. bandwidth, storage space) on the EOS blockchain. If you own 1% of the tokens you are entitled to use 1% of the network. The more valuable the tokens get the more the network grows and the more resources you will get per token.

#### The tokens can be rented/leased

You will be able to rent your unused tokens to those companies/applications looking to get more bandwidth on the EOS blockchain. As [the white paper](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md#delegating-capacity) explains, a holder of tokens who may not have an immediate need to consume all or part of the available bandwidth, can give or rent such unconsumed bandwidth to others; the block producers will recognize this delegation of capacity and allocate bandwidth accordingly.

---

# Roadmap

##### Phase 1 - Minimal Viable Testing Environment - Summer 2017

- Standalone Node
- Native Contracts
- RPC Interface
- Command line Tools
- Basic Developer Documentation

##### Phase 2 - Minimal Viable Test Network - Fall 2017

- P2P Network Code
- WASM Sanitation & CPU Sandboxing
- Resource Usage Tracking & Rate Limiting
- Genesis Import Testing
- Interblockchain Communication

##### Phase 3 - Testing & Security Audits - Winter 2017, Spring 2018

- Develop Example Applications
- Bounties for Successfully Attacking Network
- Language Support
- Documentation & Tutorials

##### Phase 4 - Parallel Optimization - Summer / Fall 2018

##### Phase 5 - Cluster Implementation - The Future

Source: [github.com](https://github.com/EOSIO/Documentation/blob/master/Roadmap.md), June 2017

---

# Milestones

#### Test Network Release - due by September 14, 2017

This milestone will mark the initial release of a functional multi-node test network with the following capabilities:

- CLI,
- Wallet,
- Contract Publishing and Execution,
- Producer Voting,
- RPC Interface for querying Contract State,
- Documentation,
- Example Contracts

#### EOS Beta - due by December 31, 2017

This milestone should be "feature complete". Issues targeted for this milestone would be anything that is potentially consensus breaking.

Source: [github.com](https://github.com/EOSIO/eos/milestones), August 2017

---

# News

#### EOS.IO Heads to Shanghai for The 3rd Global Blockchain Summit 2017

We are giving away a select number of conference passes to community members that would like to attend September 14th-16th and meet the team.

Source: [steemit.com](https://steemit.com/eos/@eosio/eos-io-heads-to-shanghai-for-the-3rd-global-blockchain-summit-2017), by @eosio, August 2017

---

# ICO announcements

#### Cappasity Introduces Global AR/VR Ecosystem through September ICO

The [Cappasity AR Token](https://artoken.io/) ICO will begin in September and continue for four weeks. Funds raised will be used to create an AR/VR Innovation Fund to reward developers for creating excellent AR/VR applications. Participants can contribute using BTC, ETH, BCH, or EOS. Tokens will be issued as standard Ethereum tokens (ERC-20) but will be transferred into the EOS blockchain once it is functional.

Source: [cryptocoinsnews.com](https://www.cryptocoinsnews.com/cappasity-introduces-global-arvr-ecosystem-september-ico/), August 2017

---

# Introduction

#### EOS - An Introduction by Ian Grigg

This paper outlines the context, vision and software architecture underlying EOS, which we are building to serve a broad and diverse group of users with smart business.

Source: [iang.org](http://iang.org/papers/EOS_An_Introduction.pdf), by Ian Grigg, July 2017

#### Introduction to EOS: the Epic (blockchain) Operating System

EOS is a consensus blockchain operating system that provides databases, account permissions, scheduling, authentication, and internet-application communication to massively improve the efficiency of smart business development that uses parallelization to make possible blockchain scalability to millions of users and millions of transactions per second.

Source: [steemit.com](https://steemit.com/eos/@trogdor/introduction-to-eos-the-epic-blockchain-operating-system), by @trogdor, May 2017

#### EOS Shanghai Meetup July 2017

Brendan Blumer, Ian Grigg and Michael Cao speak during a Shanghai Meetup in July 2017.

Source: [youtube.com](https://www.youtube.com/watch?v=HUA52v-a2TA), July 2017

#### EOS Presentation from NY Consensus 2017

Daniel Larimer introduces EOS.

Source: [youtube.com](https://www.youtube.com/watch?v=MUZWZj1pu94), May 2017

---

# Concepts

#### Who Should Control A Blockchain?

Recently the topic of voting and control has been discussed by multiple blockchain projects. EOS, Ethereum, Bitcoin, and others all agree that blockchains must be controlled by voting, but who should do the voting?

Source: [steemit.com](https://steemit.com/eos/@eosio/who-should-control-a-blockchain), by Brendan Blumer, August 2017

#### Logically Consistent Principles for Token Distributions

The EOS Token distribution has been designed to hopefully create a distribution that is widely perceived to be fair based upon what we believe to be logically consistent principles.

Source: [steemit.com](https://steemit.com/eos/@eosio/logically-consistent-principles-for-token-distributions), by block.one, June 2017

#### What could a blockchain Constitution look like?

Traditional platforms such as Facebook and Twitter have a terms of service that define acceptable behavior of users. These terms of service create a hub and spoke model where Facebook and Twitter are the hub and the users are the spokes. A decentralized platform needs to have a peer-to-peer terms of service.

Source: [steemit.com](https://steemit.com/eos/@dantheman/what-could-a-blockchain-constitution-look-like), by Dan Larimer, June 2017

#### While A Constitution For A Blockchain May Seem Unusual, It Will Make Early Project Development Much Easier And Result In A More Responsive Platform.

While a blockchain constitution can be compared to the terms of service that many websites use, the main advantage of utilizing a constitution is the ability to make necessary changes efficiently.

Source: [steemit.com](https://steemit.com/eos/@cryptofreedom/while-a-constitution-for-a-blockchain-may-seem-unusual-it-will-make-early-project-development-much-easier-and-result-in-a-more), by @cryptofreedom, June 2017

#### On a Principled Approach to Blockchain Governance - 7 Requirements

One of the things that I learnt in the CAcert adventure was that governance was critical to the safe operation of large communities. How large is large ... is a question of much debate, but to put it bluntly, this is needed beyond say a 2 digit size, which I’ve always seen as around 30, but certainly well before Dunbar’s number of 150

Source: [steemit.com](https://steemit.com/eos/@iang/on-a-principled-approach-to-blockchain-governance-7-requirements), by Ian Grigg, May 2017

---

# Business

#### Statement Regarding the SEC’s Report on The DAO

Since we have received a number of requests to provide our reaction to the SEC’s recent report in relation to The DAO, we would like to state for the record that we are of the opinion that the SEC’s report does not affect the EOS ERC-20 compatible token (the “EOS tokens”) distribution on the Ethereum blockchain

Source: [steemit.com](https://steemit.com/eos/@eosio/block-one-statement-regarding-the-sec-s-report-on-the-dao), by Brendan Blumer, August 2017

#### An Update from Block.one CEO, Brendan Blumer

We appreciate the healthy skepticism and will always do our best to clarify misunderstandings. EOS is comprised of a robust community and backed by many of the the biggest influencers in the space - this is something we don't take for granted and would never compromise!

Source: [steemit.com](https://steemit.com/eos/@eosio/an-update-from-block-one-ceo-brendan-blumer), by Brendan Blumer, August 2017

#### A Recap: EOS Headlines London Fintech Week 2017

This year, an estimated 4,000 delegates from over 50 countries came together for London Fintech Week 2017 to hear from the world's leading experts on current and upcoming trends, challenges, and technology in the Fintech sector.

Source: [steemit.com](https://steemit.com/eosevents/@eosio/a-recap-eos-headlines-london-fintech-week-2017), by block.one, August 2017

#### Coindesk Libels Dan Larimer

Earlier this week Coindesk published its first story covering EOS, written by Aaron Stanley. Considering that EOS was one of the sponsors of Consensus 2017, it was surprising to see that the coverage of EOS was more negative than I would have expected.

Source: [steemit.com](https://steemit.com/eos/@belerophon/coindesk-libels-dan-larimer), by @belerophon, June 2017

#### Shedding some light on the EOS Token Purchase Agreement

I ABSOLUTELY agree with everyone losing their minds at the Purchase Agreement. It appears to be madness and it says black on white that we are buying useless crap. What I’m saying here is WHY it is written like that. In a nutshell: Governments make everything financial illegal.

Source: [steemit.com](https://steemit.com/eos/@cob/shedding-some-light-on-the-eos-token-purchase-agreement), by @cob, June 2017

#### My Approach to Acquiring EOS Tokens

I've spent the past couple of weeks figuring out my approach to get the most cheap EOS tokens as possible, quickly realising there's no way to determine if the price is okay from one day to the next with its pro-rated distribution mechanism.

Source: [steemit.com](https://steemit.com/eos/@kevinwong/my-approach-to-acquiring-eos-tokens), by @kevinwong, July 2017

---

# Technology

#### The Message is the Medium

This post introduces what I think is a fundamental flaw in almost all blockchain designs. In brief, it is the emphasis on state as the ‘atomic element’, when we could also build using messages instead. The implications of this are quite severe, but also quite hard to understand because the computer science concepts are a bit inaccessible to the non-CS world.

Source: [steemit.com](https://steemit.com/eos/@iang/the-message-is-the-medium), by Ian Grigg, May 2017

#### Web Assembly on EOS - 50,000 Transfers Per Second

Over the past couple of weeks the EOS development team has pivoted away from the Wren programming language and embraced Web Assembly. Today we would like to update everyone on the progress and initial results we have achieved.

Source: [steemit.com](https://steemit.com/eos/@dantheman/web-assembly-on-eos-50-000-transfers-per-second), by Dan Larimer, May 2017

#### DPOS Consensus Algorithm - The Missing White Paper

This is the missing white paper and analysis of delegated proof of stake (DPOS). The goal of this paper is to provide an analysis of why DPOS works and what makes it robust.

Source: [steemit.com](https://steemit.com/dpos/@dantheman/dpos-consensus-algorithm-this-missing-white-paper), by Dan Larimer, May 2017

#### Seeking Consensus on Consensus - DPOS or Delegated Proof of Stake and the Two Generals' Problem

Laying down the rails for a high performance financial blockchain-based ecosystem is well understood if controversial because there are a number of approaches - centralised, decentralised, un-permissioned, walled garden.

Source: [steemit.com](https://steemit.com/eos/@iang/seeking-consensus-on-consensus-dpos-or-delegated-proof-of-stake-and-the-two-generals-problem), by Ian Grigg, June 2017

#### Casper as an EOS Contract

I recently reviewed the latest Casper Research Paper in light of an ongoing discussion with Vitalik Buterin over consensus mechinisms. It is my intent to be as objective and practical as possible while recognizing all factors of the greater picture.

Source: [steemit.com](https://steemit.com/eos/@dan/casper-as-an-eos-contract), by Dan Larimer, August 2017

#### EOS.IO software will not suffer from Denial of Service (DOS) attacks like Ethereum

The problem Ethereum faces cannot be solved so long as it retains the current fee model and people insist on doing capped ICOs below market prices on a first-come, first-serve basis. These capped ICOs at below market prices might as well be million dollar giveaways.

Source: [steemit.com](https://steemit.com/eos/@dantheman/eos-io-software-will-not-suffer-from-denial-of-service-dos-attacks-like-ethereum), by Dan Larimer, June 2017

#### Blockchains should be designed like massively multiplayer games

In my previous article I made a case about why general purpose blockchains shouldn’t use the UTXO transaction model. Now I will make the case that blockchains should not store state in transactions and I will do so by borrowing lessons learned from massively multiplayer online games.

Source: [steemit.com](https://steemit.com/blockchain/@dantheman/blockchains-should-be-designed-like-massively-multiplayer-games), by Dan Larimer, April 2017

#### Blockchain State Representation should be Abstract and not part of Consensus

Today I would like to make the argument that the exact form the game state takes is irrelevant so long as all players agree on the validity of new game inputs. Stated another way, I am going to argue that there is no need to reach consensus on a canonical global state that can be represented by a hash.

Source: [steemit.com](https://steemit.com/etheruem/@dantheman/blockchain-state-representation-should-be-abstract-and-not-part-of-consensus), by Dan Larimer, April 2017

#### Blockchain UTXO Model is a Dead End for General Purpose Applications

Bitcoin was the first cryptocurrency to introduce the UTXO (Unspent Transaction Output) model for tracking database state. Every Bitcoin transaction consumes (spends) outputs from prior transactions and produces new outputs to be consumed by future transactions.

Source: [steemit.com](https://steemit.com/blockchain/@dantheman/blockchain-utxo-model-is-a-dead-end-for-general-purpose-applications), by Dan Larimer, April 2017

#### Individuals That Are Skeptical of The Upcoming EOS Project Simply Don't Understand The Fundamental Differences And Advantages That The EOS Network Will Offer.

The amount of attention and investment the upcoming EOS project has already seen makes some individuals skeptical, but to me it validates the demand and faith that investors have in the upcoming smart contract platform.

Source: [steemit.com](https://steemit.com/eos/@cryptofreedom/individuals-that-are-skeptical-of-the-upcoming-eos-project-simply-don-t-understand-the-fundamental-differences-and-advantages), by @cryptofreedom, August 2017

#### Could EOS Become the Most Widely Distributed ICO Ever?

Last month I wrote about the Fear of Missing Out (FOMO) surrounding the EOS ICO. I was wrong. Well, at least I was wrong about my initial short term predictions. I figured, with a year long ICO, the price of EOS would surely drop below the initial 5-day ICO price.

Source: [steemit.com](https://steemit.com/eos/@lukestokes/could-eos-become-the-most-widely-distributed-ico-ever), by @lukestokes, August 2017

#### A Smart Contract Platform Without Transaction Costs or the Need For 'gas' Will Finally Offer Proper Incentive To DApp Developers.

When developers must continually make micro-payments to continue to run and employ their DApps or contracts, price increases make it much less practical to continue to run and develop applications.

Source: [steemit.com](https://steemit.com/eos/@cryptofreedom/a-smart-contract-platform-without-transaction-costs-or-the-need-for-gas-will-finally-make-dapp-development-practical-an), by @cryptofreedom, May 2017

---

# Comparisons

#### EOS vs. Ethereum for Dummies!

In this post I will describe some of the differences in technological capabilities and limitations, as well as differences in design philosophies between the EOS and Ethereum platforms.

Source: [steemit.com](https://steemit.com/eos/@trogdor/eos-vs-ethereum-for-dummies), by @trogdor, June 2017

#### Response to Vitalik Buterin on EOS

Vitalik Buterin recently took a question about EOS at the Ethereum Shenzhen Keynote. Today I would like to provide some factual corrections to his claims about EOS.

Source: [steemit.com](https://steemit.com/eos/@dan/response-to-vitalik-buterin-on-eos), by Dan Larimer, August 2017

#### Reponse to Vitalik's Written Remarks

I just recently learned of these remarks from Vitalik on reddit. In these remark's Vitalik brings up the issue of Fees and Voting, both of which I feel deserve to be addressed.

Source: [steemit.com](https://steemit.com/eos/@dan/reponse-to-vitalik-s-written-remarks), by Dan Larimer, August 2017

#### Centralization of Cryptocurrency - Bitcoin, Ethereum, and EOS

This post is food for thought. A small group of individuals all met face to face in New York. This relatively small group decided the future of bitcoin which is now playing-out.

Source: [steemit.com](https://steemit.com/eos/@crypto-investor/centralization-of-cryptocurrency-bitcoin-ethereum-and-eos), by @crypto-investor, August 2017

#### EOS vs. Tezos vs. Tauchain: The Dummies' Simplification Of Possibly The Biggest Blockchain Launches Of 2017...

As the blockchain revolution gains momentum, so has this year brought countless ICOs with mega-hype and mind-blowing multi-million dollar crowdfunding campaigns. It's been a ride. And it's tough to keep up with *everything* coming out. Yet, there are a few projects that stand out amongst the many.

Source: [steemit.com](https://steemit.com/eos/@rok-sivante/eos-vs-tezos-vs-tauchain-the-dummies-simplification-of-possibly-the-biggest-blockchain-launches-of-2017), by @rok-sivante, August 2017

#### Comparison of Ethereum, Hyperledger Fabric and Corda

With this paper, we provide a brief analysis of the most notable differences between the distributed ledger technologies (DLT) Hyperledger Fabric, R3 Corda and Ethereum. Our intention is to give decision makers new to DLT guidance for what use cases Hyperledger Fabric, Corda and Ethereum are most suitable.

Source: [medium.com](https://medium.com/@philippsandner/comparison-of-ethereum-hyperledger-fabric-and-corda-21c1bb9442f6), by Philipp Sandner, June 2017

---

# Witnesses

#### Storage Costs on Blockchains using EOS.IO Software

The market will naturally and unavoidably imbue monetary properties to tokens created with the EOS.IO software. It will be necessary to implement dynamic pricing on the cost of consuming an additional unit of memory in order to keep prices practical for actual application development.

Source: [steemit.com](https://steemit.com/eos/@eosio/storage-costs-on-blockchains-using-eos-io-software), by @eosio, July 2017

#### Heavy duty witness node infrastructure

Witnesses are vulnerable to DDoS attacks. An attacker who knows the network location of your witness node can saturate your uplink to a level that makes you unable to produce blocks on time. Effectively, this means voting the witness out using a network-level attack.

Source: [steemit.com](https://steemit.com/witness-category/@gtg/heavy-duty-witness-node-infrastructure), by @gtg, July 2017

---

# Developers

#### EOS Development Sneak Peek for Very Early Developers

Although the official test network is still in preparation, anyone can create their own test environment on a local node. Please understand things are likely to change; however, not drastically so.

Source: [steemit.com](https://steemit.com/eosdev/@dan/eos-development-sneak-peek-for-very-early-developers), by Dan Larimer, August 2017

#### EOS - Example Exchange Contract and Benefits of C++

This week I have been focused on the API that smart contract developers will use to write contracts. To help facilitate the design of this API I have given myself an example contract to write. This time the example is a little bit more complex than just a currency contract, but a full up exchange between the native EOS currency and an example CURRENCY contract.

Source: [steemit.com](https://steemit.com/eos/@dan/eos-example-exchange-contract-and-benefits-of-c), by Dan Larimer, July 2017

#### Implementing a Hypothetical Currency Application on EOS

Today we are excited to share with you the first sneak peak of how EOS works and how developers build applications.

Source: [steemit.com](https://steemit.com/eos/@eosio/implementing-a-hypothetical-currency-application-on-eos), by Dan Larimer, May 2017

#### EOS - Developer’s Log Stardate 20176.30

This week block.one’s blockchain c++ development team has picked up 4 new members and has been interviewing a few more. The new recruits have already begun making contributions to the code.

Source: [steemit.com](https://steemit.com/eos/@dan/eos-developer-s-log-stardate-20176-30), by Dan Larimer, June 2017

#### EOS - Developer’s Log Stardate 201707.3

Today I met with the team to discuss the challenges of making smart contracts both easy to develop and easy to execute in parallel. If you are familiar with the challenges associated with parallel execution then you know the general rule that all data must be owned by a single thread. In terms of blockchains, that means all accounts need to own their data. Owning data means that no other thread of execution may read or write the data except by asynchronous message passing.

Source: [steemit.com](https://steemit.com/eos/@dan/eos-developer-s-log-starday-201707-3), by Dan Larimer, July 2017

#### EOS - Developer Log, Stardate 201707.7

This week we made great strides toward refining the architecture of EOS and defining the developer API. In particular we have identified a programming model that should enable parallelism while maximizing ease of use and clarity of the code.

Source: [steemit.com](https://steemit.com/eos/@dan/eos-developer-log-stardate-201707-7), by Dan Larimer, July 2017

#### EOS.IO Transaction Structure - Developer's Log, Stardate 201707.9

Today I would like to take a moment to explain the current structure of an EOS.IO transaction so that developers can better understand the concurrency model.

Source: [steemit.com](https://steemit.com/eos/@dan/eos-developer-s-log-stardate-201707-9), by Dan Larimer, July 2017

#### Easy Docker Guide for EOS

My previous post EOS Build Guide on Ubuntu provides instructions to build EOS on native machine. But Docker has many advantages, especially compatibility, so that providing information for Docker users sounds a good idea to me. 

Source: [steemit.com](https://steemit.com/eoskorea/@clayop/easy-docker-guide-for-eos), by @clayop, 2017

#### EOS Build Guide on Ubuntu

This is a brief guide of building EOS on Ubuntu 16.04 LTS (Google Compute Engine).

Source: [steemit.com](https://steemit.com/eoskorea/@clayop/eos-build-guide-on-ubunbu), by @clayop, August 2017

#### EOS Build Guide on Mac OS

Here is a brief guide to show you how to build the eos on MacOS Sierra 10.12.6.

Source: [steemit.com](https://steemit.com/eosdev/@skenan/eos-build-guide-on-mac-os), by @skenan, August 2017

#### Interested In Building An EOS Up Single-node Testnet But Don't Have Access To An Ubuntu Desktop?

While an Ubuntu desktop can be installed on programs similar to VirtualBox on your local device, I decided to go with a cloud server because it is much more forgiving.

Source: [steemit.com](https://steemit.com/eos/@cryptofreedom/interested-in-building-an-eos-up-single-node-testnet-but-don-t-have-access-to-an-ubuntu-desktop-i-had-success-deploying-a), by @cryptofreedom, June 2017

#### First Install & Run of EOS on a Blank Ubuntu 16

Here I am showing my steps to run one of the first full nodes of EOS. Unfortunately it just runs on local computer and it doesn't have peer to peer implemented yet, i.e. there is no communication with anybody.

Source: [steemit.com](https://steemit.com/eos/@deaddy/first-install-and-run-of-eos-on-a-blank-ubuntu-16), by @deaddy, June 2017

---

# Video interviews

#### The New Ethereum Killer Cryptocurrency Called EOS with Dan Larimer

Dan Larimer talks to Jeff Brewick (The Dollar Vigilante) about EOS.

Source: [youtube.com](https://www.youtube.com/watch?v=8e0tinzPTbY), July 2017

#### Coin Interview with EOS

Dan Larimer talks to the Coin team about EOS.

Source: [youtube.com](https://www.youtube.com/watch?v=K6uR0A9cC5Y), June 2017

#### Blocktalk Interview with EOS

Dan Larimer talks to the Blocktalk team about EOS.

Source: [youtube.com](https://www.youtube.com/watch?v=I-X4faugNuI), May 2017

#### Millions of transactions per second on EOS.IO blockchain

An interview with Ian Grigg of BlockOne

Source: [youtube.com](https://www.youtube.com/watch?v=UC6RYwYPnpU), July 2017

---

# Ecosystem

#### EOSscan Service

EOSscan is a service that helps you to purchase [EOS ](http://eos.io/)tokens at the most reasonable price. EOSscan offers you the current price of EOS tokens by analyzing transactions of EOS token purchases on the Ethereum blockchain.

Website: [eosscan.io](https://eosscan.io/)

---

# Who is who in EOS?

#### BlockOne

The company distributing EOS tokens and funding code development.

Website: [block.one](http://block.one/)

#### Brendan Blumer

BlockOne CEO. Serial entrepreneur, with roots in the gaming industry and real estate. Since 2015 he has moved his focus to blockchain technologies.

More: [crunchbase.com](https://www.crunchbase.com/person/brendan-blumer)

#### Daniel Larimer - @bytemaster, @dan, @dantheman

BlockOne CTO. Father of the concept of DAC/DAO (Decentralized Autonomous Company / Organization). Built two of the most widely used decentralized applications: BitShares and Steem.

More: [steemit.com](https://steemit.com/introduceyourself/@dantheman/daniel-larimer--co-founder-of-bitshares-steemit)

#### Ian Grigg - @iang

BlockOne partner. Inventor of the triple entry ledger Ricardian contracts. Industry leader in identity and cryptography.

More: [steemit.com](https://steemit.com/introduceyourself/@iang/i-am-iang)

#### Nathan Hourt - @modprobe

Code developer, has been active in all Dan Larimer's projects: BitShares, Steem and now EOS.

More: [steemit.com](https://steemit.com/introduceyourself/@modprobe/this-is-my-story-nathan-hourt-true-liberty-co-founder)

---

# Documentation

* There are several [example contracts](https://github.com/EOSIO/eos/tree/master/contracts) that you can use as a starting point.
* For information about the available APIs, refer to this document: [How to Write Contracts](https://eosio.github.io/eos/group__contractdev.html).
* There is also a helpful index of [all documentation](https://eosio.github.io/eos/modules.html).

Source: [steemit.com](https://steemit.com/eosdev/@dan/eos-development-sneak-peek-for-very-early-developers), by Dan Larimer, August 2017

---

# About us

*Tokenika* is a group of entrepreneurs based in Poland, aiming to contribute to the emerging EOS ecosystem and hopefully become an active EOS witness once the system goes live in Q3 2018.

As far as information is concerned, while we are strongly committed to EOS, we would like to remain honest and critical about EOS, more so than [the official website](https://eos.io/) can be. Our success is dependent on EOS success, yet we would like our content to be both comprehensive and unbiased.

Our intention is to contribute in the following ways:

* aggregate all meaningful information about EOS under one website 
* create executive summaries and comments 
* participate in the EOS testnet
* build useful tools for the EOS ecosystem
* hold public events to promote EOS in Poland and Europe

---

# Contact

You can reach us at eos@tokenika.io.

