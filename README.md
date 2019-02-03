<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: The MythX and Mythril Classic Workshop

  * [Preparation](#preparation)
    + [Installing Truffle 5 and the MythX Plugin](#installing-truffle-5-prototype)=
    + [Installing Mythril Classic](#installing-mythril-classic)
  * [Part 1 - The Smart Contract Secure SDLC](#part-1---the-smart-contract-secure-sdlc)
  * [Part 2 - Threat Modeling](#part-2---threat-modeling)
  * [Part 3 - Reentrancy](#part-3---reentrancy)
  * [Part 4 - The Real Fun Begins](#part-4---the-real-fun-begins)
    + [Exercise 1 - Truffle Analyze](#exercise-1---truffle-analyze)
    + [Exercise 2 - Cheating on CTFs with Mythril Classic](#exercise-2---cheating-on-ctfs-with-mythril-classic)
    + [Exercise 3 - Continuous Integration with Github Projects](#exercise-3---continuous-integration-with-github-projects)
    + [Exercise 4 - Hacking Contracts on the Mainnet](#exercise-4---hacking-contracts-on-the-mainnet)
    + [Exercise 5 - Verifying Invariants Using Asserts](#exercise-5---verifying-invariants-using-asserts)
    + [Exercise 6 - The Final Challenge](#exercise-6---the-final-challenge)
  * [What to Do Next](#what-to-do-next)
  * [Credit](#credit)

## Preparation

Here's how to get set up for the workshop. It should be super easy except if you're using Windows.

First, you need a web3 capable browser and some testnet ETH. You probably also have both, but if not, get [Metamask](https://metamask.io) and grab some ETH from the Ropsten faucets:

- https://faucet.metamask.io/
- https://faucet.ropsten.be/

The workshop exercises are hosted in an separate repo. Get a local copy by cloning the repo:

```
$ git clone https://github.com/ConsenSys/mythx-playground/
```

In this workshop you'll get to know both the [MythX security analysis API](https://mythx.io) as well as the latest build of [Mythril Classic](https://github.com/ConsenSys/mythril-classic).

If you run into insurmountable problems ask the instructors for help. There's also a dedicated [Discord channel](https://discord.gg/kGDd8FP) that we created exclusively for you, the valued workshop participant. Some of
our core devs will be on standby to fix bugs in realtime.

### Installing Truffle 5 with MythX Support

[Truffle Suite](https://truffleframework.com) is a popular development framework for Ethereum. For this workshop we'll install a prototype with Mythril Platform integration. Run the following command to install it:

```
$ npm install -g truffle-plus-analyze
$ truffle+analyze --help
Truffle+Analyze v5.0.0-beta.1g - a development framework for Ethereum

Usage: truffle+analyze <command> [options]

Commands:
(...)
  analyze   Run Mythril Platform analyses on a contract
(...)
```

Don't worry if you already have Truffle installed - installing the experimental build will not affect your existing installation. You'll get a separate binary called `truffle+analyze` that you uninstall later without breaking anything.

You'll also need a [Mythril Platform](https://mythril.ai) alpha key to use the `truffle analyze` command. In this workshop we'll use a shared temporary API key. To set it up, change into the devcon4-playground directory and run the setup script:

```
$ cd devcon4-playground
$ source mythril-staging
Congratulations! You are now set up to use the Mythril Platform staging server.
```

Note that this API key will only work for a couple of days. The official beta launch is still a few weeks away, but contact us on [Discord](https://discord.gg/VfTbCm4) if you want access.

### Installing  GuardRails Alpha

_(we'll go through this process in the workshop)_

[Guardrails](https://www.guardrails.io) is a Github app that hooks into the development workflow and reports security issues on pull requests. To try out Guardrails, fork the [devcon4-playground repository](https://github.com/ConsenSys/devcon4-playground/) using the "Fork" button on the top right. Then, install the [Guardrails Github app](https://github.com/apps/guardrails) and point it to your copy of the devcon4-playground repo.

### Installing Mythril Classic

_Mythril Classic uses solc to compile Solidity files, so you'll need to [install that as well](https://solidity.readthedocs.io/en/latest/installing-solidity.html#binary-packages)_.

[Mythril Classic](https://github.com/ConsenSys/mythril-classic) is a command-line tool for advanced users. It can do a *lot* of stuff, such as analyzing contracts on the blockchain, creating control flow graphs, searching the Ethereum state trie and auto-generating transaction sequences to trigger bugs (plus you can use it to cheat in CTFs).

You can install the latest version from Pypi or Dockerhub (instructions in the [Mythril Classic Wiki](https://github.com/ConsenSys/mythril-classic/wiki/Installation-and-Setup). Make sure you have version 0.19.3 installed.


**Installing from Pypi**

```
$ pip3 install mythril
$ myth --version
Mythril version v0.19.3
```

**Installing from DockerHub**

```
$ docker pull mythril/myth
$ docker run mythril/myth --version
Mythril version v0.19.3
```

## Part 1 - The Smart Contract Secure SDLC

In part 1, [Tom Lindeman](https://twitter.com/EtherDotBlue) explains secure SDLC processes. He's not a coder like the rest of us, so please be gentle and don't ask him any hard technical questions.

TL;DR: Security should be incorporated during all phases of development. This info graphic sums things up nicely:

<p align="center">
	<img src="/static/sdlc.png" height="400px"/>
</p>

## Part 2 - Threat Modeling

Before and during buidling a smart contract system you should think about potential threats and countermeasures. This process is known as threat modeling. In part 2, [Gerhard Wagner](https://twitter.com/g3rh4rdw4gn3r) introduces threat modeling basics. Here's the workshop material:

- [Presentation slides](slides/How_to_Not_Get_Rekt_Volume_1_Threat_Modeling.pdf)
- [Blockchain incident threat list](threat-modeling/threat_list_blockchain_incident_db.md)

**Threat Modeling Exercise:**

After all this theory it's time for some hands-on action. Pick one of the following options:

- [Build a threat model for your own smart contract system](threat-modeling/exercise_your_own_system.md)
- [Build a threat model for Crypto Froggies](threat-modeling/exercise_sample_system.md)

## Part 3 - Reentrancy

The infamous TheDAO was exploited by reentrancy in 2016. Although the community is more aware of it, reentrancy struck back in October 2018. Joseph Chow will show patterns and warnings signals to watch out for, and how best practices can help defend against reentrancy. This will also help with one of the exercises in Part 4.

- Presentation slides [[Google]](https://docs.google.com/presentation/d/1rlxIeYU4iXBbPp7BeJwW5VMrzOZIClckMs8wseFrUQM/edit#slide=id.p1), [[PDF]](slides/Reentrancy%20Redux%20-%20Devcon4%202018.pdf)

## Part 4 - The Real Fun Begins

For the remainder of the workshop we'll be looking at different ways of identifying, fixing, exploiting and preventing vulnerabilities during development.

### Exercise 1 - Truffle Analyze

In [exercise 1](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise1) we'll give a sneak peek of the `truffle analyze` command, an upcoming feature of [Truffle Suite](https://truffleframework.com). Let's see if Truffle can spot the security bug and think about ways to fix it.

To run `truffle analyze`, first change into the project directory for exercise 1.
```
$ cd devcon4-playground/exercise1
$ truffle+analyze analyze
```

If you get an error message saying "You need to set environment variable MYTHRIL_API_KEY to run analyze", re-run the setup script which as described above.

The results you get from `truffle analyze` should look similar to this:

```
0:0   error  Contracts should be deployed with the same compiler version and flags that they have been tested with  SWC-103
20:4  error  The arithmetic operation can result in integer overflow   SWC-101
(...)
```

Note the "SWC" identifier at the end: That's a reference to the [Smart Contract Weakness Classification (EIP 1470)](https://smartcontractsecurity.github.io/SWC-registry/). You can look up details about each issue there.

Now things will get serious! We'll take the attacker's side and exploit this exact contract. Depending on your level of skill, pick one of the following:

- Easy: [Token](https://ethernaut.zeppelin.solutions/level/0x6545df87f57d21cb096a0bfcc53a70464d062512)
- A bit more difficult: [TokenWhale](https://capturetheether.com/challenges/math/token-whale/).

### Exercise 2 - Cheating on CTFs with Mythril Classic

Mythril Classic has a few extra tricks up its sleeve. In the [second exercise](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise2), we'll look at a the `Tokensale` contract from [CaptureTheEther](https://capturetheether.com/challenges/math/token-sale/). The source code of that contract is in the `exercise2` directory. The question is, does it have any vulnerabilities? Let's do a quick Mythril Classic run to find out:

```
$ myth -x exercise2/contracts/Tokensale.sol (Pypi)

$ docker run -v $(pwd)/exercise2/contracts:/contracts mythril/myth -x /contracts/Tokensale.sol (Docker)
```

Looks like another integer-related bug! Let's now think about how to best exploit this issue. What we want is to get a lot of tokens without paying a single ETH. A nice trick is to express the exact opposite of what we want as an *invariant* using an `assert()` statement and letting Mythril do the work of finding the solution.

Create a copy of `Tokensale.sol` called `Tokensale-cheat.sol` and add an assertion to the function `buy` as follows:

```
    function buy(uint256 numTokens) public payable {

        require(msg.value == numTokens * PRICE_PER_TOKEN);

        assert(!(msg.value == 0 && numTokens > 0));
```

This essentially means "it should never happen that numTokens is greater than zero if msg.value (the amount of Ether sent) is zero". Obviously, as the attacker that's precisely what we *want* to happen. By adding the `--verbose-report` flag, Mythril will give you the transaction data needed to violate the assertion.

```
$ myth -mexceptions -x exercise2/contracts/Tokensale-cheat.sol --verbose-report (Pypi)

$ docker run -v $(pwd)/exercise2/contracts:/contracts mythril/myth -mexceptions -x /contracts/Tokensale-cheat.sol --verbose-report (Docker)
```

Can you tell why "calldata" in Mythril's output has that particular value?

With the right calldata, you should now able to solve the [Tokensale challenge](https://capturetheether.com/challenges/math/token-sale/).

### Exercise 3 - Continuous Integration with Github Projects

**Part 1 - Hack**

We are going to hack $$$ the Etherbank in [exercise 3](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise3). Prefund Etherbank with 10 Ether and start hacking. You have solved the challenge when Etherbank is empty, call `challengeSolved()` to check if you are done. Deploying contracts to the test net and exploiting it there is more fun but it can also be slow to send transactions to the Ropsten test net. For that reason we recommend to deploy and solve the challenge in [Remix](http://remix.ethereum.org). If you want to take the risk go ahead and try the [CapturetheEther challenge](https://capturetheether.com/challenges/miscellaneous/token-bank/) instead. 

**Part 2 - Defend**

Ideally we want to know when vulnerabilities are introduced into the code base before they end up in the master branch.  In [exercise 3](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise3), we'll try the [Guardrails Github app](https://github.com/apps/guardrails) (Make sure to allow Issues in the repository settings as Guardrails will create issues), which should help you detect the issue. It's on you to fix it. Clone the [devcon4-playground](https://github.com/ConsenSys/devcon4-playground/) repository and create a new PR to resolve the issue that we exploited in Part 1.

### Exercise 4 - Hacking Contracts on the Mainnet

Mythril Classic can analyze smart contracts from many sources, including bytecode on the blockchain. In [exercise 4](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise4), we'll identify another type of vulnerability that has often been exploited in the past. We'll then show how to detect vulnerable contracts on the mainnet and auto-generate an exploit that extracts the kills the vulnerable contract.

An important aspect is the number of transactions that Mythril (symbolically) executes. The default number is 1, but you can increase it for a more in-depth analysis (note that this increases analysis time significantly). By setting max transactions to 2, you will also detect bugs that are two transactions "deep".

For this example, let's set the max transaction count to 2:

```
$ myth -x exercise4/contracts/Ownable.sol --max-transaction-count 2 --verbose-report (Pypi)

$ docker run -v $(pwd)/exercise4/contracts:/contracts mythril/myth -x /contracts/Ownable.sol --max-transaction-count 2 --verbose-report (Docker)
```

Again, the `--verbose-report` will give you the transaction sequence for triggering the bug - take a good look at the output!

Now the real fun starts: We'll deploy a real-world contract instance with a similar vulnerability. Whoever exploits it first is not only awesome, but also wins 0.1337 ETH for buying Pizza (or hodl). Tip: You can run Mythril Classic against an on-chain contract using the `-a` flag.

Tip: Use `myth -xia <address>` run Mythril against mainnet contracts using INFURA, and don't forget what you learned above :)

- [HACK THIS!](https://etherscan.io/address/0xe80a3d0a70a192dd4fbf9636235da70aa13e7b7d)

### Exercise 5 - Verifying Invariants Using Asserts

The Solidity `assert()` statement is used to specify conditions that are expected to *always* hold. If you want to prove certain assumptions about your code, you can put them into asserts and use Mythril's symbolic execution engine to do all the hard work for you.

Mythril Classic will detect reachable exceptions by default. To *only* search for exceptions, add the `-mexceptions` option.

```bash
$ myth -mexceptions -x <Solidity file>
```

In [exercise 5](https://github.com/ConsenSys/devcon4-playground/tree/master/exercise5), we'll write a test to (dis-)prove an invariant in a [token contract](https://github.com/ConsenSys/devcon4-playground/blob/master/exercise5/token-with-backdoor.sol). The token code sample was shown by Josselin Feist on TruffleCon 2018 (shouts to our friends from [Trail of Bits](https://www.trailofbits.com)).

The invariant we want to verify is that a user's balance can never exceed 1,000. A nice way to do this is to create a separate test contract that inherits from the contract to be tested. Create a new file named `token-with-backdoor-test.sol` in the `exercise5` directory and add a function containing the assertion that balances[msg.sender] must never exceed 1,000:

```solidity
import "./token-with-backdoor.sol";

contract TokenTest is Token {

    // Verify that the user's balance can never exceed 1000

    function verify_balance() {
        assert(balances[msg.sender] <= 1000);
    }

}
```

Now we should be ready to go! Run Mythril Classic against the newly created file:

```bash
$ myth -mexceptions -x exercise5/token-with-backdoor-test.sol --max-transaction-count 3 --verbose-report (Pypi)

$ docker run -v $(pwd)/exercise5:/exercise5 mythril/myth -mexceptions -x /exercise5/token-with-backdoor-test.sol --max-transaction-count 3 --verbose-report (Docker)
```

As you can see, in this case three transactions need to be sent in the correct order to violate the invariant. Again, it is useful to have a close look at Mythril's output and match it to the functions in the contract.

### Exercise 6 - The Final Challenge

As a fully certified Mythril expert, you are now capable of solving a more difficult CTF challenge. This challenge is worth another 0.1337 MYTH. This time there won't be any hints ;)

## What to Do Next

A great way to continue learning is playing challenges like [Capture the Ether](https://capturetheether.com), [Security Innovation CTF](https://blockchain-ctf.securityinnovation.com) and [Ethernaut](https://ethernaut.zeppelin.solutions).

If you're into buidling Ethereum security tooling, the Mythril team is probably *not* a good place for you. Because in our team, you get near-complete freedom to work on what you like on your own time, plus the resources you need to bring complex ideas life. That sucks, because most tool buidlers see their tools as side projects to work on in-between audits or on weekends. But if you, against all odds, *do* want to fully focus on building awesome technology that helps the ecosystem, you can always ping us on [Discord](https://discord.gg/kktn8Wt).

## Credit

Created by [ConsenSys Diligence](https://consensys.net/diligence/) and the [Mythril](https://mythril.ai) team. Special thanks to Mick Ayzenberg ([Security Innovation](https://www.securityinnovation.com)), [Trail of Bits](https://www.trailofbits.com), Steve Marx of [CaptureTheEther](https://capturetheether.com) and ConsenSys fame and [Zeppelin Solutions](https://zeppelin.solutions) for vulnerable contract samples and challenges. Also, kudos to the [Truffle](https://truffleframework.com) and [Guardrails](https://www.guardrails.io) teams for working with us on Mythril Platform integration.
