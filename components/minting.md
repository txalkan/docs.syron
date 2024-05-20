# Minting

{% hint style="info" %}
**Good to know:** Minting is the process of withdrawing Syron US dollars according to the Syron stablecoin meta-protocol.
{% endhint %}

Our innovative approach to Bitcoin-native stablecoins aims to empower users to unlock the potential of their BTC holdings in a self-sovereign identity (SSI) manner. In this context, SSI involves a decentralized identity paradigm where online data, such as digital money, is managed not in a centralized silo but using Distributed Ledger Technologies like Bitcoin and the Internet Computer. Additionally, in SSI, the subject of the identity, described by the digital identity, also serves as the controller, ensuring that no one else can claim control of the user’s funds.

On Tyron, this paradigm is realized through safety deposit boxes (SD₿), each independently holding the BTC collateral (one ₿ox per user). This setup ensures users maintain complete control over their assets without reliance on third parties.

![](./syron_minting.png)

## Syron Bitcoin Minter

The Syron minter is an Internet Computer canister with its own Pay-to-Witness-Public-Key-Hash (P2WPKH) Bitcoin address. This wallet holds Syron US dollars (SUSD) as BRC-20 [tokens](./token.md) corresponding to the premine amount.

The Syron stablecoin includes two ledgers: one to record BTC collateral and another one for SUSD balances, including the details about the dollars available for withdrawal.

### Safety Deposit ₿ox

Tyron computes the wallet address of the user's SD₿ with a P2WPKH script. To do so, it defines the user's Bitcoin wallet address as the SSI to include its value as part of the derivation path used in Chain Fusion's advanced cryptography, leveraging ICP's threshold ECDSA.

For user computations, the meta-protocol considers the minter canister's ID and a subaccount that incorporates the user's wallet.

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

All deposited UTXOs into an SD₿ are tracked on ICP by considering all satoshis as the provided BTC collateral. Tyron's stablecoin meta-protocol is backed solely by BTC in an over-collateralized manner, ensuring that the collateral's value exceeds 1.5 times the amount of dollars users can withdraw from their SD₿s.

### Withdrawing Syron

To withdraw SUSD, users request a balance update and provide the transaction ID of a transfer inscription submitted on Bitcoin. This BRC-20 inscription is verified using Ordinals indexers.

TyronDAO utilizes the Internet Computer to record ledger balances of BTC deposits and SUSD balances. In these Syron ledgers, several accounts come into place:

- Subaccount with nonce 1 for the bitcoin collateral and SUSD loan balance
- Subaccount with nonce 2 for dollars pending withdrawal and nonce 3 for SUSD withdrawn as BRC-20 tokens

Additional subaccounts can be employed to account for withdrawals to other blockchain protocols like Bitcoin Runes and Ethereum. Syron ledgers on ICP utilize the minter's principal ID as the accounts' owner with subaccounts made out of the user's Bitcoin wallet and a specific nonce - as mentioned above.

If this transaction fails, the ledger must reflect the unsuccessful withdrawal in the selected protocol. Consequently, users can request it again, and the meta-protocol validates the request by referring to subaccount 2 of pending Syron withdrawals.
