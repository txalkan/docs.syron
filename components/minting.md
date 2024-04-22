# Minting

![](./syron_minting.png)

{% hint style="info" %}
**Good to know:** Minting is the process of withdrawing Syron U$ dollars according to the Tyron's stablecoin metaprotocol code.
{% endhint %}

Our innovative approach to Bitcoin-native stablecoins aims to empower users to unlock the potential of their BTC holdings in a self-sovereign identity (SSI) manner. In this context, SSI involves a decentralized identity paradigm where online data, such as digital money, is managed not in a centralized silo but using Distributed Ledger Technologies like Bitcoin and the Internet Computer. Additionally, in SSI, the subject of the identity, described by the digital identity, also serves as the controller, ensuring that no one else can claim control of the user’s funds.

On Tyron, this paradigm is realized through safety deposit boxes (SD₿), each independently holding the BTC collateral (one ₿ox per user). This setup ensures users maintain complete control over their assets without reliance on third parties.

## Syron Bitcoin Minter

The Syron minter is an Internet Computer canister with its own Pay-to-Witness-Public-Key-Hash (P2WPKH) Bitcoin address. This wallet holds Syron U$ dollars (SU$D) as BRC-20 [tokens](./token.md) corresponding to the premine amount.

The Syron minter is an Internet Computer canister with its own Pay-to-Witness-Public-Key-Hash (P2WPKH) Bitcoin address. This wallet holds Syron U$ dollars (SU$D) as BRC-20 .

The Syron stablecoin includes two ledgers: one to record BTC collateral and another one for SU$D balances, including the details about the dollars available for withdrawal.

### Safety Deposit ₿ox

Tyron computes the wallet address of the user's SD₿ with a P2WPKH script. To do so, it defines the user's Bitcoin wallet address as the SSI to include its value as part of the derivation path used in Chain Fusion's advanced cryptography, leveraging ICP's threshold ECDSA.

For user computations, the Syron Bitcoin Minter considers its main canister's ID and a subaccount that incorporates the user's wallet.

```rust
let ssi_box_subaccount: Subaccount = compute_subaccount(1, &args.ssi);
```

Here, 1 represents the nonce of the SD₿, and `&args.ssi` refers to the user's Bitcoin L1 wallet address.

This user's wallet address (SSI) is also appended at the end of the derivation path:

```rust
vec![
    ByteBuf::from(SCHEMA),
    ByteBuf::from(MINTER),
    ByteBuf::from(SUBACCOUNT),
    ByteBuf::from(SSI)
]
```

Once the user's SD₿ wallet is known, the next step is to make a BTC deposit.

### Using an SD₿

In principle, anyone can send a bitcoin transfer to an SD₿ in a permissionless manner. Security measures to prevent illicit activities can be implemented by utilizing the Know Your Transaction canister developed by DFINITY.

All deposited UTXOs into an SD₿ are tracked by the Syron Minter, which considers all their satoshis as the provided BTC collateral. Tyron's stablecoin metaprotocol is backed solely by BTC in an overcollateralized manner, ensuring that the collateral's value exceeds 1.5 times the amount of dollars users can withdraw from their SD₿s.

### Withdrawing SU$D

To withdraw SU$D, users request a balance update and provide the transaction ID of a transfer inscription submitted to Syron. This BRC-20 inscription is verified using the OPI Network.

Tyron utilizes the Internet Computer to record ledger balances of BTC deposits and SU$D balances. For Syron balances, several accounts come into place:

- Subaccount with nonce 1 for the bitcoin collateral and SU$D minting balance
- Subaccount with nonce 2 for dollars withdrawn as BRC-20 tokens

Additional subaccounts can be employed to account for withdrawals to other blockchain protocols like Bitcoin Runes and Ethereum. SU$D balances on ICP shall utilize the user's principal ID as the accounts' owner with no subaccount.

If this transaction fails, the ledger must reflect the unsuccessful withdrawal in the selected protocol. Consequently, users can request it again, and Syron validates the request by comparing the SU$D minting balance against the withdrawn dollars.
