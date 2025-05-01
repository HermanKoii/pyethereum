# PyEthereum: A Pure Python Blockchain Implementation and Educational Toolkit

## Project Overview

A lightweight Ethereum-like blockchain implementation in Python, focusing on core blockchain data structures and transaction processing. This project provides a foundational implementation of blockchain concepts, including block and transaction management, cryptographic primitives, and state tracking.

### Key Features

- **Block Management**: Supports block creation, serialization, and verification with key attributes like block number, previous block hash, transactions, and state root
- **Transaction Handling**: Implements a Transaction class that supports:
  - Transaction signing and signature verification
  - Value transfer between addresses
  - Transaction data and fee management
- **State Management**: Utilizes a Merkle Patricia Trie for efficient state storage and retrieval
- **Cryptographic Primitives**: Integrates cryptographic functions for hashing, public key recovery, and digital signatures

### Core Capabilities

- Create and validate blockchain blocks
- Process and sign cryptocurrency transactions
- Manage account balances and state
- Perform cryptographic operations essential for blockchain functionality

### Technical Highlights

- Written in pure Python
- Implements Recursive Length Prefix (RLP) encoding
- Supports hexadecimal and binary data representations
- Provides low-level blockchain data structure implementations

This implementation serves as an educational and foundational tool for understanding blockchain technology's core mechanisms, demonstrating how fundamental blockchain components interact and function.

## Getting Started, Installation, and Setup

### Prerequisites

Before you begin, ensure you have the following dependencies installed:
- Python 3.7+
- pip (Python package manager)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ethereum/pyethereum.git
   cd pyethereum
   ```

2. Install required dependencies:
   ```bash
   pip install rlp leveldb pybitcointools
   ```

### Quick Start

#### Running the Project

To interact with the project, you can use the various modules provided:

```python
import rlp
from blocks import Block
from transactions import Transaction
from manager import db, genaddr, broadcast, receive

# Generate test addresses
k1, a1 = genaddr("123")
k2, a2 = genaddr("456")

# Create a transaction or block
# Example usage depends on your specific use case
```

### Development

For development purposes, ensure you have the following additional tools:
- Git
- A Python IDE or text editor

### Project Structure

The project contains several key modules:
- `blocks.py`: Block-related functionality
- `transactions.py`: Transaction handling
- `manager.py`: Core management and utility functions
- `rlp.py`: RLP (Recursive Length Prefix) encoding/decoding
- `processblock.py`: Block processing logic

### Notes

- This is a low-level Ethereum implementation
- Use with caution and for educational/experimental purposes
- Not recommended for production without thorough testing and security review

## Project Structure

The project is organized into the following key Python modules:

#### Core Modules
- `blocks.py`: Handles blockchain block-related functionality
- `manager.py`: Likely manages core system operations
- `parser.py`: Responsible for parsing data or transactions
- `processblock.py`: Contains logic for processing blockchain blocks
- `rlp.py`: Implements RLP (Recursive Length Prefix) encoding/decoding
- `transactions.py`: Manages blockchain transaction-related operations
- `trie.py`: Implements Merkle Patricia Trie data structure

#### Testing
- `trietest.py`: Contains tests for the trie implementation

#### Project Root
- `README.md`: Project documentation and overview

Each module focuses on a specific aspect of blockchain or cryptographic data structures, suggesting this is a low-level implementation related to Ethereum or blockchain technology.

## Technologies Used

### Programming Languages
- Python 2.x (legacy implementation)

### Core Technologies
- RLP (Recursive Length Prefix) Encoding/Decoding
  - Custom implementation for Ethereum-specific data serialization
- Ethereum Protocol Implementation
  - Low-level blockchain data structures and transaction processing

### Cryptography and Blockchain
- Blockchain data structures
- Transaction encoding
- Trie data structure implementation

### Development Tools
- Standard Python libraries
  - Built-in types and conversion utilities
  - No external dependencies detected in the current implementation

### Key Technical Characteristics
- Low-level blockchain data handling
- Manual binary and encoding operations
- Minimal external dependency approach

## Additional Notes

### Ethereum Prototype Implementation

This repository contains an early prototype implementation of Ethereum's core blockchain functionality, demonstrating fundamental blockchain and smart contract concepts. The code provides insights into the initial design considerations of decentralized blockchain systems.

#### Key Implementation Details

- Implements a custom RLP (Recursive Length Prefix) encoding/decoding mechanism for serialization
- Supports basic transaction processing and block validation
- Includes a rudimentary smart contract virtual machine with a limited instruction set
- Defines blockchain parameters such as mining rewards, transaction fees, and difficulty adjustment

#### Supported Script Operations

The contract evaluation system supports a range of low-level operations, including:
- Arithmetic: ADD, SUB, MUL, DIV, MOD, EXP
- Comparison: LT, LE, GT, GE, EQ, NOT
- Cryptographic: SHA256, RIPEMD-160
- Elliptic Curve Cryptography: ECMUL, ECADD, ECSIGN, ECRECOVER
- Memory and Control Flow: STORE, LOAD, JMP, JMPI

#### Historical Context

This implementation represents an early stage of Ethereum's technological evolution, predating the more sophisticated and mature Ethereum implementations. It serves as a valuable historical artifact and learning resource for understanding the initial design principles of programmable blockchain systems.

#### Limitations

- Experimental and non-production ready
- Limited instruction set for smart contracts
- Lacks advanced blockchain features found in modern implementations
- Not compatible with current Ethereum network specifications

### Important Note

The original project has moved. The current implementation can be found at the official Ethereum repository.

## Contributing

We welcome contributions to this project! Here are some guidelines to help you get started:

### How to Contribute

1. Fork the repository
2. Create a new branch for your feature or bugfix
3. Make your changes
4. Write or update tests as appropriate
5. Ensure all tests pass
6. Submit a pull request with a clear description of your changes

### Contribution Requirements

#### Code Style
- Follow Python coding standards (PEP 8)
- Use clear, descriptive variable and function names
- Add docstrings to functions and classes
- Keep code clean and well-commented

#### Testing
- All new features or bugfixes must include appropriate test cases
- Run existing tests using `python -m unittest` before submitting a pull request
- Ensure 100% test coverage for new code

#### Code Review
- All contributions will be reviewed by the project maintainers
- Be prepared to make requested changes
- Maintain a respectful and collaborative attitude

### Reporting Issues
- Use the GitHub Issues section to report bugs or suggest improvements
- Provide detailed information, including:
  - Expected behavior
  - Actual behavior
  - Steps to reproduce
  - Python version
  - Any relevant error messages or logs

### Questions?
If you have any questions about contributing, please open an issue for discussion.

## License

This project is currently unlicensed. 

#### Licensing Status
Without an explicit license, the default copyright laws apply. This means:
- No one else has permission to reproduce, distribute, or create derivative works
- The original authors retain all rights to the code
- Others cannot legally use, modify, or share the code without explicit permission

#### Recommendations
It is strongly recommended to add an open-source license to clarify usage rights and encourage collaboration. Common licenses for similar projects include MIT, Apache 2.0, or GPL.