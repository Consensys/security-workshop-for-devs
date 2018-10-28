<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: The DevCon4 Workshop

  * [Preparation](#preparation)
  * [Part 1 - The Smart Contract Secure SDLC](#part-1---the-smart-contract-secure-sdlc)
  * [Part 2 - Threat Modeling](#part-2---threat-modeling)
  * [Part 3 - Security Verification and Hacking](#part-3---security-verification-and-hacking)
    + [Exercise 1](#exercise-1)
    + [Exercise 2](#exercise-2)
    + [Exercise 3](#exercise-3)
    + [Exercise 4](#exercise-4)
    + [Exercise 5](#exercise-5)
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
$ git clone https://github.com/ConsenSys/devcon4-exercises/
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

We'll start with a little bit of theory (sorry guys, life isn't always just fun and games). [Tom Lindeman](https://twitter.com/EtherDotBlue) explains secure SDLC processes. He's not a coder like the rest of us, so please be gentle and don't ask him any hard technical questions.

This info graphic sums things up pretty nicely.

<p align="center">
	<img src="/static/sdlc.png" height="400px"/>
</p>

## Part 2 - Threat Modeling

Before buidling a smart contract system you should think about potential threats and countermeasures In this section of the workshop, [Gerhard Wagner](https://twitter.com/g3rh4rdw4gn3r) gives an overview on threat modeling. As an exercise, you'll then build a mini-threat-model for your own app or sample app. The [presentation slides](slides/How_to_Not_Get_Rekt_Part_1_Threat_Modeling.pdf) contain further instructions.

## Part 3 - Security Verification and Hacking

In the threat modeling part, we saw stats about the most common vulnerability types. For the remainder of the workshop we'll be looking into identifying, fixing, exploiting and preventing commonly exploited vulnerabilities.

### Exercise 1

In this [exercise](https://github.com/ConsenSys/devcon4-exercises/tree/master/exercise1), we'll try out the upcoming Mythril Platform "analyze" feature in Truffle Suite. Let's see if we can spot the bug and brainstorm a fix. Once that's done, we'll have a crack at the [hacking the token sale on CaptureTheEther](https://capturetheether.com/challenges/math/token-sale/)

Hint: You need to compile the project before running the analyze command.

```
$ cd exercise1
$ truffle+analyze compile
$ truffle+analyze analyze
```

### Exercise 2

Mythril Classic has a few extra tricks up it's sleeve. In the [second exercise](https://github.com/ConsenSys/devcon4-exercises/tree/master/exercise2), we'll look out for a similar bug as in exercise 1, and show how to use Mythril Classic to make solving the challenge on [CaptureTheEther](https://capturetheether.com/challenges/math/token-whale/)] a little bit easier (i.e. we'll learn how to cheat).

Hint: Mythril Classic has a whole lot of command line options, but running it in default mode is usually fine.

```
$ cd exercise2
$ myth -x contracts/Tokenwhale.sol
```

However, if you want to get more information, you can activate verbose reporting and debugging output.

```
$ myth --verbose-report -v2 -x contracts/Tokenwhale.sol
```

### Exercise 3

To ensure that no bugs make it into the code, it's useful to make security analysis a part of the deployment pipeline. In [exercise 3](https://github.com/ConsenSys/devcon4-exercises/tree/master/exercise3), we'll try out Guardrails on a Truffle project, which should detect a couple of security issues. After brainstorming possible fixes for the issue(s) detected, we'll then proceed to exploit the issue and steal somne testnet ETH from the [CaptureTheEther Bank](https://capturetheether.com/challenges/miscellaneous/token-bank/).

### Exercise 4

Taklking about extra tricks: Mythril Classic can analyze smart contracts from many sources, including bytecode on the blockchain. In [exercise 4](https://github.com/ConsenSys/devcon4-exercises/tree/master/exercise4), we'll identify another type of vulnerability that has often been exploited in the past. We'll then show how to detect this vulnerability on the mainnet and auto-generate an exploit that extracts all the ETH from the vulnerable contract.

Top top things off, we'll deploy a real-world instance of a vulnerable contract for our valued participants to exploit.

### Exercise 5

TODO: Writing custom tests to verify invariants.

[Exercise 5](https://github.com/ConsenSys/devcon4-exercises/tree/master/exercise5).

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

