# SSI Vault

Syron's SU$D stablecoin is generated within a user-owned SSI Vault. This smart account takes care of safely holding the collateral and it serves as the home for the stablecoin redemption and liquidation code. These vaults independently track user balances in a permissionless manner.

For more detailed design information, refer to [Bitcoin-Native Assets](../introduction/design-principles.md#bitcoin-native-assets).

<!-- On Bison, minter SSI accounts (MISAs) are identified as smart contracts with the special `MINTER_ROLE` granted by the Access Control system. This allows for tailored U$D minting functionality per MISA.

```
uint256 private _vaultSupply;
mapping(address account => uint256) private _vaults;
```

{% hint style="info" %}
**Good to know:** MISAs, being minter SSI accounts, may operate without an SSI controller, governed solely by the code. However, an admin role as an SSI controller can be beneficial in certain scenarios for administering context parameters.
{% endhint %} -->

## Oracles

For an SSI Vault to function properly a reliable source of truth is essential. Syron will obtain these information from multiple off-chain data points.

Information can also originate from on-chain data, such as decentralized exchanges and DeFi applications. In this scenario, layer-2 vaults could read the required data at the time of the transaction in an atomic manner.
