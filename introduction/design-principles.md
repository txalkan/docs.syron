# Design Principles

## :zap: Self-Sovereign Identity

Self-Sovereign Identity (SSI) empowers users by providing complete control over their data, including digital assets like Bitcoin-native tokens. Through the decentralization of identity management, enhanced privacy and security are achieved. Your BRC-20 collateral is securely locked in an SSI Vault, ensuring it stays under your control.

To ensure true user ownership and sovereignty, there are only gas fees. Vault maintenance, being on the Bitcoin network, incurs no fees. Creating Syron U$ dollars is fee-free, requiring only sufficient collateral. However, liquidation can occur if collateral falls below a threshold.

## :bank: Bitcoin Network

Bitcoin stands out as the most secure network, being a decentralized, permissionless, and tamper-resistant platform primarily due to its innovative use of the Proof-of-Work (PoW) consensus mechanism:

1. Mining: Bitcoin transactions are grouped into blocks, and miners compete to solve complex mathematical puzzles to add a block to the blockchain.

2. Consensus: The first miner to solve the puzzle broadcasts the solution, and other nodes verify its validity. Consensus is reached when the majority of nodes agree on the validity of the new block.

3. Security: PoW ensures security by making it computationally expensive to modify past blocks. Any attempt to alter a block would require redoing the work for that block and all subsequent blocks, making it economically unfeasible.

### Bitcoin-Native Assets

The first supported collateral includes tokens compliant with the [BRC-20 standard](https://layer1.gitbook.io/layer1-foundation/protocols/brc-20). Additionally, the SU$D token itself will adhere to this standard.

Syron is advancing its development on the Bitcoin layer-1 network, utilizing [Discreet Log Contract (DLC)](https://github.com/discreetlogcontracts/dlcspecs) technology in conjunction with [Pay-to-Taproot (P2TR)](https://river.com/learn/terms/p/pay-to-taproot-p2tr/) scripts.

### :bison: Bison's ZK-Rollup

The ZK-rollup by [Bison Labs](https://bisonlabs.io) is set to play a crucial role in enhancing Bitcoin's scalability. Zero-knowledge technology has the potential to significantly boost the network's transaction processing capacity without compromising security. This is achieved by grouping multiple layer-2 transactions into a single proof, which is then validated on the main Bitcoin layer.

ZK-rollups, therefore, enable faster and more cost-effective transactions, optimizing specific functionalities and use cases like stablecoins. This approach effectively addresses Bitcoin's throughput and scalability challenges without sacrificing security, making them an indispensable solution for the future of cryptocurrencies. In tackling Bitcoin's scalability hurdles, ZK-rollups emerge as a vital component, ensuring the network's growth while upholding security standards.

Consequently, Syron U$ dollars will seamlessly integrate on Bison to enable instant liquidity. This objective will be realized through a SU$D-based decentralized exchange where BRC-20 tokens and bitcoin will be available, with liquidity providers acting as the governing body of the protocol.
