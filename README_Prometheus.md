# Pyethereum: Lightweight Ethereum Cryptographic and Transaction Processing Utilities

## Project Overview

This project is a lightweight implementation of Ethereum-related cryptographic and transaction processing utilities, focused on core blockchain data encoding and transaction management.

### Key Features

- **RLP (Recursive Length Prefix) Encoding/Decoding**: 
  - Provides robust encoding and decoding mechanisms for serializing complex data structures
  - Supports encoding of integers, strings, and lists
  - Handles various input types with flexible serialization rules

- **Transaction Management**:
  - Comprehensive `Transaction` class for creating, parsing, and manipulating Ethereum transactions
  - Supports transaction signing and verification
  - Handles transaction serialization and hash generation
  - Integrates cryptographic functions for secure transaction processing

### Core Capabilities

- Binary conversion and length calculation utilities
- Recursive Length Prefix (RLP) encoding and decoding
- Transaction creation, signing, and serialization
- Cryptographic operations including hashing and digital signatures

### Technical Highlights

- Implements low-level blockchain data handling primitives
- Provides foundational components for Ethereum-like blockchain interactions
- Lightweight and focused implementation of core blockchain data processing techniques

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.7+
- pip package manager

### Dependencies

This project requires the following Python libraries:
- `rlp` (Recursive Length Prefix encoding)
- `leveldb` (Key-value storage library)
- `pybitcointools` (Bitcoin-related utilities)

### Installation

To install the project and its dependencies, follow these steps:

1. Clone the repository:
```bash
git clone https://github.com/ethereum/pyethereum
cd pyethereum
```

2. Create a virtual environment (recommended):
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

3. Install required dependencies:
```bash
pip install rlp leveldb pybitcointools
```

### Quick Start

Here's a basic example of using the project:

```python
import rlp
from blocks import Block
from transactions import Transaction

# Generate an address
from manager import genaddr
private_key, address = genaddr("example_seed")

# Create a transaction (simplified example)
tx = Transaction(...)  # Construct transaction details
```

### Development

To run the project in development mode:
```bash
python manager.py  # Example entry point
```

### Important Notes

- This is a low-level Ethereum implementation
- Ensure you have the necessary cryptographic libraries installed
- Always use caution when working with blockchain-related code

### Troubleshooting

- Verify all dependencies are correctly installed
- Check Python version compatibility
- Ensure you have the required system libraries for `leveldb`

## API Reference

### Transactions

#### `Transaction` Class

A class representing blockchain transactions with methods for parsing, signing, and serialization.

**Constructor**:
```python
def __init__(self, nonce, to, value, fee, data)
```
- `nonce`: Transaction sequence number
- `to`: Recipient address
- `value`: Transaction amount
- `fee`: Transaction fee
- `data`: Transaction data payload

**Methods**:

1. `parse(data)`: Parse a transaction from RLP-encoded data
   - Decodes transaction details and validates the transaction
   - Recovers sender's public key
   - Returns `self`

2. `sign(key)`: Sign the transaction
   - Signs transaction with private key
   - Sets `v`, `r`, `s` signature components
   - Sets sender's address
   - Returns `self`

3. `serialize()`: Serialize transaction to RLP-encoded format
   - Converts transaction to binary representation
   - Returns encoded transaction

4. `hex_serialize()`: Serialize transaction to hex-encoded format
   - Converts transaction to hexadecimal representation
   - Returns hex-encoded transaction

5. `hash()`: Generate transaction hash
   - Computes SHA256 hash of serialized transaction
   - Returns transaction hash

### Functions and Parameters

#### Manager Module (`manager.py`)

**Constants**:
- `genesis_header`: Initial block header configuration
- `genesis`: Genesis block definition
- `mainblk`: Main blockchain block instance

**Functions**:
1. `genaddr(seed)`: Generate cryptographic address
   - Creates private key and corresponding address from seed
   - Returns tuple of `(private_key, address)`

2. `broadcast(obj)`: Placeholder for broadcasting blockchain objects
   - Currently a no-op function

3. `receive(obj)`: Process received blockchain objects
   - Validates and processes transactions, messages, and blocks

### Blockchain Processing

#### Block Processing (`processblock.py`)

**Script Code Map** (`scriptcode_map`):
Dictionary mapping numeric codes to blockchain script operations like:
- Arithmetic: `ADD`, `SUB`, `MUL`, `DIV`
- Comparison: `LT`, `GT`, `EQ`
- Cryptographic: `SHA256`, `ECMUL`, `ECSIGN`
- Memory: `STORE`, `LOAD`
- Control Flow: `JMP`, `JMPI`

**Parameters** (`params`):
Configuration for blockchain economics, including:
- Transaction fees
- Block rewards
- Memory and computation costs
- Block time parameters

**Key Functions**:
1. `process_transactions(block, transactions)`: Process block transactions
2. `eval(block, transactions, timestamp, coinbase)`: Evaluate and process a block
3. `eval_contract(block, transaction_list, tx)`: Execute smart contract logic

### Encoding and Decoding (RLP Module)

#### RLP Encoding/Decoding Functions
- `encode(s)`: Encode data to RLP format
- `decode(s)`: Decode RLP-encoded data
- Supports encoding/decoding of integers, strings, and lists

### Database and Trie Structure (`trie.py`)

#### `Trie` Class
Implements a Merkle Patricia Trie data structure for efficient key-value storage and verification.

**Methods**:
- `get(key)`: Retrieve value for a key
- `update(key, value)`: Update or insert key-value pair
- `to_dict()`: Convert trie to dictionary representation
- `get_size()`: Get total number of entries

#### `DB` Class
Wrapper for LevelDB database operations
- `get(key)`: Retrieve value
- `put(key, value)`: Store key-value pair
- `delete(key)`: Remove key-value pair

## Project Structure

The project is a Python-based implementation of core blockchain-related functionality, with several key modules that handle different aspects of blockchain operations:

### Core Modules
- `blocks.py`: Implements the `Block` class, handling block-level operations including:
  - Block initialization and serialization
  - State management
  - Transaction processing
  - Balance and nonce tracking
  - Blockchain state manipulation

- `transactions.py`: Defines the `Transaction` class with functionality for:
  - Transaction creation and parsing
  - Transaction signing
  - Serialization
  - Cryptographic operations related to transactions

### Cryptographic and Data Structures
- `trie.py`: Implements a Merkle Trie data structure, crucial for efficient state management and data verification in blockchain systems
- `rlp.py`: Provides RLP (Recursive Length Prefix) encoding and decoding, a critical serialization method used in Ethereum-like blockchain systems

### Additional Utility and Test Modules
- `processblock.py`: Likely contains logic for processing blockchain blocks
- `manager.py`: Potentially manages overall blockchain or system operations
- `parser.py`: Provides parsing utilities for blockchain-related data
- `trietest.py`: Contains tests for the Trie data structure implementation

### Configuration and Documentation
- `README.md`: Project documentation and overview

The project follows a modular design, with each file responsible for a specific aspect of blockchain functionality, emphasizing separation of concerns and maintainability.

## Additional Notes

### Historical Context

This repository contains an early implementation of Ethereum-related cryptographic and transaction processing utilities. It represents a historical snapshot of the Ethereum protocol development, specifically focusing on core encoding and transaction mechanisms.

### RLP Encoding Specifics

The project implements a custom RLP (Recursive Length Prefix) encoding and decoding mechanism, which is crucial for Ethereum's data serialization. Key characteristics include:
- Support for encoding integers, strings, and nested lists
- Efficient binary conversion and length handling
- Flexible encoding for different data types

### Transaction Handling

The transaction implementation supports:
- Transaction creation and parsing
- Cryptographic signing using ECDSA
- Serialization and deserialization of transaction data
- Sender address derivation

### Compatibility Note

This is an early prototype and is NOT intended for production use. The current version is maintained at the [official pyethereum repository](https://github.com/ethereum/pyethereum).

### Security Considerations

- The implementation uses basic cryptographic primitives
- No guarantee of current security standards
- Should be used for historical research or educational purposes only

### Dependencies

- Relies on `pybitcointools` for cryptographic operations
- Custom RLP implementation for data encoding

## Contributing

We welcome contributions to this project! To ensure a smooth collaboration process, please follow these guidelines:

### How to Contribute

1. **Fork the Repository**: Create a fork of the project on GitHub.

2. **Create a Branch**: 
   - Create a new branch for your feature or bugfix
   - Use a clear and descriptive branch name
   - Example: `feature/add-new-encoding-method` or `bugfix/fix-rlp-decoding`

3. **Code Guidelines**
   - Follow Python's PEP 8 style guide
   - Write clear, concise, and well-documented code
   - Include type hints where appropriate
   - Ensure your code passes existing tests

4. **Testing**
   - Add tests for new functionality
   - Ensure all existing tests pass
   - Run the full test suite before submitting a pull request
   - Use the existing test files (e.g., `trietest.py`) as a reference for test structure

5. **Commit Messages**
   - Use clear and descriptive commit messages
   - Provide context about why the change was made
   - Reference issue numbers if applicable

6. **Pull Request Process**
   - Open a pull request with a clear title and description
   - Describe the purpose and impact of your changes
   - Be prepared to discuss and iterate on feedback

### Reporting Issues

- Use the GitHub Issues section to report bugs or suggest improvements
- Provide detailed information, including:
  - Steps to reproduce the issue
  - Expected vs. actual behavior
  - Python version
  - Relevant code snippets or error messages

### Code of Conduct

Respect and professionalism are expected in all interactions. Be considerate, collaborative, and constructive.