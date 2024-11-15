# Blockchain and Distributed Ledger Technology

## Blockchain Structure

A blockchain is a growing list of records, known as blocks, which are linked using cryptography. Each block contains a cryptographic hash of the previous block, a timestamp, and transaction data.

Here's a simplified Pythonic representation of a block:

```python
class Block:
    def __init__(self, previous_hash, timestamp, data, hash):
        self.previous_hash = previous_hash
        self.timestamp = timestamp
        self.data = data
        self.hash = hash
```

## Proof of Work

Blockchain employs a mechanism called "Proof of Work" (PoW) to create new blocks. Miners compete to solve complex mathematical problems and the first one to solve it adds the new block to the chain. This mathematical problem can be described as finding an input that, when hashed, produces a result with a specific number of leading zeros.

Here's a basic PoW implementation in Python:

```python
import hashlib
def proof_of_work(data, difficulty):
    prefix = '0' * difficulty
    nonce = 0
    while True:
        digest = hashlib.sha256(f'{data}{nonce}'.encode()).hexdigest()
        if digest[:difficulty] == prefix:
            return nonce
        nonce += 1
```

## Distributed Ledger Technology

Distributed Ledger Technology (DLT) is a consensus of replicated, shared, and synchronized digital data geographically spread across multiple sites, countries, or institutions. Unlike traditional databases, distributed ledgers have no central data store or administration functionality.

In a blockchain, the ledger is updated with each block and the updated version is distributed to all nodes in the network. Each node validates the new block and the state of the ledger before adding it to their own copy.

This robust and secure design makes DLTs resistant to data modification, providing a solid foundation for systems like cryptocurrencies.
