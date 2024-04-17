# Safety Deposit Box

Tyron's SU$D stablecoin management occurs within user-owned safety deposit boxes. These smart accounts securely hold the collateral and serve as the hub for stablecoin minting, burning, and liquidation transactions. These safety deposit boxes autonomously track user balances in a permissionless manner and are Bitcoin-native, each possessing its own layer-1 address.

For more detailed design information, refer to [Bitcoin-Native Assets](../introduction/design-principles.md#bitcoin-native-assets).

<!-- Minter SSI accounts (MISAs) are identified as smart contracts with the special `MINTER_ROLE` granted by the Access Control system. This allows for tailored U$D minting functionality per MISA.

```
uint256 private _vaultSupply;
mapping(address account => uint256) private _vaults;
```

{% hint style="info" %}
**Good to know:** MISAs, being minter SSI accounts, may operate without an SSI controller, governed solely by the code. However, an admin role as an SSI controller can be beneficial in certain scenarios for administering context parameters.
{% endhint %} -->

## Oracles

To ensure the stability of the stablecoin, Syron relies on accurate data sourced from multiple off-chain data points managed by the ICP's [Exchange Rate Canister](https://wiki.internetcomputer.org/wiki/Exchange_rate_canister). Additionally, on-chain data from decentralized exchanges and DeFi applications can contribute to price discovery. Safety deposit boxes can efficiently access this on-chain data at the time of the transaction, guaranteeing that the information used for stablecoin operations is up-to-date and reliable.
