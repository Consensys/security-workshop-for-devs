<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: The DevCon4 Workshop

  * [Preparation](#preparation)
  * [Part 1 - The Smart Contract Secure SDLC](#part-1---the-smart-contract-secure-sdlc)
  * [Part 2 - Threat Modeling](#part-2---threat-modeling)
  * [Part 3 - Security Verification and Hacking](#part-3---security-verification-and-hacking)
    + [Integer Arithmetic Fails](#integer-arithmetic-fails)
    + [Preventing Another DAOsaster](#preventing-another-daosaster)
    + [Ether Theft and Accidental Killings](#ether-theft-and-accidental-killings)
    + [Writing Custom Tests](#writing-custom-tests)
  * [What to Do Next](#what-to-do-next)
  * [Credit](#credit)

## Preparation

Here's how to get set up for the workshop.

**Getting Metamask and Testnet ETH:**

We'll be solving some challenges on CaptureTheEther. To do that, you'll need a web3-capable browser and some testnet ETH.

1. Get Metamask
2. Grab some ETH from the Ropsten Faucets: 

- https://faucet.metamask.io/
- https://faucet.ropsten.be/

**Downloading the Exercises:**

The workshop exercises are hosted in an separate repo. Clone the repo to get them:

```
$ git clone https://github.com/ConsenSys/devcon4-playground/
```

**Tools:**

In this workshop you'll get a sneak peek into the future: We'll be using the latest experimental build of [Mythril Classic](https://github.com/ConsenSys/mythril-classic) as well as [Mythril Platform](https://mythril.ai) prototypes we have built together with the [Truffle](https://truffleframework.com) and [Guardrails](https://www.guardrails.io) teams. Here's how install the tools:

| Tool        |  Instructions           | 
| :-------------: |-------------| 
| <img src="/static/mythril_new.png" width="180px"/>  | We'll use the newest and most awesome build of Mythril Classic during the workshop. 
|<img src="/static/truffle.png" width="90px"/>  |  [Truffle Suite](https://truffleframework.com) is a popular development framework for Ethereum. Run `npm install -g truffle-plus-analyze` to install a build of Truffle 5.0 with built-in Mythril Platform support (note that this is still early alpha).
| <img src="/static/guardrails.png" width="280px"/> | [Guardrails](https://www.guardrails.io) is a Github app that hooks into the development workflow and reports security issues on every pull request. To use it, install the [Guardrails Github app](https://github.com/apps/guardrails).

**Support:**

If anything goes wrong ask the instructors for help. Some of our core devs will also be on standby on [Discord](https://discord.gg/E3YrVtG) during the workshop (sometimes they can be quite nice and helpful).

## Part 1 - The Smart Contract Secure SDLC

We'll start with a little bit of theory (sorry guys, life isn't always just fun and games). In part 1, [Tom Lindeman](https://twitter.com/EtherDotBlue) explains secure SDLC processes. He's not a coder like the rest of us, so please be gentle and don't ask him any hard technical questions.

TL;DR: Security should be incorporated during all phases of development. This info graphic sums things up nicely:

<p align="center">
	<img src="/static/sdlc.png" height="400px"/>
</p>

## Part 2 - Threat Modeling

Before and during buidling a smart contract system you should think about potential threats and countermeasures. This process is formally known as threat modeling. In part 2, [Gerhard Wagner](https://twitter.com/g3rh4rdw4gn3r) introduces threat modeling basics. Here's the workshop material:

- [Presentation slides](slides/How_to_Not_Get_Rekt_Part_1_Threat_Modeling.pdf)
- [Blockchain incident threat list](threat-modeling/threat_list_blockchain_incident_db.md)

**Threat Modeling Exercise:**

After all this theory it's finally time for some hands-on action. Pick one of the following options:

- [Build a threat model for your own smart contract system](threat-modeling/exercise_sample_system.md)
- [Build a threat model for Crypto Froggies](threat-modeling/exercise_sample_system.md)

## Part 3 - Security Verification and Hacking

In the threat modeling part, we saw stats about the most common vulnerability types. For the remainder of the workshop we'll be looking into identifying, fixing, exploiting and preventing commonly exploited vulnerabilities.

### Integer Arithmetic Fails

-- TODO: A few slides, show real-world hacks --

https://smartcontractsecurity.github.io/SWC-registry/docs/SWC-101

**Exercise 1:**

In [exercise 1](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise1) we'll give a sneak peek of the `truffle analyze` command, an upcoming feature of [Truffle Suite](https://truffleframework.com). Let's see if Truffle can spot the security bug and think about ways to fix it.

To make things fun, we'll have a crack at the exploiting the same vulnerability on [CaptureTheEther](https://capturetheether.com/challenges/math/token-sale/).

*Hint: You need to compile the project before running the analyze command.*

```
$ cd devcon4-playground/exercise1
$ truffle+analyze compile
$ truffle+analyze analyze
```

**Exercise 2:**

Mythril Classic has a few extra tricks up its sleeve. In the [second exercise](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise2), we'll find another integer arithmetic bug, and show how to use Mythril Classic to make the challenge on [CaptureTheEther](https://capturetheether.com/challenges/math/token-whale/) a little bit easier (in other words we'll cheat).

*Hint: Mythril Classic has a whole lot of command line options, but running it in default mode is usually fine. However, if you want to get more information, you can activate verbose reporting and debugging output.*

```
$ cd devcon4-playground/exercise2
$ myth -x contracts/Tokenwhale.sol
$ myth --verbose-report -v2 -x contracts/Tokenwhale.sol
```

### Preventing Another DAOsaster

-- TODO: Joseph's Slides go here --

**Exercise 3:**

To ensure that no bugs make it into the code, it's useful to integrate security analysis into the deployment pipeline. In [exercise 3](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise3), we'll try out the [Guardrails](https://www.guardrails.io) Github app, which should detect a couple of security issues. After brainstorming possible fixes for the issue(s), we'll then proceed to exploit them to steal testnet ETH from the [CaptureTheEther Bank](https://capturetheether.com/challenges/miscellaneous/token-bank/).

### Ether Theft and Accidental Killings

-- TODO: A few slides, show real-world hacks --

**Exercise 4:**

Mythril Classic can analyze smart contracts from many sources, including bytecode on the blockchain. In [exercise 4](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise4), we'll identify another type of vulnerability that has often been exploited in the past. We'll then show how to detect vulnerable contracts on the mainnet and auto-generate an exploit that extracts the ETH from the vulnerable contract.

Now the real fun starts! We'll deploy a real-world contract instance with a similar vulnerability. Whoever exploits it first is not only awesome, but also wins 0.1337 ETH for buying Pizza (or hodl).

### Writing Custom Tests

-- TODO: Writing custom tests to verify invariants with Mythril Classic. --

**Exercise 5:**

[Exercise 5](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise5).

## What to Do Next

- Solve the other challenges on CaptureTheEther and Security Innovation CTF
- Major Mythril Platform CTF soon
- Beta launch on first of December
- MYTH token launch in early 2019

## Credit

By [ConsenSys Diligence](https://consensys.net/diligence/) and the [Mythril](https://mythril.ai) team. Special thanks to Mick Ayzenberg (Security Innovation).

Todo: Add logos

- ConsenSys Diligence
- Mythril

