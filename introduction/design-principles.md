# Design Principles

## :zap: Self-Sovereign Identity

Self-Sovereign Identity (SSI) gives users complete control over their digital identity and assets, including cryptocurrencies. In SSI, users manage their identity without relying on third parties, enhancing privacy and security.

Tyron aims to enable users to leverage their bitcoin holdings in a decentralized manner. This paradigm means that users control their digital assets without depending on centralized systems. Tyron implements this through a user-owned Safety Deposit ₿ox (SDB), where the BTC collateral is securely stored.

In the Tyron dApp, each user's BTC collateral is securely locked in a separate SDB, guaranteeing sole management and control. Each SDB possesses its own Bitcoin address, with its information transparently available through any block explorer. This security measure stands in contrast to traditional systems, where intermediaries often have the ability to intervene.

To mint Syron US dollars, users only need BTC collateral in their SDB. This process aligns with Tyron's goal of accessibility and user empowerment, enabling users to freely withdraw stablecoins while retaining control of their BTC collateral.

However, if a user's BTC collateral falls below a certain threshold, then liquidation may occur. This mechanism maintains Syron's stability by ensuring adequate collateralization. Tyron aims to balance user autonomy with protocol stability, providing a secure and transparent platform for users to optimize their assets' capital efficiency and engage in decentralized finance.

## :bank: Bitcoin Network

Bitcoin stands out as the most secure network, being a decentralized, permissionless, and tamper-resistant platform primarily due to its innovative use of the Proof-of-Work (PoW) consensus mechanism:

1. Mining: Bitcoin transactions are grouped into blocks, and miners compete to solve complex mathematical puzzles to add a block to the blockchain.

2. Consensus: The first miner to solve the puzzle broadcasts the solution, and other nodes verify its validity. Consensus is reached when the majority of nodes agree on the validity of the new block.

3. Security: PoW ensures security by making it computationally expensive to modify past blocks. Any attempt to alter a block would require redoing the work for that block and all subsequent blocks, making it economically unfeasible.

### Bitcoin-Native Assets

The SYRON stablecoin ensures secure token transfers by leveraging the Bitcoin Ordinals protocol, adhering to the [BRC-20 meta-protocol](https://layer1.gitbook.io/layer1-foundation/protocols/brc-20) for compatibility.

Syron prioritizes development on the Bitcoin layer-1 network, employing various technologies for implementation. This includes utilizing the [Internet Computer Protocol](https://internetcomputer.org) and considering future integration with [Discreet Log Contract (DLC)](https://github.com/discreetlogcontracts/dlcspecs) technology and [Pay-to-Taproot (P2TR)](https://river.com/learn/terms/p/pay-to-taproot-p2tr/) Bitcoin scripts.

<!-- ### :bison: Bison's ZK-Rollup

Layer-2 solutions are in development to play a pivotal role in enhancing Bitcoin's scalability. Leveraging tools like zero-knowledge technology, they hold the potential to significantly bolster the Bitcoin network's transaction processing capacity while maintaining a trustless setup. This can be achieved by consolidating multiple layer-2 transactions into a single proof, which is then validated on the main Bitcoin layer.

ZK-rollups facilitate faster and more cost-effective transactions, optimizing specific functionalities and use cases like stablecoins. By addressing Bitcoin's throughput and scalability challenges without compromising on permissionless innovation, they emerge as an indispensable solution for the future of cryptocurrencies. In tackling Bitcoin's scalability hurdles, ZK-rollups can be essential components, ensuring the network's growth while adhering to Bitcoin standards.

As part of this advancement, Syron US dollars will seamlessly integrate with L2 platforms to provide instant liquidity for Bitcoin DeFi. To complement this vision of decentralized finance powered by Bitcoin, a SYRON-based decentralized exchange would present exciting opportunities for liquidity provision and farming. -->
