# Safety Deposit ₿ox

Syron's stablecoin management occurs within a user-owned Safety Deposit ₿ox (SDB). This smart contract wallet securely holds the collateral and serves as the hub for stablecoin minting, burning, and liquidation transactions.

An SDB autonomously track its user balance in a permissionless and trustless manner and is a Bitcoin-native wallet. Each SDB has its own Layer-1 address, allowing users to monitor their holdings at any time using their preferred Bitcoin block explorer. This native integration with Bitcoin ensures seamless interaction with the Bitcoin ecosystem.

For more detailed design information, refer to [Bitcoin-Native Assets](../introduction/design-principles.md#bitcoin-native-assets).

<!-- Minter SSI accounts (MISAs) are identified as smart contracts with the special `MINTER_ROLE` granted by the Access Control system. This allows for tailored minting functionality per MISA.

```
uint256 private _vaultSupply;
mapping(address account => uint256) private _vaults;
```

{% hint style="info" %}
**Good to know:** MISAs, being minter SSI accounts, may operate without an SSI controller, governed solely by the code. However, an admin role as an SSI controller can be beneficial in certain scenarios for administering context parameters.
{% endhint %} -->

## Oracles

To ensure the stability of the stablecoin, Syron relies on accurate data sourced from multiple off-chain data points managed by the ICP's [Exchange Rate Canister](https://wiki.internetcomputer.org/wiki/Exchange_rate_canister). Additionally, on-chain data from decentralized exchanges and DeFi applications can contribute to price discovery. A Safety Deposit ₿ox could efficiently access this on-chain data at the time of the transaction, guaranteeing that the information used for stablecoin operations is up-to-date and reliable.
