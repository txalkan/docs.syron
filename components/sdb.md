# Safety Deposit ₿ox

The Safety Deposit ₿ox (SDB) is a user-owned smart contract wallet at the core of Syron's stablecoin metaprotocol. It securely holds Bitcoin (BTC) as collateral and facilitates key actions such as minting, burning, and liquidation of Syron stablecoins.

Each SDB operates autonomously and is both permissionless and trust-minimized. It functions as a native Bitcoin wallet, with a dedicated Bitcoin Layer 1 address, enabling users to verify their balances independently using any Bitcoin block explorer.

This deep integration with Bitcoin ensures full transparency, real-time visibility, and seamless interoperability with the broader Bitcoin ecosystem.

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
