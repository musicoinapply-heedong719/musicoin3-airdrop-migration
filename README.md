# Musicoin3 Airdrop Migration

## Overview
Musicoin 3.0 relaunches the ecosystem on Polygon while preserving the historical rights of all legacy Musicoin holders.  
This repository documents the complete workflow for extracting balances from **two different old chains**, merging them, and generating a unified airdrop allocation for the new Polygon-based Musicoin 3.0 token.

The migration requires:
1. Balance extraction from the **original Musicoin blockchain (Ethereum Classic fork)**  
2. Balance extraction from the **later ERC-20 Musicoin token on Ethereum**  
3. Using **specific block heights** in both chains to ensure fairness  
4. Producing a clean and verified dataset for the Polygon airdrop contract

---

## Purpose
- Retrieve historical Musicoin addresses and balances from the legacy ETC-fork chain  
- Retrieve all addresses and balances from the ERC-20 Musicoin token contract  
- Snapshot both datasets at **specific block heights**  
- Merge, deduplicate, and validate all unique holders  
- Generate the final airdrop allocation file for Polygon  
- Provide transparent, reproducible migration logic

---

## Snapshot Requirements

### 1. Legacy Musicoin Chain (ETC Fork)
A full-node snapshot is required at a specific historical block height.

The repository includes:
- Tools to scan `go-musicoin` chain data  
- Exporter scripts to extract all wallets and balances  
- Configuration to specify **exact block height** for snapshot consistency  

Output format:  
```
address,balance_legacy
```

### 2. Ethereum ERC‑20 Musicoin Token
A second dataset must be created using the ERC-20 Musicoin smart contract on Ethereum.

The repository includes:
- Scripts for reading token balances directly from an archive Ethereum node  
- Configuration for **ERC‑20 snapshot block number**  
- Automatic paging through all token holders via `eth_getLogs` and balance checks  

Output format:  
```
address,balance_erc20
```

---

## Balance Merge Logic
After collecting both datasets:

1. Normalize addresses  
2. Convert both balances to unified decimal units  
3. Merge into a single holder set  
4. For any address appearing in both chains, balances are summed  
5. Final output file is generated:

```
address,final_allocation
```

This file becomes the source for the Polygon airdrop contract.

---

## Airdrop Smart Contract (Polygon)
The Polygon airdrop contract can support either:

- **Direct transfer distribution**, or  
- **Merkle-Tree-based claim model**

This repository will include:
- Reference contract implementations  
- Allocation loader scripts  
- Verification tools for end users

---

## How the Migration Works
1. Export snapshot from the legacy ETC-fork Musicoin chain  
2. Export ERC-20 token snapshot from Ethereum  
3. Convert both into uniform CSV datasets  
4. Merge and verify  
5. Generate final airdrop dataset  
6. Deploy Polygon airdrop contract  
7. Load allocation data  
8. Users receive or claim Musicoin 3.0 tokens

---

## Repository Structure
```
/contracts
/scripts
/snapshot-legacy-chain
/snapshot-erc20
/allocation-engine
/validation-tools
/docs
```

---

## License
MIT License
