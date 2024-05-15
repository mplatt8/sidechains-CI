# BitNames Testing Notes

## Functionality
- Deposit and Withdrawal to mainchain
- Transfer and receive on L2
- Name reservation
- Name registration
- Message encryption


## Commands
- balance
- bitnames
- connect-peer
- format-deposit-address
- generate-mnemonic
- get-block
- get-new-address
- get-blockcount
- get-paymail
- mine
- my-utxos
- reserve-bitname
- set-seed-from-mnemonic
- sidechain-wealth
- stop
- transfer
- withdraw
- help

## General Notes
- Should automatically pull key from L1 in respect to the sidechain slot. Ex. Slot 2 would restore L2 wallet by default from m/44'/0'/2' (hardened)
- Advanced mode would allow for set seed and passphrase
- Get BitName hex button
- GUI should display error messages, not just the console. For already registered names and double spent utxos
- Could there be a way to make the mining more efficient in a testing environment? (Manually set the hash target?)
- Clarification for address formatting. Probably should be taken care of under the hood
- Stop is not stopping the node

### balance
- Verify initial balance is zero.
- Check balance after a deposit.
- Ensure balance decreases after a withdrawal and increases after deposit.
- Verify balance after multiple transactions.
- Check balance updates correctly with concurrent transactions.

### bitnames
- List all reserved BitNames.
- Check list behavior when no BitNames are reserved.
- Ensure accurate listing with a large number of BitNames.

### connect-peer
- Connect to a valid peer and verify connection status.
- Disconnect from a peer and verify behavior.
- Test to connect to an invalid peer.
- Test behavior when maximum peer connections are reached.*
- Test connecting to the same peer multiple times.

### format-deposit-address
- Format a valid address correctly.
- Verify address format matches expected criteria.
- Test invalid address inputs.

### generate-mnemonic
- Generate a mnemonic seed phrase and verify its validity.
- Ensure each generation produces a unique mnemonic.
- Test different lengths of mnemonics.
- Verify consistent generation under repeated calls.

### get-block
- Retrieve block data for a specific block and verify contents.
- Request non-existent blocks and verify behavior.
- Retrieve the genesis block and the latest block.
- Ensure proper error handling for invalid block requests.

### get-new-address
- Generate new addresses and verify their format.
- Ensure uniqueness of each generated address.
- Generate a large number of addresses to check for duplicates.
- Verify address generation under repeated calls.

### get-blockcount
- Retrieve the current block count and verify accuracy.
- Check block count updates after mining new blocks.
- Verify behavior with an initially empty blockchain.
- Test with very high block counts.

### get-paymail
- Retrieve all paymail addresses and verify correctness.
- Test behavior with no paymail addresses.
- Verify retrieval with a large list of paymail addresses.
- Check paymail address format and uniqueness.

### mine
- Successfully mine a sidechain block and verify the process.
- Ensure the mined block contents are correct and valid.
- Test mining with multiple miners simultaneously.
- Verify block rewards and transaction inclusion.

### my-utxos
- List all owned UTXOs and verify details (amount and txid).
- Check behavior with no UTXOs owned.
- Verify correctness with a large number of UTXOs.
- Ensure spent UTXOs are not listed.

### reserve-bitname
- Successfully reserve a new BitName and verify reservation.
- Test reserving BitNames with invalid characters.
- Verify behavior with very short and very long BitNames.

### set-seed-from-mnemonic
- Set the wallet seed from a valid mnemonic seed phrase.
- Ensure the wallet state is initialized correctly from the seed.
- Test to set seed with an invalid mnemonic.
- Test behavior with incomplete or partial mnemonics.

### sidechain-wealth
- Retrieve total sidechain wealth and verify the amount.
- Check wealth updates before and after transactions.
- Verify behavior with no transactions affecting wealth.
- Test with a high volume of transactions.

### stop
- Stop the node and verify it shuts down correctly.
- Test to stop the node during high activity.
- Issue multiple stop commands simultaneously and verify behavior.

### transfer
- Successfully transfer funds to a specified address.
- Verify the transfer is reflected in both sender and receiver balances.
- Test to transfer to an invalid address.
- Test transferring more than the available balance.
- Test with a large number of transfers in quick succession.

### withdraw
- Initiate a withdrawal to the mainchain and verify the process.
- Ensure the withdrawal is processed and reflected on the mainchain.
- Test to withdraw to an invalid address.
- Test withdrawing more than the sidechain balance.
- Test multiple withdrawals simultaneously.

### help
- Print the help message and ensure all commands are listed.
