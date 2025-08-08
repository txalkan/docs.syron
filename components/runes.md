# Deposit Syron Runes Function Summary

## Overview

The `deposit_syron_runes` function is an async function that handles the deposit of Syron runes into the system. It processes UTXOs containing runes, validates deposits, and manages the transfer of runes to the minter while updating user balances.

## Function Signature

```rust
async fn deposit_syron_runes(args: GetBoxAddressArgs, fee: u64) -> Result<Vec<UtxoStatus>, UpdateBalanceError>
```

## Parameters

- `args: GetBoxAddressArgs` - Contains the SSI (Self-Sovereign Identity) and operation type
- `fee: u64` - Fee amount for the transaction

## Key Functionality

### 1. Operation Validation

- Verifies that `args.op` equals `SyronOperation::DepositSyron`
- Returns an error if the operation is invalid

### 2. Account Setup

- Calls `setup_ssi_account_and_guard()` to initialize the user's account and activate balance guard
- Retrieves the Safety Deposit Box (SDB) address using `get_box_address()`

### 3. Network and Fee Configuration

- Fetches Bitcoin network configuration
- Sets fee per byte based on the network
- Defines constants:
  - `cycles_cost`: 72,000,000
  - `provider_id`: 0
  - `treasury_fee`: 546 satoshis
  - `stable_deposit`: 10,000,000 (0.1 syron)

### 4. UTXO Processing

- Retrieves all UTXOs from the SDB address
- Filters for new UTXOs only (excludes previously used collateral)
- Iterates through UTXOs to categorize them:
  - **Sats UTXOs**: UTXOs with 0 runes balance
  - **Runes UTXOs**: UTXOs containing runes
- Calculates total runes deposit amount

### 5. Validation Checks

- **No Runes Check**: If `runes_deposit == 0`, returns `NoNewUtxos` error with pending UTXOs
- **Minimum Deposit**: Ensures runes deposit is at least `stable_deposit` (0.1 syron)
- **Sufficient Funds**: Validates that BTC deposit + runes sats can cover treasury fee + outputs value (660 satoshis)

### 6. Balance Management

- Deducts `stable_deposit` from total runes deposit
- Credits runes deposit to user's pending balance (nonce 5) using `syron_runes_deposit()`
- Handles errors by reverting the credit if needed

### 7. Runes Transfer

- Sends runes back to the minter (burn operation) using `burn_p2wpkh_runes()`
- If transfer fails:
  - Reverts the pending balance credit
  - Returns a `GenericError` with error code 904

### 8. Final Balance Update

- Calls `update_ssi_balance()` to move pending balance to available balance
- Returns the result as `Vec<UtxoStatus>`

## Error Handling

The function handles various error scenarios:

- Invalid operation type
- Insufficient runes deposit
- Insufficient funds for fees and outputs
- Failed runes transfer to minter
- Account setup failures

## Key Dependencies

- `bitcoin_wallet::burn_p2wpkh_runes()` - For burning runes
- `update_balance::syron_runes_deposit()` - For managing runes deposits
- `update_balance::update_ssi_balance()` - For final balance updates
- `management::get_utxos()` - For retrieving UTXOs
- `https::outcall::call_indexer_runes_balance()` - For checking runes balance

## Return Value

Returns `Result<Vec<UtxoStatus>, UpdateBalanceError>` where:

- `Ok(Vec<UtxoStatus>)` - Successfully processed UTXOs
- `Err(UpdateBalanceError)` - Various error conditions

## Notes

- The function implements a two-phase commit pattern for runes deposits
- It maintains atomicity by reverting pending balances on failures
- Uses nonce 5 for pending runes deposits and nonce 2 for available balances
- Includes comprehensive logging for debugging and monitoring

## Backend Code

The complete implementation can be found at: [https://github.com/txalkan/tyron-icp/blob/48fbabcafc5a3b545f9ae65fc1efe0ef77ec179a/src/basic_bitcoin/src/lib.rs#L933](https://github.com/txalkan/tyron-icp/blob/48fbabcafc5a3b545f9ae65fc1efe0ef77ec179a/src/basic_bitcoin/src/lib.rs#L933)

## Runes Minter Address

The runes minter address where runes are sent for burning: [bc1qhtux6m8zptg0qtcml8nap7te90epqmu8sag3du](https://mempool.space/address/bc1qhtux6m8zptg0qtcml8nap7te90epqmu8sag3du)

This address receives runes from the Safety Deposit Box (SDB), effectively burning them after the deposit process by calling `redeem_btc`.
