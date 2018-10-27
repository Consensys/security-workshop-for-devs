<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: The DevCon4 Workshop

## Preparation

In this workshop you'll get a sneak peek into the future: We'll be using the latest experimental build of [Mythril Classic] as well as [Mythril Platform](https://mythril.ai) prototypes we have built together with the [Truffle](https://truffleframework.com) and [Guardrails](https://www.guardrails.io) teams. Here's how to get set up for the workshop.

### Getting Metamask and Testnet ETH

1. Get Metamask
2. Grab some ETH from the Ropsten Faucets: 

https://faucet.metamask.io/
https://faucet.ropsten.be/

### Installing the Mythril Classic Experimental Branch



### Installing the Truffle Prototype

Mythril Platform will be fully integrated into [Truffle Suite] in the near future. For now, you can try an early prototype.

### Installing Guardrails Alpha

[Guardrails] is Github app that hooks into the smart contract development workflow. 


### Real-time Support

If anything goes wrong ask the instructors for help. Some of our core devs will also be on standby on [Discord](https://discord.gg/E3YrVtG) during the workshop (usually they can be quite nice and helpful).

## Part 1: The Smart Contract Secure SDLC

We'll start with a little bit of theory (sorry guys, it can't all be fun and games). [Tom Lindeman](https://twitter.com/EtherDotBlue) explains Secure SDLC Processes. He's not a coder like the rest of us, so please be gentle and don't ask him any hard technical questions.

This info graphic sums things up pretty nicely.

<p align="center">
	<img src="/static/sdlc.png" height="400px"/>
</p>

## Part 2: Threat Modeling

Before buidling a smart contract system you should think about potential threats and countermeasures In this section of the workshop, [Gerhard Wagner](https://twitter.com/g3rh4rdw4gn3r) gives an overview on threat modeling. As an exercise, you'll then build a mini-threat-model for your own app or sample app. The [presentation slides](slides/How_to_Not_Get_Rekt_Part_1_Threat_Modeling.pdf) contain further instructions.

### Exercises

## Part 3: Security Verification and Hacking
Tricks
In the threat modeling part, we saw stats about the most common vulnerability types. For the remainder of the workshop we'll be looking into identifying, fixing, exploiting and preventing commonly exploited vulnerabilities. This is where the real fun starts!

#### Arithmetic Overflows

**Exercise one:**

https://capturetheether.com/challenges/math/token-whale/

1. Look at the source code with participants first. What's wrong?
2. Check the contract in a Truffle project with Truffle+analyze
3. Brainstorm a fix
4. Solve the exercise on CapturetheEther


**Exercise two:**
https://capturetheether.com/challenges/math/token-sale/

1. Look at the source code with participants first. What's wrong?
2. Solve the exercise on CapturetheEther. Tip: You can make things easy with Mythril Classic!
3. Show a neat example how Mythril classic can compute the solution

#### Re-Entrancy


#### Unprotected Criticial Functions


### Advanced Techniques

Asserting Invariants with Mythril Classic

## CTF Finale


# What's Next

- Beta launch on first of December
- MYTH token launch in early 2019

# Credit

By [ConsenSys Diligence](https://consensys.net/diligence/) and the [Mythril](https://mythril.ai) team.
