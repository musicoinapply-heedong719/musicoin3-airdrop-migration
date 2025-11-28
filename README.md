Musicoin3 Airdrop Migration

Overview
Musicoin 3.0 aims to relaunch the ecosystem on Polygon while preserving the legacy of existing Musicoin holders. This repository defines the full technical and operational framework for executing an on‑chain airdrop distribution to legacy wallets, enabling a smooth migration into the new Musicoin 3.0 token economy.

Purpose
- Verify historical Musicoin addresses
- Map legacy balances to new Polygon-based token allocations
- Provide transparent airdrop logic
- Offer scripts, smart contracts, and CSV processing tools for automated migration

Components
1. Legacy Wallet Scanner

1. Tools for scanning Musicoin Classic chain snapshots and exporting wallet/balance data.

2. Balance Mapping Engine

2. Converts legacy balances into Musicoin 3.0 allocation amounts based on defined rules.

3. Airdrop Smart Contract (Polygon)

3. Contract responsible for claim-based or direct airdrop distribution.

4. Verification Dashboard

1. Optional front-end that allows users to check their eligibility and allocation.

How It Works
1. Export historical snapshot of Musicoin addresses
2. Generate a clean CSV of all eligible wallets
3. Deploy the airdrop contract on Polygon
4. Run the allocation engine to populate the contract
5. Users receive tokens automatically or claim manually depending on chosen design

Folder Structure
/contracts
/scripts
/snapshot-tools
/allocation-engine
/docs


License
MIT License
