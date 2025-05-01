# PyEthereum: Lightweight Ethereum Blockchain Core Primitives Toolkit

## Project Overview

This project is an implementation of core Ethereum blockchain data structures and transaction handling, focusing on fundamental cryptographic and serialization mechanisms for blockchain transactions.

### Core Functionality

The library provides essential components for working with Ethereum-like blockchain transactions, including:

- Recursive Length Prefix (RLP) encoding and decoding
- Transaction creation, parsing, and serialization
- Cryptographic transaction signing and verification

### Key Features

- Lightweight RLP implementation for efficient data encoding
- Transaction object with comprehensive methods for:
  - Creating and parsing transactions
  - Signing transactions with cryptographic keys
  - Serializing transactions for network transmission
- Support for hexadecimal and binary data formats
- Cryptographic operations including hashing and public key recovery

### Technical Highlights

The implementation demonstrates low-level blockchain transaction handling, including:
- Nonce management
- Transaction value and fee tracking
- Cryptographic signature generation and verification
- Sender address derivation from transaction signatures

This library serves as a foundational component for building Ethereum-compatible blockchain applications, providing core primitives for transaction processing and data serialization.

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.x
- pip (Python package manager)

### Dependencies

Before getting started, install the following dependencies:

```bash
pip install rlp leveldb pybitcointools
```

### Quick Start

This library provides low-level Ethereum data structure and encoding utilities. Instead of running as a standalone application, you'll import and use its modules in your Python projects.

#### Basic Import Example

```python
from blocks import Block
from transactions import Transaction
from manager import genaddr

# Generate an Ethereum-like address
private_key, address = genaddr("your_seed")

# Create a transaction or interact with blockchain-related functions
```

### Installation

#### Cloning the Repository

```bash
git clone https://github.com/ethereum/pyethereum
cd pyethereum
```

### Development Setup

1. Verify all dependencies are successfully installed
2. The project uses a local LevelDB database in the "objects" directory for storing blockchain data
3. Includes testing utilities and example address generation

### Running Tests

Since this is a library of low-level Ethereum data structures, standard application running is not applicable. However, you can run tests using Python's testing framework (specific test command details are not provided in the repository).

### Package Distribution

To create a distributable package:

```bash
python setup.py sdist bdist_wheel
```

### Platform Compatibility

- Supports Python 3.x
- Compatible with Ethereum-like transaction and data encoding patterns
- Requires additional cryptographic libraries for full functionality

### Important Notes

- This is a foundational toolkit for blockchain developers
- Provides critical infrastructure for data serialization and encoding
- Primarily intended for educational and research purposes
- Requires careful integration with other blockchain tools and frameworks

## Features / Capabilities

Ethereum-related Data Structures and Utilities provide a comprehensive set of core capabilities for blockchain and cryptographic operations:

### RLP (Recursive Length Prefix) Encoding
- Robust encoding and decoding mechanism for Ethereum's data serialization format
- Supports encoding of:
  - Integers (both small and large)
  - Strings
  - Lists
- Handles various length encodings with efficient binary conversion
- Supports encoding numbers up to 2^256

### Transaction Management
- Full transaction object implementation with key features:
  - Transaction creation and parsing
  - Digital signature support
  - Transaction serialization
  - Sender identification
- Cryptographic operations including:
  - ECDSA signature generation
  - Public key recovery
  - Transaction hashing

### Merkle Patricia Trie Data Structure
- Advanced key-value storage mechanism with unique features:
  - Persistent storage using LevelDB
  - Efficient state management
  - Complex key encoding and decoding
  - Support for inserting, updating, and deleting key-value pairs
- Advanced traversal and dictionary conversion methods
- Cryptographic hash-based node identification

### Database Interaction
- Lightweight database abstraction layer
- Key-value storage operations:
  - Get
  - Put
  - Delete
- Support for multiple database instances

### Cryptographic Utilities
- SHA256 hashing
- Binary conversion and manipulation
- Hexadecimal encoding/decoding

These features provide a foundational toolkit for blockchain and cryptographic applications, with a focus on Ethereum-specific data structures and encoding mechanisms.

## Usage Examples

### Creating a Transaction
```python
from transactions import Transaction
from pybitcointools import sha256

# Create a new transaction
tx = Transaction(
    nonce=0,         # Transaction nonce
    to='destination_address',  # Recipient address
    value=100,       # Amount to send
    fee=1,           # Transaction fee
    data=''          # Optional transaction data
)

# Sign the transaction with a private key
private_key = 'your_private_key'
signed_tx = tx.sign(private_key)

# Serialize the transaction (for sending or storage)
serialized_tx = signed_tx.serialize()
hex_tx = signed_tx.hex_serialize()
```

### Working with Blocks
```python
from blocks import Block
import rlp

# Create a genesis block
genesis_block_data = [
    # Block header and other initialization parameters
]
genesis_block = Block(rlp.encode(genesis_block_data))

# Access block properties
block_hash = genesis_block.hash()
block_number = genesis_block.number
```

### Address Generation
```python
from manager import genaddr

# Generate a random address from a seed
private_key, address = genaddr("your_seed_string")
```

### Basic Transaction Pool Operations
```python
from manager import txpool, receive, broadcast

# Receive a transaction or block
received_object = 'encoded_transaction_or_block'
result = receive(received_object)

# Broadcast a transaction or block
broadcast(received_object)
```

### Querying Blockchain State
```python
from manager import receive

# Get balance of an address
balance_query = receive(['getbalance', 'address'])

# Retrieve an object by hash
object_query = receive(['getobj', 'object_hash'])
```

### Notes
- This library provides low-level Ethereum blockchain primitives
- Transactions and blocks can be created, signed, and serialized
- Basic blockchain operations like address generation and transaction handling are supported

## Project Structure

The project is structured with several Python modules that collectively implement core blockchain functionality:

### Core Modules
- `blocks.py`: Defines the `Block` class, handling block creation, serialization, and state management
- `transactions.py`: Implements transaction-related functionality
- `trie.py`: Provides Merkle tree (Trie) data structure implementation
- `rlp.py`: Handles Recursive Length Prefix (RLP) encoding and decoding
- `processblock.py`: Contains block processing logic
- `manager.py`: Manages blockchain operations, including transaction and block handling

### Testing
- `trietest.py`: Likely contains unit tests for the Trie data structure

### Key Features of the Structure
- Modular design separating concerns across different components
- Support for block creation, transaction processing, and state management
- Includes utility modules for cryptographic operations and data encoding
- Leverages LevelDB for persistent storage of blockchain objects

### Dependencies
- Relies on external libraries such as `pybitcointools` for cryptographic functions
- Uses `leveldb` for database operations
- Implements custom data structures and encoding mechanisms

## Additional Notes

### Technical Implementation Details

The project provides a low-level implementation of Ethereum blockchain data structures with a focus on core encoding and data management primitives. Key technical components include specialized encoding mechanisms and cryptographic data structure handling.

#### Key Technical Characteristics

- **Encoding Mechanism**: Implements Recursive Length Prefix (RLP) encoding for complex data serialization
- **Data Structure Management**: Utilizes Merkle Patricia Trie for efficient key-value storage and cryptographic verification
- **Cryptographic Foundations**: Supports address generation, transaction parsing, and digital signature operations

### Performance Considerations

- Designed for low-level blockchain data manipulation
- Recursive encoding algorithms may introduce performance overhead for large datasets
- Primarily intended for educational and research purposes in blockchain technology

### Compatibility and Dependencies

- **Python Environment**: Compatible with Python 3.x
- **External Dependencies**: 
  - `rlp`
  - `leveldb`
  - `pybitcointools`

### Architectural Insights

The library is structured as a modular toolkit with specialized modules for different blockchain-related operations:
- `blocks.py`: Block management and representation
- `transactions.py`: Transaction parsing and handling
- `rlp.py`: Recursive Length Prefix encoding utilities
- `trie.py`: Merkle Patricia Trie implementation
- `manager.py`: Utility functions for network and state interactions

### Potential Use Cases

- Blockchain research and educational projects
- Low-level Ethereum protocol implementation studies
- Experimental blockchain development
- Cryptographic data structure exploration

### Limitations and Considerations

- Not recommended for direct production use without extensive review
- Requires advanced understanding of blockchain technologies
- Serves as a foundational toolkit rather than a complete blockchain solution

## Contributing

We welcome contributions to this project! To ensure a smooth and collaborative development process, please follow these guidelines:

### Contribution Process

1. Fork the repository and create a new branch from the `main` branch
2. Make your changes, ensuring they align with the project's core purpose of providing low-level Ethereum data structures and encoding mechanisms
3. Write clear, descriptive commit messages that explain the purpose of your changes

### Code Style Guidelines

- Adhere to PEP 8 Python style guidelines
- Use 4 spaces for indentation
- Write clear, descriptive variable and function names
- Include type hints where appropriate
- Add docstrings to explain the purpose and behavior of functions and classes

### Testing Requirements

- All new features or bug fixes must include corresponding unit tests
- Existing tests located in `trietest.py` provide a reference for test structure
- Ensure all tests pass before submitting a pull request
- Write tests that cover various edge cases and potential failure scenarios

### Documentation

- Update relevant documentation to reflect your changes
- If you add new functionality, provide clear examples of its usage
- Keep documentation consistent with the project's technical focus on low-level Ethereum data structures

### Submitting Contributions

1. Push your changes to your fork
2. Open a pull request with a clear description of your modifications
3. Explain the rationale behind your changes and any potential impacts
4. Be prepared to discuss and refine your contribution during the review process

### Reporting Issues

- Use GitHub Issues to report bugs or suggest improvements
- Provide a clear, detailed description of the issue
- Include steps to reproduce the problem
- Specify your Python environment and version

### Code of Conduct

- Treat all contributors with respect and professionalism
- Constructive feedback and collaboration are key to the project's success
- Harassment or discriminatory behavior will not be tolerated

## License

This project is currently unlicensed.

### Legal Status

Without a specific license, the following legal conditions apply:

- The original authors retain full copyright to the source code
- No permission is granted for reproduction, distribution, or creation of derivative works
- Explicit permission from the original authors is required for any use of the code

### Recommended Action

It is strongly recommended that the project maintainers select an appropriate open-source license to:
- Clarify usage rights
- Promote collaboration
- Provide clear guidelines for code utilization and contribution