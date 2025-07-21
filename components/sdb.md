> **TL;DR**  
> A Safety Deposit ₿ox (SDB) is a user-owned smart contract wallet at the core of Tyron's stablecoin protocol. It securely holds Bitcoin (BTC) as collateral and enables minting, burning, and liquidation of Syron stablecoins. Each SDB is fully transparent, permissionless, and integrated with the Bitcoin network for real-time verification and interoperability.

# Safety Deposit ₿ox

A Safety Deposit ₿ox (SDB) is a smart contract wallet on the Syron protocol, uniquely linked to a user's self-custodial Bitcoin address. It securely holds Bitcoin (BTC) as collateral and enables minting, burning, and liquidation of Syron stablecoins. Each SDB is fully transparent, permissionless, and integrated with the Bitcoin network for real-time verification and interoperability.

## How it Works

An SDB's address is generated using a method called P2WPKH (Pay-to-Witness-Public-Key-Hash). This process uses the user's existing Bitcoin address as a Self-Sovereign Identity (SSI) to create a unique derivation path.

This is achieved through Chain Fusion's advanced chain-key cryptography, which leverages the Internet Computer's threshold ECDSA capabilities.

**The key components in this process are:**

- **SSI:** The user's self-custodial Bitcoin wallet address.
- **Nonce:** A unique number for the SDB (e.g., 1).
- **Derivation Path:** A unique path created by combining the schema, minter, subaccount, and the user's SSI.

Once the SDB wallet address is computed, the user can deposit BTC directly into it on Bitcoin Mainnet.

Every SDB operates autonomously and is both permissionless and trust-minimized. It functions as a native Bitcoin wallet, with a dedicated Bitcoin Layer 1 address, enabling users to verify their balances independently using any Bitcoin block explorer.

For user computations, the Syron protocol considers the minter's main canister ID and a subaccount that incorporates the user's SSI.

```rust
let sdb_subaccount: Subaccount = compute_subaccount(1, &args.ssi);
```

Here, 1 represents the nonce of the SDB, and `&args.ssi` refers to the user's Bitcoin self-custodial wallet address.

This user's SSI is also appended at the end of the derivation path:

```rust
vec![
    ByteBuf::from(SCHEMA),
    ByteBuf::from(MINTER),
    ByteBuf::from(SUBACCOUNT),
    ByteBuf::from(SSI)
]
```

Syron's deep integration with Bitcoin ensures full transparency, real-time visibility, and seamless interoperability with the broader Bitcoin ecosystem.

![](./syron_sdb.png)

> _Interface: Safety Deposit ₿ox structure and interactions on the TyronDAO dApp_

<!-- Minter SSI accounts (MISAs) are identified as smart contracts with the special `MINTER_ROLE` granted by the Access Control system. This allows for tailored minting functionality per MISA.

```
uint256 private _vaultSupply;
mapping(address account => uint256) private _vaults;
```

{% hint style="info" %}
**Good to know:** MISAs, being minter SSI accounts, may operate without an SSI controller, governed solely by the code. However, an admin role as an SSI controller can be beneficial in certain scenarios for administering context parameters.
{% endhint %} -->

## Oracles

To ensure the stability of the stablecoins, Syron relies on accurate data sourced from multiple off-chain data points managed by the Internet Computer's [Exchange Rate Canister](https://wiki.internetcomputer.org/wiki/Exchange_rate_canister). Additionally, on-chain data from decentralized exchanges and DeFi applications can contribute to price discovery. A Safety Deposit ₿ox could efficiently access this on-chain data at the time of the transaction, guaranteeing that the information used for stablecoin operations is up-to-date and reliable.
