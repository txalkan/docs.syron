# Syron: Bitcoin-Native Stablecoins for Self-Custodial Liquidity

**Xalkan Duarte**, Founder · xalkan@tyrondao.org

> **TL;DR**  
> Syron is a Bitcoin-native metaprotocol that enables users to access USD liquidity without selling their BTC. Users deposit Bitcoin into self-custodial Safety Deposit ₿oxes and mint overcollateralized stablecoins (SUSD) available as BRC-20 and Runes tokens across Bitcoin Layer1. Built on Chain Fusion technology connecting Bitcoin mainnet with the Internet Computer, Syron preserves complete user ownership while providing instant dollar-denominated liquidity. The protocol addresses the core Bitcoin holder dilemma: needing cash flow without breaking long-term BTC accumulation strategies. Currently testing on Bitcoin mainnet with multi-token availability, Syron represents the first implementation of truly self-custodial Bitcoin-backed stablecoins with native mainnet integration.

## Abstract

This whitepaper presents Syron, a decentralized metaprotocol for issuing Bitcoin-collateralized stablecoins that preserve user custody and enable instant liquidity access. As Bitcoin adoption grows, holders increasingly face the liquidity paradox: they need dollar-denominated cash flow but refuse to sell their appreciating BTC. Existing solutions require wrapped Bitcoin, custody transfer, or complex bridging mechanisms that compromise the core Bitcoin value proposition of self-sovereignty.

Syron solves this through Safety Deposit ₿ox smart contracts that lock native Bitcoin on Layer 1 while enabling stablecoin minting via Chain Fusion integration with the Internet Computer. Users maintain complete ownership of their Bitcoin collateral while accessing up to 66% loan-to-value in SUSD stablecoins, available in both BRC-20 and Runes token formats for maximum ecosystem compatibility.

Built on principles of monetary self-determination and financial sovereignty, Syron enables users to "be their own bank" without intermediaries, custody risks, or wrapped token complications. This paper outlines the technical architecture, implementation details, and broader implications of Bitcoin-native stablecoin infrastructure for decentralized finance.

## Introduction: The Bitcoin Liquidity Problem

Bitcoin holders face a fundamental paradox in today's financial system. They hold the world's most appreciating digital asset but struggle to access liquidity without selling their position. This creates a forced choice between maintaining Bitcoin exposure and meeting real-world financial needs—a choice that shouldn't exist in a properly functioning monetary system.

### Current Inadequate Solutions

**Selling Bitcoin:** The most direct approach, but holders miss future appreciation and face tax implications. For long-term Bitcoin believers, selling defeats the purpose of accumulation strategies.

**Wrapped Bitcoin (wBTC):** Requires transferring custody to centralized entities, violating Bitcoin's "not your keys, not your coins" principle. Users lose the self-sovereignty that makes Bitcoin valuable in the first place.

**Centralized Lending:** Platforms like BlockFi and Celsius have demonstrated the custody risks inherent in traditional crypto lending models. Users who trusted these platforms lost their Bitcoin entirely.

**Lightning Network Solutions:** While preserving Bitcoin nativity, Lightning-based lending remains complex, liquidity-constrained, and unsuitable for larger positions requiring stable dollar exposure.

### The Syron Solution

Syron introduces a new paradigm: Bitcoin-collateralized stablecoins that preserve complete user custody while providing instant dollar liquidity. Through Safety Deposit ₿ox smart contracts and Chain Fusion technology, users can:

- **Lock Bitcoin** in self-custodial smart wallets they control
- **Mint SUSD stablecoins** pegged to USD up to 66% of collateral value
- **Maintain ownership** of Bitcoin throughout the loan period
- **Access liquidity** for payments, investments, or operational needs
- **Choose token standards** between BRC-20 and Runes formats

This approach preserves Bitcoin's core value propositions—self-custody, censorship resistance, and monetary sovereignty—while solving the liquidity accessibility problem.

> Note: Syron's technical architecture serves broader principles of monetary self-determination. For detailed analysis of centralized monetary systems and their socio-political implications, see ["The Crisis of Self-Determination in the Age of Centralized States & Currencies"](whitepapers/self-determination.md) by Tyron Mapu CIC.

## Technical Architecture

### Safety Deposit ₿ox Infrastructure

The Safety Deposit ₿ox represents Syron's core innovation: a smart contract system that enables Bitcoin collateralization without custody transfer. Each user generates a unique Safety Deposit ₿ox by connecting their existing Bitcoin wallet, creating an auditable vault that they fully control.

**Key Features:**

- **Self-Custodial:** Users maintain full control over deposited Bitcoin through their controlling wallet
- **Deterministic:** Each Safety Deposit ₿ox is uniquely tied to its controlling wallet - funds can only be withdrawn to that wallet
- **Auditable:** All collateral holdings are transparently verifiable on-chain
- **Programmable:** Smart contract logic handles collateralization ratios and liquidation protection
- **Interoperable:** Works with existing Bitcoin and ICP wallets without additional software

The Safety Deposit ₿ox architecture builds on proven self-sovereign identity (SSI) principles developed by TyronDAO and supported by $75k in DFINITY Developer Grants, extending identity-controlled custody to Bitcoin financial infrastructure.

### Chain Fusion: Bitcoin + Internet Computer Integration

Syron leverages Chain Fusion technology to connect Bitcoin Layer 1 with Internet Computer smart contract capabilities. This integration enables:

**Native Bitcoin Integration:** Direct Bitcoin mainnet interaction without wrapping or bridging mechanisms that introduce counterparty risk.

**Smart Contract Logic:** Internet Computer provides the computational environment for complex stablecoin management while Bitcoin remains the settlement layer.

**Real-Time Oracles:** Price feeds and collateralization monitoring through Internet Computer's native HTTPS outcalls eliminate reliance on external oracle networks.

**Gasless Transactions:** Internet Computer's reverse gas model enables users to interact with Syron without holding additional tokens for transaction fees.

### Dual Token Standard Implementation

Syron SUSD launches with support for BRC-20 and Runes token standards, providing users comprehensive choice across the Bitcoin ecosystem:

**BRC-20 Format:**

- Established ecosystem with existing wallet and exchange support
- Proven infrastructure for Bitcoin-native token interactions
- Broader liquidity venue availability

**Runes Format:**

- More efficient UTXO-based model with lower transaction costs
- Future-oriented standard with enhanced technical capabilities
- Reduced blockchain bloat through improved data handling

This dual implementation demonstrates Syron's advanced architecture while maintaining Bitcoin as the sole collateral asset. Users can choose their preferred token standard based on intended use cases, wallet compatibility, and personal preferences.

## Syron SUSD: Implementation and Use Cases

### Minting Process

1. **Wallet Connection:** Users connect existing Bitcoin wallets to generate their unique Safety Deposit ₿ox address
2. **Bitcoin Deposit:** BTC is transferred to the user-controlled Safety Deposit ₿ox smart contract
3. **Collateral Verification:** Chain Fusion confirms deposit and calculates available minting capacity
4. **SUSD Generation:** Users mint up to 66% of collateral value in SUSD tokens (150% collateralization ratio)
5. **Token Selection:** Choose between BRC-20 or Runes formats

### Redemption and Collateral Management

**Loan Repayment:** Users repay SUSD loans to unlock their Bitcoin collateral. Repayment can be partial or complete, with collateral released proportionally.

**Collateral Addition:** Users can deposit additional Bitcoin to their Safety Deposit ₿ox to improve their collateralization ratio and mint additional SUSD.

**Liquidation Protection:** Automated liquidations when collateralization approaches dangerous levels. Manual collateral additions and repayments maintain position health.

### Real-World Applications

**Business Operations:** Bitcoin-holding companies can access working capital without selling their treasury reserves, maintaining long-term BTC exposure while funding operations.

**Personal Liquidity:** Individual holders can access cash for major purchases, emergencies, or investment opportunities without disrupting their Bitcoin accumulation strategies.

**DeFi Integration:** SUSD tokens can be used across Decentralized Finance protocols, enabling yield farming and liquidity provision while maintaining Bitcoin backing.

**Global Payments:** SUSD provides stable value transfer capabilities backed by Bitcoin's security and decentralization, ideal for international transactions and remittances.

## Current Deployment Status

Syron is currently live in testing on Bitcoin Layer 1 with core functionality operational:

**Available Features:**

- Safety Deposit ₿ox creation and Bitcoin collateral deposits
- SUSD minting in BRC-20 and Runes formats
- Secure redemption mechanisms for Bitcoin collateral recovery
- Gasless payment system via Internet Computer integration
- Cross-chain SUSD utility across Bitcoin and ICP ecosystems

**Ongoing Optimization:**

- Collateral management interface improvements
- Enhanced liquidation protection mechanisms
- Community governance mechanism integration

**Access:** Users can interact with Syron through the Tyron App, with technical guides and documentation available in the Components section.

## Future Development Roadmap

### Multi-Stablecoin Ecosystem

While SUSD represents Syron's initial implementation, the metaprotocol architecture supports multiple fiat-pegged stablecoins, all overcollateralized with Bitcoin:

**Planned Additions:**

- USDC borrowing options using the same Bitcoin collateral
- Regional stablecoin implementations for specific market needs
- Community-governed stablecoin proposals through DAO mechanisms

### Governance Evolution

**TyronDAO Governance:** The protocol will transition to community governance through TYRON token mechanisms, enabling stakeholder participation in:

- Collateralization ratio adjustments
- New stablecoin implementations
- Protocol upgrade proposals
- Risk parameter modifications

**Decentralized Autonomous Organization:** Full DAO implementation will distribute control among protocol users and TYRON token holders, ensuring long-term decentralization and community ownership.

## Conclusion

Syron addresses Bitcoin's fundamental liquidity challenge through innovative technical architecture that preserves the cryptocurrency's core value propositions. By combining Safety Deposit ₿ox smart contracts with Chain Fusion technology, the protocol enables Bitcoin holders to access dollar-denominated liquidity without sacrificing self-custody, censorship resistance, or long-term investment strategies.

The dual BRC-20 and Runes implementation ensures compatibility across Bitcoin's evolving ecosystem while the Internet Computer integration provides sophisticated smart contract capabilities without compromising Bitcoin's security model. Current mainnet deployment demonstrates the protocol's readiness for real-world usage, with ongoing optimizations preparing for broader adoption.

As Bitcoin continues its evolution from digital gold to global monetary infrastructure, protocols like Syron become essential for enabling the productive use of Bitcoin capital. By solving the liquidity paradox through self-custodial mechanisms, Syron represents a crucial step toward Bitcoin's full realization as the foundation of a new, more sovereign financial system.

The protocol invites Bitcoin holders, developers, and DeFi participants to explore this new paradigm of Bitcoin-native finance. Through community participation and continued development, Syron aims to establish the standard for self-custodial Bitcoin liquidity solutions in the emerging decentralized economy.
