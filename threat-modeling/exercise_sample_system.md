### Threat Modeling exercise - Crypto Froggies

#### Description 
You are building a crypto kittie clone for cute :frog: ... 😱 ... yes you heard right. The system will allow users to buy, sell, and breed digital frogs. Each frog has a unique appearance that is defined by its genes, and when you breed 2 frogs together, their genes combine in a unique way to produce an offspring, which you can then breed or sell. 

The team is ready eager to start and they are waiting for you. 


|  CEO |  CFO |  CTO |
|:-------------:|:-------------:|:-------------:|		
| <img height="100px"  align="right"   src="https://consequenceofsound.files.wordpress.com/2018/03/michael-scott.png"> | <img height="100px" src="https://media.giphy.com/media/ZPFQVis9WAAcE/giphy.gif"> | <img height="100px" src="https://i.stack.imgur.com/sdKcs.jpg">  |


Your are just putting the finishing touch on the high level specs for the crypto froggie system:

- The main interaction point for users will be a website that is going to be hosted by your organization. Users will go to your website, unlock their Metamask account and then be able to access their cute froggies. 
- You are planning to build some administrative functions in for your contract system just in case something goes wrong. You would like to pause any interaction with the contract system if there is anything unexpected happening. Only the CEO of the company will be able to call the function in case of :fire:.
- The second measure in case something goes wrong is to allow the CFO to withdraw all the funds that are kept in the contract.
- Both the CFO and CEO have their private keys on a hardware wallet and you advise them to keep them super-duper safe. 
- You have some serious social media pros on the team and they are going to promote crypto froggie on every platform you can think of and encourage people to breed more :frog::frog::frog:.
- Your CTO tells you that he wants to upgrade parts of the contract system from time to time. The key for upgrading the contract system will be the same one that he will use for deployment. He will keep the private key on a separate machine that has the development environment setup and that the dev team only uses it for this purpose.

Security is at the top of your mind and you want to make sure that the system is secure. You planning to use security analysis tools, do an audit and run a bug bounty. Besides that you are also thinking about operational security and want to make sure it is :100:. You heard that threat modeling might help with that and you decide to give it a go. 

#### Threat Model 

Use the [threat example table](./threat_list_blockchain_incident_db.md) from the Blockchain incident db and think how they might apply to this system. If you get lost have a look at threat modeling cheat sheet in the [slides](./../slides/How_to_Not_Get_Rekt_Volume_1_Threat_Modeling.pdf).   

| Number | Threat | Mitigation Strategy |
|--------|---------------------------------------------------------------|---------------------------------------------------------------|
| 1      |  An attacker hacks the crypto froggies website and creates fake sell orders in order to steal funds from users that want to trade froggies.  |  1. ) Perform regular security audits for the website.  2.) Implement EIP-712 so users can more easily verify what messages they sign. 3.) In the long term move to a more decentralised Dapp design that renders the UI from IPFS and not from a web server. |
| 2      |   |   |
| 3      |   |   |
| 4      |   |   |
| 5      |   |   |
