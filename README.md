# Anchor Example: Escrow Program

## Overview

Instead of letting initializer create a token account to be reset to a PDA authority, we create a token account `Vault` that has both a PDA key and a PDA authority.

### Initialize

`Initializer` can send a transaction to the escrow program to initialize the Vault. In this transaction, two new accounts: `Vault` and `EscrowAccount`, will be created and tokens (Token A) to be exchanged will be transfered from `Initializer` to `Vault`.

### Cancel

`Initializer` can also send a transaction to the escrow program to cancel the demand of escrow. The tokens will be transfered back to the `Initialzer` and both `Vault` and `EscrowAccount` will be closed in this case.

### Exchange

`Taker` can send a transaction to the escrow to exchange Token B for Token A. First, tokens (Token B) will be transfered from `Taker` to `Initializer`. Afterward, the tokens (Token A) kept in the Vault will be transfered to `Taker`. Finally, both `Vault` and `EscrowAccount` will be closed.

## Build, Deploy and Test

Let's run the test once to see what happens.

Deploying a Staking Contract to Mainnet or devnet Using anchor.

1. git clone https://github.com/RashidInvo/Ft-escrow.git 

2. open terminal and goto project folder and run yarn for adding node_modules.

3.  run anchor build

4. run solana address -k ./target/deploy/anchor_escrow-keypair.json and you will get your program address.

5. replace that address in anchor.toml and lib.rs files.

6. run anchor test command it will build your program with new declare id as well as deploy the smart contract on devnet and after that will run test cases. You can also run only test cases by running anchor test --skip-build --skip-deploy. 

