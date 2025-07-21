> **TL;DR**  
> Minting Syron stablecoins enables users to unlock the value of their BTC by depositing it as collateral in a Safety Deposit ₿ox. The process is decentralized, over-collateralized, and managed via the Internet Computer, ensuring users retain full control of their assets.

# Minting

{% hint style="info" %}
Minting is the process of withdrawing Syron stablecoins according to Tyron's stablecoin protocol.
{% endhint %}

Tyron's innovative approach to Bitcoin-native stablecoins empowers users to unlock the potential of their BTC holdings through a Self-Sovereign Identity (SSI) solution. In the context of Syron, SSI involves a decentralized identity paradigm where online data, such as digital money, is managed not in centralized silos but through distributed ledger technologies like Bitcoin and the Internet Computer. Additionally, with SSI, the subject of the identity also serves as the controller, ensuring that no one else can claim control of the user’s funds.

On Syron, this paradigm is realized through Safety Deposit Boxes, each independently holding a user's BTC collateral (one ₿ox per user). This setup ensures everyone maintains complete control over their assets without reliance on third parties.

![](./syron_minting.png)

## Syron Minter

The Syron minter is a smart contract system first implemented on the Internet Computer through a collection of canisters. The system has its own Pay-to-Witness-Public-Key-Hash (P2WPKH) Bitcoin addresses. These wallets hold Syron stablecoins, one per [token](./token.md) standard, such as BRC-20 and Runes. Syron stablecoins on Bitcoin must be fully premined, and the Tyron Mapu Community Interest Company distributes the tokens across the minters. Both the CIC's wallet balance and the minters' wallet balances must not be considered as part of the circulating supply of Syron stablecoins.

A Syron stablecoin includes two ledgers: one to record BTC collateral and another for the stablecoin balances, including details about loans, balances, and withdrawals.

### Depositing BTC in Safety Deposit ₿ox

A Safety Deposit ₿ox (SDB) is essential to the minting process, serving as the user-owned smart contract wallet that securely holds BTC collateral. The SDB ensures users maintain full control and transparency over their assets throughout the minting process. For a detailed explanation of how SDBs work, see the [Safety Deposit ₿ox documentation](./sdb.md).

In principle, anyone can send a BTC transfer to an SDB in a permissionless manner. Security measures to prevent illicit activities can be implemented by utilizing the Know Your Transaction canister developed by DFINITY.

All deposited UTXOs into an SDB are tracked on the Syron ledgers by considering all satoshis as the provided BTC collateral. Tyron's stablecoin protocol is backed solely by BTC in an over-collateralized manner, ensuring that the collateral's value is at least 1.5 times the amount of Syron stablecoins users can mint in their SDB.

### Minting Syron

To mint Syron stablecoins, users request a balance update that computes a new loan based on their BTC collateral.

To withdraw Syron SUSD as SYRON BRC-20, the user must provide the ID of an inscribe-transfer transaction submitted on Bitcoin. This BRC-20 inscription is verified using Ordinals indexers.

As mentioned in the Syron minter section, Tyron utilizes the Internet Computer to record the amount of BTC deposits and Syron balances per user. In these ledgers, several accounts come into play:

- Subaccount with nonce 1 for the Bitcoin collateral and Syron borrowed in return (loan).
- Subaccount with nonce 2 for dollars available for withdrawal (Syron balance), nonce 3 for Syron stablecoins withdrawn as BRC-20 tokens, and nonce 4 for withdrawals as Rune tokens.

Additional subaccounts can be employed to account for withdrawals to other blockchain protocols like Ethereum. TyronDAO's ledgers on ICP utilize the Syron minter's main principal ID as the accounts' owner, with subaccounts made out of the user's Bitcoin self-custodial wallet and a specific nonce, as mentioned above and in the SDB documentation.

If a transaction fails, the ledger must record the unsuccessful withdrawal in the appropriate ledger. Consequently, users can request it again, and the protocol validates the request by referring to the relevant subaccounts.

{% embed url="https://www.youtube.com/watch?v=-1sWY0-h4ZY" %}
