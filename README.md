<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: Secure Smart Contract Development

## Preparation

Here's how to get set up for the workshop. It should be super easy except if you're using Windows.

First, you need a web3 capable browser and some testnet ETH. You probably also have both, but if not, get [Metamask](https://metamask.io) and grab some ETH from the Ropsten faucets:

- https://faucet.metamask.io/
- https://faucet.ropsten.be/

The workshop exercises are hosted in an separate repo. Get a local copy by cloning the repo:

```
$ git clone https://github.com/ConsenSys/mythx-playground/
```

In this workshop you'll get to know both [MythX](https://mythx.io) as well as the latest build of [Mythril](https://github.com/ConsenSys/mythril-classic).

If you run into insurmountable problems ask the instructors for help. There's also a dedicated [Discord channel](https://discord.gg/kGDd8FP) that we created exclusively for you, the valued workshop participant.

### Setting up a Free MythX Account

TODO

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

## Part 1 - Detecting and Preventing Common Vulnerabilities

For the remainder of the workshop we'll be looking at different ways of identifying, fixing and preventing vulnerabilities during development.

### Exposure of Private Information

TODO

- [Guess the Random Number](https://github.com/ConsenSys/mythx-playground/blob/master/01_weak_random/RandomNumber.sol) - [Challenge on CTE](https://capturetheether.com/challenges/lotteries/guess-the-random-number/)

### Predictable Random Numbers

TODO

### Broken Access Controls

TODO - WalletLibrary Forensics

Note the "SWC" identifier at the end: That's a reference to the [Smart Contract Weakness Classification (EIP 1470)](https://smartcontractsecurity.github.io/SWC-registry/). You can look up details about each issue there.

- [Ethernaut Fallout](https://github.com/ConsenSys/mythx-playground/blob/master/02_capturing_ether/ethernaut-fallout.sol) - [Challenge on Ethernaut](https://ethernaut.openzeppelin.com/level/0x220beee334f1c1f8078352d88bcc4e6165b792f6)
- [Ethernaut Fallback](https://github.com/ConsenSys/mythx-playground/blob/master/02_capturing_ether/ethernaut-fallback.sol) - [Challenge on Ethernaut](https://ethernaut.openzeppelin.com/level/0x234094aac85628444a82dae0396c680974260be7)

### Integer Arithmetic Bugs

TODO

- [Ethernaut Token](https://github.com/ConsenSys/mythx-playground/blob/master/03_integer_arithmetics/ethernaut-token.sol) - [Challenge on Ethernaut](https://ethernaut.openzeppelin.com/level/0x6545df87f57d21cb096a0bfcc53a70464d062512)
- [Tokensale on CaptureTheEther](https://github.com/ConsenSys/mythx-playground/blob/master/03_integer_arithmetics/cte-tokensale.sol) - [Challenge on CTE](https://capturetheether.com/challenges/math/token-sale/)
TODO: Prevention with SafeMath

### Reentrancy

The infamous TheDAO was exploited by reentrancy in 2016. Although the community is more aware of it, reentrancy struck back in October 2018. 

TODO

## Part 2 - Writing Custom Security Tests

The Solidity `assert()` statement is used to specify conditions that are expected to *always* hold. If you want to prove certain assumptions about your code, you can put them into asserts and use Mythril's symbolic execution engine to do all the hard work for you.

## Part 3 - Security Testing in the Development Workflow

TODO

### Security Analysis with Truffle

TODO

### Integration with CircleCI

TODO

Ideally we want to know when vulnerabilities are introduced into the code base before they end up in the master branch.  In [exercise 3](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise3), we'll try the [Guardrails Github app](https://github.com/apps/guardrails) (Make sure to allow Issues in the repository settings as Guardrails will create issues), which should help you detect the issue. It's on you to fix it. Clone the [devcon4-playground](https://github.com/ConsenSys/devcon4-playground/) repository and create a new PR to resolve the issue that we exploited in Part 1.

## Credit

Created by [ConsenSys Diligence](https://consensys.net/diligence/) and the [Mythril](https://mythril.ai) team. Special thanks to Mick Ayzenberg ([Security Innovation](https://www.securityinnovation.com)), [Trail of Bits](https://www.trailofbits.com), Steve Marx of [CaptureTheEther](https://capturetheether.com) and ConsenSys fame and [Zeppelin Solutions](https://zeppelin.solutions) for vulnerable contract samples and challenges. Also, kudos to the [Truffle](https://truffleframework.com) and [Guardrails](https://www.guardrails.io) teams for working with us on Mythril Platform integration.
