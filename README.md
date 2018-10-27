<p align="center">
	<img src="/static/notrekt-logo.png" height="200px"/>
</p>

# How To Not Get Rekt: The DevCon4 Workshop

  * [Preparation](#preparation)
  * [Part 1 - The Smart Contract Secure SDLC](#part-1---the-smart-contract-secure-sdlc)
  * [Part 2 - Threat Modeling](#part-2---threat-modeling)
  * [Part 3 - Security Verification and Hacking](#part-3---security-verification-and-hacking)
    + [Arithmetic Overflows](#arithmetic-overflows)
    + [Re-Entrancy](#re-entrancy)
    + [Unprotected Criticial Functions](#unprotected-criticial-functions)
    + [Advanced Techniques - Verification of Custom Invariants](#advanced-techniques---verification-of-custom-invariants)
  * [CTF Finale](#ctf-finale)
  * [Call for Participation](#call-for-participation)
  * [Credit](#credit)

## Preparation

In this workshop you'll get a sneak peek into the future: We'll be using the latest experimental build of [Mythril Classic](https://www.guardrails.io) as well as [Mythril Platform](https://mythril.ai) prototypes we have built together with the [Truffle](https://truffleframework.com) and [Guardrails](https://www.guardrails.io) teams. Here's how to get set up for the workshop.

**Getting Metamask and Testnet ETH:**

1. Get Metamask
2. Grab some ETH from the Ropsten Faucets: 

https://faucet.metamask.io/
https://faucet.ropsten.be/

**Installing Tool used during the Workshop:**

| Tool        | Installation Instructions           | 
| :-------------: |-------------| 
| <img src="/static/mythril_new.png" width="180px"/>  | We'll use the newest and most awesome build of Mythril Classic during the workshop. 
|<img src="/static/truffle.png" width="90px"/>  |  [Truffle Suite](https://truffleframework.com) is a popular development framework for Ethereum. Run `npm install -g truffle_plus_analyze` to install a build of Truffle 5.0 with built-in Mythril Platform support (note that this is still early alpha).
| <img src="/static/guardrails.png" width="200px"/> | [Guardrails](https://www.guardrails.io) is Github app that hooks into the development workflow and reports security issues on every pull request. To use it, install the [Guardrails Github app](https://github.com/apps/guardrails).

**Support:**

If anything goes wrong ask the instructors for help. Some of our core devs will also be on standby on [Discord](https://discord.gg/E3YrVtG) during the workshop (usually they can be quite nice and helpful).

## Part 1 - The Smart Contract Secure SDLC

We'll start with a little bit of theory (sorry guys, it can't all be fun and games). [Tom Lindeman](https://twitter.com/EtherDotBlue) explains Secure SDLC Processes. He's not a coder like the rest of us, so please be gentle and don't ask him any hard technical questions.

This info graphic sums things up pretty nicely.

<p align="center">
	<img src="/static/sdlc.png" height="400px"/>
</p>

## Part 2 - Threat Modeling

Before buidling a smart contract system you should think about potential threats and countermeasures In this section of the workshop, [Gerhard Wagner](https://twitter.com/g3rh4rdw4gn3r) gives an overview on threat modeling. As an exercise, you'll then build a mini-threat-model for your own app or sample app. The [presentation slides](slides/How_to_Not_Get_Rekt_Part_1_Threat_Modeling.pdf) contain further instructions.

## Part 3 - Security Verification and Hacking

In the threat modeling part, we saw stats about the most common vulnerability types. For the remainder of the workshop we'll be looking into identifying, fixing, exploiting and preventing commonly exploited vulnerabilities.

### Arithmetic Operation Fails

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

### Preventing another DAOsaster


### Avoiding Accidental Suicide


### Verifying Custom Invariants (Advanced)

Asserting Invariants with Mythril Classic

## CTF Finale

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

