# 2024 ICP Korea Hacker House

## Content
- [Schedule](#schedule)
- [Hackathon](#hackathon)
  * [Tracks](#tracks)
    + [xChain dapps  - Total Prize pool of USD 12k (5k, 4k, 3k)](#xchain-dapps----total-prize-pool-of-usd-12k--5k--4k--3k-)
    + [Fully on-chain dapps - Total Prize pool of USD 8k (3k, 2k, 2k, 1k)](#fully-on-chain-dapps---total-prize-pool-of-usd-8k---5k---3k-)
    + [Build solidity smart contracts on ICP using the Bitfinity EVM - Total Prize pool of USD 3k ( 2k & 1k)](#build-solidity-smart-contracts-on-icp-using-the-bitfinity-evm---total-prize-pool-of-usd-3k---2k---1k-)
    + [Community Documentation Effort - Total Prize pool of USD 2k](#community-documentation-effort---total-prize-pool-of-usd-2k)
  * [Resources](#resources)
  * [Submission](#submission)
  * [Judging Criteria](#judging-criteria)

## Schedule


| **Time Slots**      | **Activity**                       | **Duration**   |
|-----------------|--------------------------------|------------|
| 8:00 - 8:30     | Registration                   | 30 mins    |
| 8:30 - 9:00     | Breakfast & Setting Up         | 30 mins    |
| 9:00 - 9:30     | Welcome & Context Setting      | 30 mins    |
| 9:30 - 10:30    | Whiteboard Session        | 60 mins    |
| 10:30 - 11:30   | [Building Fully On-Chain Dapps](https://docs.google.com/presentation/d/1UP80RDDK6MF6GPQAXSslWU5eoH_UAY-HkUgWlvYqfak/edit?usp=sharing)  | 60 mins    |
| 11:30 - 12:00   | Coding Smart Contract on Bitcoin | 30 mins  |
| 12:00 - 12:30   | [Building Cross-Chain Dapps](https://docs.google.com/presentation/d/1hbDoXVhSHfHsnJVx423YHOrVVSJPQjagt-XmYDdafEE/edit?usp=sharing)     | 30 mins    |
| 12:30 - 13:00   | Hacking challenges and team formation | 30 mins |
| 13:00 - 13:30   | Lunch + Networking             | 30 mins    |
| 14:00 - 15:00   | Further Mentoring on ICP and Bitfinity             | 60 mins    |
| 14:00 - 19:00   | Hacking Session                | 300 mins   |
| 19:00 - 19:30   | Small group presentations      | 30 mins    |
| 19:30 - 21:00   | Graduation & Demos             | 90 mins    |
| 21:00 - 22:00   | Dinner & Disbursal             | 60 mins    |


## Hackathon

### Tracks

Here are the four different tracks we have open and some example ideas you can
inspire yourself from/copy

#### xChain dapps  - Total Prize pool of USD 12k


The Internet Computer is a unique platform to build cross-chain dapps. In the
workshops, you’ll get introduced to threshold ECDSA, the Bitcoin integration,
ckBTC, HTTPS outcalls, and the IC-ETH-Starter template.

In this track, you are challenged to use one or more of these powerful building
blocks to create a novel application. In the following, we have listed some
projects you could tackle.

##### Prizes

1. USD 2.5k in ICP  + 2.5k grant based on project progress
2. USD 2k in ICP + 2k grant based on project progress
3. USD 1.5k in ICP + 1k grant based on project progress


These bounties focus on adding to the IC-ETH-Starter template which is a starter
project that uses an IC canister to verify the ownership of Ethereum NFTs:
https://github.com/dfinity/ic-eth-starter

**How to Get Started:**
1.  Attend the Integrating with Ethereum session from 11:30 to 12:00 or watch this Youtube tutorial video to get an overview of the IC-ETH-Starter project.
2.  Clone/Fork the IC-ETH-Starter template.

##### Add verification of ERC-20 tokens. (Beginner)
The IC-ETH-Starter can currently verify ownership of ERC-721 and ERC-1155 NFTs. Add support for ERC-20 tokens.

**Requirements:**
-   A user would input an Etherscan link to an ERC20 smart contract address in the OpenSea / Etherscan link section on the Verify page.
-   Once a user clicks on Verify Token, the app will request the user to sign and verify if the user does own a positive balance of the ERC20 token.
-   The ERC20 token verification with the user wallet address will be listed on the Home page.

**Hints:**

-   Enable ERC-20 as a token type
    -   Add erc20 as a token type on Line 11 in `src/services/HistoryService.ts`
-   Add a function to verify ownership of an ERC-20 token
    -   Add a function similar to `erc721_owner_of` and `erc1155_balance_of` to check
    for the user balance of the ERC20 token.

-   Enable the user to input a link from Ethereum that references an ERC20 smart contract
    -   Adjust the `verifyNFT` function in `src/components/WalletArea.tsx` to check the user balance of the ERC20 token using the function created in Add a function to verify ownership of an ERC-20 token.

[**Full Tutorial Link**](/erc20icp.md)

##### Add other ownership details. (Beginner)

The IC-ETH-Starter shows the NFT image, name, and link to OpenSea alongside the wallet address of the user who verified ownership of the NFT. Provide owners with other information on their verified NFTs such as:

-   date and time of purchase
-   the purchase amount in ETH
-   the name of the NFT collection

**Requirements:**
-   Upon token verification, the verification listed on the Home page will list additional details than currently provided.

**Hints:**
-   Add a function that queries additional data on NFTs
    -   Add a function that queries additional data on NFTs in `src/components/WalletArea.tsx`
    -   Call the function in the VerifyNFT function when verifying the ownership of the NFT

-   Save the data
    -   Update the NFT type and `addNFTs` function to accept additional data that you would like to save about the ownership of the NFT
    -   Enable verification of NFTs on other chains. (Beginner)

#### Enable verification of NFTs on other chains. (Intermediate)

The IC-ETH-Starter can currently verify ownership of ERC-721 and ERC-1155 NFTs on Ethereum and its testnets (Goerli and Sepolia). Adding support for other EVM-compatible chains, such as:

-   Arbitrum
-   Avalanche
-   Optimism
-   Polygon
-   Binance Smart Chain

**Requirements:**
-   A user can input a block explorer link to an NFT on another chain. You can optionally add a dropdown that allows the user to select the chain of the NFT that they want to verify ownership of.
-   Click "Verify Token" and sign your message.
-   The app will verify that you own the NFT.

**Hints:**

-   Add a corresponding chain RPC
    -   Add the corresponding chain RPC under the get_rpc_endpoint function in `canisters/ic_eth/src/eth_rpc.rs`

-   Adjust functions to accept the new chain
    -   Adjust `parseOpenSeaNft` to accept a newly supported chain. Add another parse function to handle a URL link from a supported block explorer

##### Create attestations during verification (Advanced)

Verified owners should be able to add notes to the verification process. Upon
verifying their NFT ownership, owners can add different notes under their
verified NFTs. Bonus points if you can keep the notes only visible to certain
Internet Computer principals using vetKeys.

**Requirements:**
-   A user inputs the block explorer link to the NFT you want to verify and add a message.
-   Click "Verify Token" and sign your message.
-   The app will verify that you own the NFT.
-   If the verification is successful, your NFT verification details and message will be displayed on the home page.

**Resources:**

[vetKeys](https://internetcomputer.org/docs/current/developer-docs/integrations/vetkeys/technology-overview)

##### Create a Chat Between Verified Owners of the NFTs in the same Collection (Advanced)
Create a chat between verified owners of any NFT collection. For example, if an
NFT owner verifies their ownership of a Bored Ape, the app will open a chat
between any other Bored Ape owners who have verified their ownership. You can
gamify the experience by giving the first x owners to verify their NFTs in a
collection a special reward, such as an NFT or token.

**Requirements:**
-   A chat that is only visible to wallet addresses that verified NFTs/tokens in the same collection.

#### Ideas to build with the Bitcoin integration and ckBTC

##### Augment PoS example to fully fledged product website - virtual store with ckBTC (Intermediate)
Using the [POS](https://internetcomputer.org/docs/current/samples/pos) example, from the internet computer documentation. You can extend it
to have an inventory of items and

##### Add NFC payments to the PoS example dapp (Advanced)
Extend the last POS example to request payments via NFC instead of QR code!

##### File Sharing Payment (Advanced)
Upload files locally and exchange them with various principals through ckBTC.

The cli utility wrapping around dfx should upload binary blob with a hash -
anyone should be able buy a hash for a given amount - would get copied to their own storage canister - which they would be allowed to download.


#### Fully on-chain dapps - Total Prize pool of USD 8k

Utilize the Internet Computer to build a fully on-chain dapp. Consider using a
starter project or a sample dapp to kickstart your development. Here are some
possible directions you could take


-   **SocialFi applications** - Social interactions on chains means that users own their data. On ICP you can host websites and interact with smart canisters directly from the browser. On top of this, ICP has the smoothest user onboarding experience. No wallet necessary.
-   **DAO tooling** - ICP has the capability of hosting the entire governance process for DAOs on-chain. Show us what you can build to make DAOs thrive.
-   **Privacy focused applications** - Blockchains in general are not the best for privacy of data. vetKeys on ICP help you build dapps in which users can preserve their privacy.
-   **RWA DeFi protocols** - With https outcalls, ICP canisters can bring in real world data streams on chain. We are looking for projects that tokenize new assets and bring them on chain.

##### Prizes

1. USD 1.5k in ICP  + 1.5k grant based on project progress
2. USD 1k in ICP + 1k grant based on project progress
3. USD 1k in ICP + 1k grant based on project progress
4. USD 1k in ICP


#### Build solidity smart contracts on ICP using the Bitfinity EVM - Total Prize pool of USD 3k

[Bitfinity](Bitfinity is an Ethereum Virtual Machine (EVM) implemented as a smart contract on Internet Computer Protocol) is an Ethereum Virtual Machine (EVM) implemented as a smart contract on Internet Computer Protocol
It helps scale the Ethereum ecosystem for developers to operate their apps on an Ethereum-compatible, high-throughput, scalable, and future-safe platform, with low transaction costs for their users.

Here are some suggested themes. Projects are not limited to these verticals.

- DeFi (e.g. AMM, Aggregator, Lending & Borrowing, etc.)
- NFT & Gaming (e.g. NFT Platform, POAP dApp, Marketplace, Web3 Game etc.)
- Infrastructure (e.g. Remix, Bridge, Text Messaging, Internet Identity etc.)


##### Prizes

1. USD 2k in ICP
2. USD 1k in ICP

#### Community Documentation Effort - Total Prize pool of USD 2k

The goal is to start a community documentation effort covering the core
protocol, canister development and the advantage of the IC.

-   Recreate the Motoko developer journey in Rust as we will have strong Rust skills gathered in one place.
-   Show the actual code development step by step.
-   Have a community controlled project.
-   Translate it in different languages.
-   Create something similar to learn Rust with too many examples.
-   Create tutorials instead of examples.
-   Get to be some of the first contributor and can help steer the project.
-   Community get to show what they think is the best side of the IC

### Resources

- Discord channel for the event: https://discord.gg/kyUJNWwg
- [ICP Hackathon Cheatsheet](https://dfinityorg.notion.site/ICP-Hackathon-Cheat-Sheet-b2921239266149de81021412f572351c)
- [Awesome Internet Computer Dev Resources](https://github.com/dfinity/awesome-internet-computer)
- [Rust CDK docs](https://docs.rs/ic-cdk/latest/ic_cdk/)
- [AI Chatbot](https://icp-ai-chat-frontend.vercel.app/)

#### Cycles

Follow [these steps](https://internetcomputer.org/docs/current/developer-docs/setup/cycles/cycles-faucet) to receive cycles to deploy on mainnet.

### Submission
To submit a project for the hackathon - raise a pull request and  every commit
before the deadline will be considered.

Your submission needs to be in `submissions/`

In order for your PR to be considered you need to have a `README.md` file at the
root of the repository which contains:
-   project description
-   track
-   team participants
    -   please use GitHub username for everyone
    -   Discord IDs
-   canister ID(s) of mainnet deployment
-   feedback part
    -   what have you learned
    -   what were the challenges you ran into
    -   what are you proud of

### Judging

#### Presentations and judging
While the DFINITY, Patika, and Bitfinity crew will be judging submissions,
each group will be presenting the project to hackers around their table in a
small committee.

The winner(s) of each track will then present their project on stage.

#### Judging Criteria

-   **X Factor and Potential**
    -   What is the wow factor of the idea? Does it have potential?
-   **Technical Competence**
    -   What is the quality of the technical designs and source code?
-   **Impact**
    -   Does this project solve a real-world problem? Can people use it?
-   **Progression**
    -   Can a library be used? Is a service actually usable? How far did you go?
-   **IC Superpowers**
    -   How well did you utilize the superpowers of the Internet Computer?

[DFINITY Hackathon Terms and Conditions](https://www.notion.so/dfinityorg/DFINITY-HACKATHON-TERMS-AND-CONDITIONS-Fully-On-Chain-with-ICP-1faf692d49a64c89afb5589a7219eee2?pvs=4)
