# Token

The Syron Dollar (SUSD) is a stablecoin crafted as a digital fungible token, seamlessly usable on the Bitcoin network, Internet Computer, and other platforms.

{% hint style="info" %}
**What is a fungible token?**

A fungible token is interchangeable with others of the same type and value. Each unit is identical and can be traded on a one-to-one basis. Fungible tokens are divisible and lack uniqueness, making them uniform and easily exchangeable, like money.
{% endhint %}

The fungible token infrastructure is a crucial aspect of the stablecoin protocol's core design. It's designed to operate seamlessly on Bitcoin and other blockchain protocols, offering improved scalability and accessibility.

Tyron's Bitcoin-native stablecoins are premined and transferred to a Syron Bitcoin Minter (SBM). The balance of the SBM must not be considered in the circulating supply.

## BRC-20

As a Bitcoin-native asset, Syron's first implementation adheres to the [BRC-20 standard](https://layer1.gitbook.io/layer1-foundation/protocols/brc-20) for holding and transferability, and it can be done using 4- or 5-byte tokens.

This fungible token type is based on the Ordinals protocol and thus requires inscriptions.

When making a BTC deposit into a Safety Deposit ₿ox, an inscribe-transfer UTXO shall be sent to the Syron Minter wallet. When the withdrawal of dollars occurs, this inscribe-transfer UTXO is sent to the user's Bitcoin wallet.

```javascript
const inscription: InscribeData = await api.createTransfer({
  receiveAddress: syron_minter,
  feeRate,
  satoshis: 546,
  depositAddress: sdb,
  deposit: collateral,
  brc20Ticker: SYRON,
  brc20Amount: amt,
});

await api.sendBitcoin(inscription);
```

At the time of withdrawal, the Syron Minter uses the above inscribe-transfer UTXO to send the SYRON dollars to the user's wallet.

<!-- {% embed url="https://5ccbc373887ca40020446347-geedzbiswp.chromatic.com/iframe.html?id=icon--labels&args=&viewMode=story" %}
These examples are taken from the excellent [Storybook Example Design System](https://5ccbc373887ca40020446347-geedzbiswp.chromatic.com/?path=/story/icon--labels).
{% endembed %} -->
