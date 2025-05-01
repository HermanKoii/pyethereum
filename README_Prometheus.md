# PyEthereum: A Low-Level Ethereum Prototype Implementation in Python

## Project Overview

A lightweight, low-level Ethereum implementation in Python that provides core blockchain and transaction processing functionality. This project represents an early prototype of an Ethereum node and smart contract execution environment, focusing on fundamental blockchain components and computational mechanics.

### Core Functionality

The project implements several critical blockchain mechanisms:

- Transaction processing and validation
- Block creation and management
- Smart contract execution environment
- Cryptocurrency transaction handling
- Basic cryptographic operations

### Key Technical Components

- Supports complex transaction types, including contract creation and execution
- Implements a custom scripting language for smart contract interactions
- Provides a transaction pool and block processing system
- Includes cryptographic utilities for address generation and transaction signing
- Defines a comprehensive set of computational opcodes for contract execution

### Design Characteristics

- Low-level implementation focusing on core blockchain principles
- Designed with modularity, with separate modules for blocks, transactions, and contract processing
- Supports fundamental cryptocurrency operations like balance tracking and transaction validation
- Includes a flexible contract evaluation mechanism with support for various computational operations

The codebase serves as an educational and experimental implementation of Ethereum's core concepts, demonstrating the underlying mechanisms of blockchain technology and decentralized computational systems.

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Dependencies

This project requires the following Python libraries:
- `rlp` (Recursive Length Prefix encoding)
- `leveldb` (Key-value storage library)
- `pybitcointools` (Bitcoin-related cryptographic utilities)

### Installation Steps

1. Clone the repository:
```bash
git clone https://github.com/ethereum/pyethereum
cd pyethereum
```

2. Create a virtual environment (recommended):
```bash
python3 -m venv venv
source venv/bin/activate  # On Unix/macOS
venv\Scripts\activate  # On Windows
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
from manager import genaddr

# Generate an Ethereum-like address
private_key, address = genaddr("example_seed")

# Create a transaction (simplified example)
# Note: Actual transaction creation requires specific parameters
```

### Development Mode

To run the project in development mode:
```bash
python manager.py
```

### Platform Considerations

#### System Requirements
- Compatible with Unix/Linux, macOS, and Windows
- Requires Python 3.7+
- System libraries for `leveldb` must be installed

#### Potential Installation Challenges
- Ensure all dependencies are correctly installed
- Verify Python version compatibility
- Check system-specific library requirements for `leveldb`

### Important Notes

- This is a low-level Ethereum implementation
- Intended for research and educational purposes
- Not recommended for production use
- Always exercise caution when working with blockchain-related code

## Usage Examples

These examples demonstrate how to work with the core classes in this Ethereum-related Python library.

#### Creating and Manipulating Transactions

Create a new transaction with specific parameters:
```python
# Create a transaction (nonce, to_address, value, fee, data)
tx = Transaction(1, '0x1234...', 100, 1, '')

# Sign the transaction with a private key
signed_tx = tx.sign(private_key)

# Serialize the transaction to RLP format
serialized_tx = tx.serialize()
hex_serialized_tx = tx.hex_serialize()
```

#### Working with Blocks

Create and manipulate blockchain blocks:
```python
# Initialize a block from RLP-encoded data
block = Block(encoded_block_data)

# Get account balance
balance = block.get_balance('0x1234...')

# Set account balance
block.set_balance('0x1234...', new_balance)

# Pay transaction fees
block.pay_fee(address, fee_amount)

# Get contract state
contract = block.get_contract('0x1234...')

# Serialize block data
block_data = block.serialize()
block_hash = block.hash()
```

#### Retrieving Block and Transaction Information

Accessing block and transaction metadata:
```python
# Block properties
block_number = block.number
block_timestamp = block.timestamp
block_difficulty = block.difficulty

# Transaction properties
tx_nonce = tx.nonce
tx_to_address = tx.to
tx_value = tx.value
tx_sender = tx.sender
```

#### Handling RLP Encoding/Decoding

The library uses RLP (Recursive Length Prefix) encoding for serialization:
```python
# RLP encoding and decoding are handled by the rlp module
# Used internally by Transaction and Block classes
```

## Additional Notes

### Historical Context

This project represents an early implementation of Ethereum-related cryptographic and transaction processing utilities, serving as a historical snapshot of the Ethereum protocol's development.

### RLP Encoding Specifics

The implementation features a custom Recursive Length Prefix (RLP) encoding mechanism critical to Ethereum's data serialization:
- Supports encoding of integers, strings, and nested lists
- Provides efficient binary conversion and length handling
- Offers flexible encoding for diverse data types

### Transaction Processing

The transaction implementation demonstrates core blockchain functionality:
- Cryptographic transaction signing using ECDSA
- Comprehensive transaction creation and parsing
- Serialization and deserialization of transaction data
- Mechanism for deriving sender addresses

### Compatibility and Limitations

**Important Considerations**:
- This is a prototype implementation
- Not intended for production use
- Represents an early-stage development of Ethereum-related technologies
- Current maintained version is available in the [official pyethereum repository](https://github.com/ethereum/pyethereum)

### Cryptographic and Technical Foundations

- Utilizes basic cryptographic primitives
- Implements low-level blockchain data handling techniques
- Provides foundational components for understanding blockchain data processing

### Research and Educational Value

While not suitable for production, this implementation offers:
- Insights into early blockchain technology design
- Example of Ethereum protocol primitives
- Reference for understanding transaction and encoding mechanisms

### Dependency Notes

- Relies on `pybitcointools` for cryptographic operations
- Features a custom RLP implementation for data encoding

## Contributing

We welcome contributions to this project! By contributing, you help improve and expand the functionality of this Ethereum-related Python library.

### How to Contribute

1. Fork the repository
2. Create a new branch for your feature or bugfix
3. Make your changes
4. Write or update tests to cover your modifications
5. Ensure all tests pass
6. Submit a pull request

### Contribution Guidelines

#### Code Style
- Follow Python coding standards (PEP 8)
- Write clear, concise, and well-documented code
- Use meaningful variable and function names

#### Testing
- All new features and bugfixes must include appropriate test cases
- Run existing test suite before submitting a pull request
- Maintain or improve overall test coverage

#### Reporting Issues
- Use GitHub Issues to report bugs or suggest enhancements
- Provide a clear description of the issue
- Include steps to reproduce the problem, if applicable

#### Pull Request Process
- Provide a clear description of your changes
- Reference any related issues
- Ensure your code passes all existing tests
- Be responsive to code review feedback

### Code of Conduct
Be respectful, inclusive, and considerate of others. Harassment and discrimination are not tolerated.

## License

This project is currently unlicensed. 

#### Licensing Status
As no specific license file is present in the repository, the code is considered unlicensed. This means:

- The code is not legally protected for reuse
- No explicit permissions are granted for modification or distribution
- Copyright may implicitly belong to the original authors
- Users should contact the original authors for any usage permissions

#### Recommended Action
For clarity and legal protection, it is strongly advised to add an appropriate open-source license to the project, such as MIT, Apache, or GPL, to define clear terms of use and contribution.