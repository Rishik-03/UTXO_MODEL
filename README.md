# CS216 – Blockchain Simulation Assignment (UTXO Model)

## Team Name

**Strange Coins**

## Team Members

| Name          | Roll Number |
| ------------- | ----------- |
| Charan Kumar  | 240001057   |
| Shiv Pratap   | 240001069   |
| Rishik        | 240003027   |
| Aravind Nayak | 240003082   |

---

# Overview

This project is a simplified blockchain simulation implemented in **C++** using the **UTXO (Unspent Transaction Output)** model.

The project demonstrates:

* Transaction creation
* Transaction validation
* Mempool management
* Block mining
* UTXO updates
* Balance tracking

The implementation follows a **modular design**, where each blockchain component is separated into its own header (`.h`) and source (`.cpp`) files.

---

# Repository Structure

```text
CS216/
│
├── src/
│   ├── main.cpp
│   ├── utxo_manager.h
│   ├── utxo_manager.cpp
│   ├── transaction.h
│   ├── mempool.h
│   ├── mempool.cpp
│   ├── validator.h
│   ├── validator.cpp
│   ├── miner.h
│   └── miner.cpp
│
├── tests/
│   ├── tests.h
│   └── tests.cpp
│
├── .gitignore
├── README.md
├── requirements.txt
└── sample_output.txt
```

---

# Core Components

## 1. UTXO Manager (`utxo_manager`)

Maintains the set of all **Unspent Transaction Outputs (UTXOs)**.

### Responsibilities

* Add UTXOs after mining
* Remove spent UTXOs
* Calculate balances
* Track ownership

### Data Structure

```text
Key   : (transaction_id, output_index)
Value : {amount, owner}
```

### Why UTXO?

The UTXO model:

* Prevents double spending
* Enables efficient balance calculation
* Provides simple ownership tracking

---

## 2. Transaction (`transaction`)

Represents a blockchain transaction.

### Components

* Transaction ID
* Inputs (references to existing UTXOs)
* Outputs (new UTXOs)

Transactions become immutable once created.

---

## 3. Validator (`validator`)

Verifies transactions before they enter the mempool.

### Validation Checks

* Referenced UTXOs exist
* Sender owns referenced UTXOs
* No double spending
* Total Input ≥ Total Output

### Result

* Valid transactions are accepted
* Invalid transactions are rejected immediately

---

## 4. Mempool (`mempool`)

Stores valid transactions waiting to be mined.

### Responsibilities

* Accept validated transactions
* Hold pending transactions
* Clear transactions after block creation

---

## 5. Miner (`miner`)

Creates blocks from mempool transactions.

### Responsibilities

* Select transactions from mempool
* Update UTXO set
* Create coinbase transaction
* Award mining reward

### Mining Reward

The miner receives newly created UTXOs through the coinbase transaction.

---

## 6. Test Scenarios (`tests`)

Contains all **10 mandatory test cases**.

### Features

* Run a specific test
* Run all tests together

### Tests Verify

* Balance updates
* Validation logic
* Double-spending prevention
* Mempool behavior
* Mining rewards

---

# Program Flow

```text
Genesis UTXOs
      │
      ▼
Create Transaction
      │
      ▼
Validate Transaction
      │
      ▼
Add to Mempool
      │
      ▼
Mine Block
      │
      ▼
Update UTXO Set
      │
      ▼
Display Balances
```

---

# Compilation Instructions

Run the following command from the project root directory:

```bash
g++ -std=gnu++17 \
src/main.cpp \
src/utxo_manager.cpp \
src/mempool.cpp \
src/validator.cpp \
src/miner.cpp \
tests/tests.cpp \
-o blockchain
```

---

# Running the Program

```bash
./blockchain
```

For Windows:

```bash
blockchain.exe
```

---

# Features Implemented

✔ UTXO-based ledger

✔ Transaction validation

✔ Double-spending prevention

✔ Mempool management

✔ Block mining

✔ Coinbase rewards

✔ Balance tracking

✔ Modular C++ architecture

✔ Automated test scenarios

✔ Genesis balance initialization

---

# Sample Output

Refer to:

```text
sample_output.txt
```

for example execution results and test outputs.
