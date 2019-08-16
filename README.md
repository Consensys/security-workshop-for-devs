<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: Secure Smart Contract Development

In this workshop we'll practice detecting & preventing common bugs in Solidity/EVM smart contracts. We'll solve challenges from [CaptureTheEther](https://capturetheether.com) and [OpenZeppelin Ethernaut](https://ethernaut.openzeppelin.com) and learn how to use [Mythril](https://github.com/ConsenSys/mythril) and [MythX](https://mythx.io) during development to prevent security bugs and verify security properties.

## Preparation

Here's how to get set up for the workshop. It should be super easy except if you're using Windows.

First, you need a web3 capable browser and some testnet ETH. You probably also have both, but if not, get [Metamask](https://metamask.io) and grab some ETH from the Ropsten faucets:

- https://faucet.metamask.io/
- https://faucet.ropsten.be/

The workshop exercises are hosted in an separate repo. Get a local copy by cloning the repo:

```
$ git clone https://github.com/ConsenSys/mythx-playground/
```

If you run into insurmountable problems ask the instructors for help. There's also a dedicated [Discord channel](https://discord.gg/kGDd8FP) that we created exclusively for you, the valued workshop participant.

### Mythril vs. MythX

In this workshop we'll work with a couple of tools. [Mythril](https://github.com/ConsenSys/mythril) is an open-source symbolic analyzer that is geared towards auditors, while [MyhtX](https://mythx.io) is an API service for smart contract developers. Either tool (Mythril or MythX free tier) is sufficient for this workshop - feel free to try out both.

### Setting up Mythril

_Mythril uses solc to compile Solidity files, so you'll need to [install that as well](https://solidity.readthedocs.io/en/latest/installing-solidity.html#binary-packages)_.

[Mythril](https://github.com/ConsenSys/mythril-classic) is a command-line tool for advanced users. It can do a *lot* of stuff, such as analyzing contracts on the blockchain, creating control flow graphs, searching the Ethereum state trie and auto-generating transaction sequences to trigger bugs (plus you can use it to cheat in CTFs).

You can install the latest version from Pypi or Dockerhub (instructions in the [Mythril Wiki](https://github.com/ConsenSys/mythril-classic/wiki/Installation-and-Setup).

**Installing from Pypi**

```
$ pip3 install mythril
$ myth version
Mythril version v0.21.12
```

**Installing from DockerHub**

```
$ docker pull mythril/myth
$ docker run mythril/myth version
Mythril version v0.21.12
```

### Setting up a Free MythX Account

Head to the [MythX website](https://mythx.io) and sign up for a free account. You'll be able to use your Ethereum address and password with all MythX tools including the [Remix](https://remix.ethereum.org) plugin and [MythX for Truffle](https://github.com/ConsenSys/truffle-security). There's also a standalone command-line tool called [Sabre](https://github.com/b-mueller/sabre) which can be installed with:

```
$ npm install sabre-mythx
```

## Part 1 - Detecting and Preventing Common Vulnerabilities

For the remainder of the workshop we'll be looking at different ways of identifying, fixing and preventing vulnerabilities during development.

### Exposure of Private Information

Well, Ethereum is a *public* ledger so there nothing is really private. Here is an example of what not to do.

**Target Contract:**

- [Guess the Random Number](https://github.com/ConsenSys/mythx-playground/blob/master/01_weak_random/RandomNumber.sol) - [Challenge on CTE](https://capturetheether.com/challenges/lotteries/guess-the-random-number/)

### Predictable Random Numbers

It is impossible to create truly random numbers using Solidity. Let's see what happens if we rely on things like blocknumbers and blockhashes for randomness.

**Target Contract:**

- [Guess the New Number](https://github.com/ConsenSys/mythx-playground/blob/master/01_weak_random/GuessTheNewNumber.sol) - [Challenge on CTE](https://capturetheether.com/challenges/lotteries/guess-the-new-number/)

### Broken Access Controls

Some of the worst incidents so far were caused by critical functions that were inadvertently exposed to attackers. Remember [Parity WalletLibrary](https://github.com/ConsenSys/mythx-playground/blob/master/02_capturing_ether/SimpleWalletLibrary.sol)?

Mythril and MythX are great at discovering this bug class.

Note the "SWC" identifier at the end: That's a reference to the [Smart Contract Weakness Classification (EIP 1470)](https://smartcontractsecurity.github.io/SWC-registry/). You can look up details about each issue there.

**Target Contracts:**

- [Ethernaut Fallout](https://github.com/ConsenSys/mythx-playground/blob/master/02_capturing_ether/ethernaut-fallout.sol) - [Challenge on Ethernaut](https://ethernaut.openzeppelin.com/level/0x220beee334f1c1f8078352d88bcc4e6165b792f6)
- [Ethernaut Fallback](https://github.com/ConsenSys/mythx-playground/blob/master/02_capturing_ether/ethernaut-fallback.sol) - [Challenge on Ethernaut](https://ethernaut.openzeppelin.com/level/0x234094aac85628444a82dae0396c680974260be7)

### Integer Arithmetic Bugs

Antoher common source of bugs are integer overflows and underflows. We'll cover them im the next two examples. Hint: The best way to prevent integer arithmetic bugs is by using [SafeMath](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/math/SafeMath.sol).

- [Ethernaut Token](https://github.com/ConsenSys/mythx-playground/blob/master/03_integer_arithmetics/ethernaut-token.sol) - [Challenge on Ethernaut](https://ethernaut.openzeppelin.com/level/0x6545df87f57d21cb096a0bfcc53a70464d062512)
- [Tokensale on CaptureTheEther](https://github.com/ConsenSys/mythx-playground/blob/master/03_integer_arithmetics/cte-tokensale.sol) - [Challenge on CTE](https://capturetheether.com/challenges/math/token-sale/)

### Reentrancy

The infamous TheDAO was exploited by reentrancy in 2016. Although the community is more aware of it, reentrancy struck back in October 2018. 

Let's look at a [simplified example](https://github.com/ConsenSys/mythx-playground/blob/master/05_truffle_project/contracts/Reentrance.sol) of the DAO bug.

## Part 2 - Writing Custom Security Tests

The Solidity `assert()` statement is used to specify conditions that are expected to *always* hold. If you want to prove certain assumptions about your code, you can put them into asserts and use Mythril's symbolic execution engine to do all the hard work for you.

In thus exercise we'll write and check and invariant for [Etherbank](https://github.com/ConsenSys/mythx-playground/blob/master/04_custom_invariant/etherbank.sol).

## Part 3 - Security Testing in the Development Workflow

Catching bugs early during the development lifecycle saves a lot of pain. In this section we'll have a look at Truffle and CI integration.

### Security Analysis with Truffle

```
$ npm install truffle-security
```

## Credit

Created by [ConsenSys Diligence](https://consensys.net/diligence/) and the [Mythril](https://mythril.ai) team. Special thanks to Mick Ayzenberg ([Security Innovation](https://www.securityinnovation.com)), [Trail of Bits](https://www.trailofbits.com), Steve Marx of [CaptureTheEther](https://capturetheether.com) and ConsenSys fame and [Zeppelin Solutions](https://zeppelin.solutions) for vulnerable contract samples and challenges. Also, kudos to the [Truffle](https://truffleframework.com) and [Guardrails](https://www.guardrails.io) teams for working with us on Mythril Platform integration.
