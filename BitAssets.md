# BitAssets Testing Notes

## Functionality
- Asset management (minting, burning, swapping)
- Dutch auctions
- UTXO management

## Commands
- amm-burn
- amm-mint
- amm-swap
- bitassets
- bitcoin-balance
- connect-peer
- dutch-auction-bid
- dutch-auction-create
- dutch-auction-collect
- dutch-auctions
- format-deposit-address
- generate-mnemonic
- get-amm-pool-state
- get-amm-price
- get-block
- get-block-hash
- get-blockcount
- get-new-address
- mine
- my-unconfirmed-utxos
- my-utxos
- reserve-bitasset
- set-seed-from-mnemonic
- sidechain-wealth
- stop
- transfer
- withdraw
- help

## General Notes
- Notes about the general behavior and specific observations.

### Testing and Edge Cases

#### AMM Operations
- **amm-burn**: 
  - Burn an AMM position and verify holdings reduction.
  - Burn a position with the minimum amount.
  - Attempt to burn a non-existent position.
  - Burn with insufficient funds.

- **amm-mint**: 
  - Mint a new AMM position and verify addition to holdings.
  - Mint with the minimum amount.
  - Attempt to mint a position with invalid parameters.
  - Mint with the maximum allowed amount.

- **amm-swap**: 
  - Swap assets in the AMM and verify the received amount.
  - Swap with the minimum amount.
  - Attempt to swap with insufficient funds.
  - Swap under extreme market conditions.

#### Asset Listings and Balances
- **bitassets**: 
  - List all BitAssets and verify the list accuracy.
  - List with no BitAssets.
  - List with a large number of BitAssets.
  - List with filters (if applicable).

- **bitcoin-balance**: 
  - Get Bitcoin balance and verify the amount.
  - Check with zero balance.
  - Verify with multiple transactions affecting the balance.

#### Peer Connections
- **connect-peer**: 
  - Connect to a valid peer and verify connection.
  - Attempt to connect to an invalid peer.
  - Connect when the maximum number of peers is reached.
  - Connect to the same peer multiple times.

#### Dutch Auctions
- **dutch-auction-bid**: 
  - Place a bid in a Dutch auction and verify the outcome.
  - Bid with the minimum amount.
  - Attempt to bid with insufficient funds.
  - Bid in a non-existent auction.

- **dutch-auction-create**: 
  - Create a Dutch auction and verify its creation.
  - Create an auction with invalid parameters.
  - Create multiple auctions in quick succession.

- **dutch-auction-collect**: 
  - Collect assets from a Dutch auction and verify the received amount.
  - Collect from an auction with the minimum assets.
  - Attempt to collect from a non-existent auction.
  - Collect when auction parameters are extreme.

- **dutch-auctions**: 
  - List all Dutch auctions and verify the list accuracy.
  - List with no Dutch auctions.
  - List with a large number of Dutch auctions.
  - List with filters (if applicable).

#### Address and Mnemonic Handling
- **format-deposit-address**: 
  - Format a deposit address and verify correctness.
  - Provide invalid input for formatting.
  - Test addresses with unusual but valid formats.

- **generate-mnemonic**: 
  - Generate a mnemonic seed phrase and verify its validity.
  - Generate mnemonic of different lengths (12, 18, 24 words).
  - Ensure uniqueness of multiple generations.

#### AMM Pool State and Price
- **get-amm-pool-state**: 
  - Retrieve the state of the specified AMM pool and verify details.
  - Request the state of a non-existent pool.
  - Verify state under extreme conditions.

- **get-amm-price**: 
  - Get the current price for a specified pair and verify accuracy.
  - Request price for a non-existent pair.
  - Verify price under extreme market conditions.

#### Blockchain Operations
- **get-block**: 
  - Retrieve block data and verify contents.
  - Request non-existent blocks.
  - Retrieve the genesis and latest block.

- **get-block-hash**: 
  - Get the hash of the block at a specified height.
  - Request hash for a non-existent block height.
  - Verify hash for boundary block heights.

- **get-blockcount**: 
  - Retrieve the current block count and verify accuracy.
  - Check block count when no blocks are mined.
  - Verify block count after mining new blocks.

#### Address and Transaction Handling
- **get-new-address**: 
  - Generate a new address and verify its format.
  - Generate a large number of addresses.
  - Check for duplicates over multiple generations.

#### Mining
- **mine**: 
  - Attempt to mine a sidechain block and verify the process.
  - Mine with insufficient computational resources.
  - Concurrent mining attempts.

#### UTXO Management
- **my-unconfirmed-utxos**: 
  - List unconfirmed owned UTXOs and verify details.
  - List with no unconfirmed UTXOs.
  - Verify a large number of unconfirmed UTXOs.

- **my-utxos**: 
  - List owned UTXOs and verify details.
  - List with no UTXOs.
  - Verify a large number of UTXOs.

#### Asset Reservation
- **reserve-bitasset**: 
  - Reserve a BitAsset and verify the reservation.
  - Attempt to reserve a duplicate BitAsset.
  - Reserve with invalid parameters.

#### Wallet Seed Management
- **set-seed-from-mnemonic**: 
  - Set the wallet seed from a mnemonic seed phrase and verify wallet state.
  - Use an invalid or incomplete mnemonic.

#### Sidechain Wealth
- **sidechain-wealth**: 
  - Retrieve total sidechain wealth and verify the amount.
  - Check wealth with no transactions.
  - Verify wealth with high transaction volume.

#### Node Operations
- **stop**: 
  - Stop the node and verify shutdown.
  - Stop node during high activity.
  - Issue multiple stop commands.

#### Fund Transfer
- **transfer**: 
  - Transfer funds to a specified address and verify the transaction.
  - Transfer to invalid addresses.
  - Attempt to transfer more than the available balance.

#### Withdrawal
- **withdraw**: 
  - Initiate a withdrawal to the mainchain and verify the process.
  - Withdraw to invalid mainchain addresses.
  - Attempt to withdraw more than the sidechain balance.

#### Help Command
- **help**: 
  - Print the help message and ensure all commands are listed.
  - Request help for non-existent subcommands.
  - Verify subcommand help messages.

## GUI Panels
- **Deposit/Withdrawal Panel**:
  - Verify fields for amount, fee, mainchain address, and generate buttons.
  - Test deposit and withdrawal functionality.
  - Deposit with invalid amounts or addresses.
  - Withdrawal with invalid mainchain addresses or insufficient funds.

- **Transfer/Receive Panel**:
  - Verify fields for destination address, amount, fee, and generate button for receiving address.
  - Test transfer and receive functionality.
  - Transfer with invalid destination addresses.
  - Receive functionality with edge case addresses.

- **Transaction Builder Panel**:
  - Verify UTXO selection, value in, and value out fields.
  - Test transaction construction.
  - Construct transactions with invalid UTXOs or amounts.
  - Verify behavior with zero or extreme value UTXOs.

- **My BitAssets Panel**:
  - Verify reservation and registration fields for BitAssets.
  - Test asset reservation and registration.
  - Reserve and register assets with invalid parameters.
  - Verify behavior with duplicate asset names or addresses.
