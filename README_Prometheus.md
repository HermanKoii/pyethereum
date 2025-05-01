# PyEthereum: Low-Level Ethereum Transaction and Encoding Library

## Project Overview

Lightweight Ethereum Transaction and Encoding Library

This project is a low-level implementation of core Ethereum blockchain components, focusing on transaction handling, RLP (Recursive Length Prefix) encoding, and cryptographic transaction processing. The library provides fundamental tools for creating, parsing, and managing Ethereum transactions with a focus on raw data manipulation and encoding.

### Key Features

- **Transaction Handling**: Comprehensive `Transaction` class that supports:
  - Transaction creation with detailed parameters (nonce, recipient, value, fee, data)
  - Transaction signing using cryptographic key operations
  - Transaction serialization and hash generation

- **RLP Encoding**: Custom RLP encoding and decoding implementation for:
  - Converting between binary, integer, and list representations
  - Supporting complex nested data structures
  - Efficient encoding of blockchain-specific data types

- **Cryptographic Primitives**:
  - Transaction signing using ECDSA (Elliptic Curve Digital Signature Algorithm)
  - Public key recovery
  - Hash generation for transaction verification

### Core Capabilities

The library provides low-level primitives for blockchain transaction management, enabling developers to work with raw Ethereum transaction data, perform encoding/decoding operations, and implement core blockchain transaction logic with minimal dependencies.

### Design Philosophy

Emphasizes lightweight, performant implementation of essential blockchain transaction processing components, focusing on providing clean, direct implementations of core cryptographic and encoding mechanisms.

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

Here's a basic example of initializing the project:

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

### Running the Project

#### Development Mode
To run the project in development mode:
```bash
python manager.py
```

### Platform Compatibility

- Compatible with Unix/Linux, macOS, and Windows
- Requires Python 3.7+
- System libraries for `leveldb` must be installed

### Troubleshooting

- Ensure all dependencies are correctly installed
- Verify Python version compatibility
- Check system-specific library requirements for `leveldb`

### Important Notes

- This is a low-level Ethereum implementation
- Intended for research and educational purposes
- Not recommended for production use
- Always exercise caution when working with blockchain-related code

## Usage Examples

### Creating Transactions
Create a new transaction by specifying the nonce, recipient address, value, fee, and optional data:

```python
from transactions import Transaction

# Create a transaction
tx = Transaction(
    nonce=0,           # Transaction nonce
    to='recipient_address',  # Recipient address 
    value=10,          # Amount to send
    fee=1,             # Transaction fee
    data=None          # Optional additional data
)
```

### Signing Transactions
Sign a transaction using a private key:

```python
# Sign the transaction with a private key
private_key = 'your_private_key'
signed_tx = tx.sign(private_key)

# Serialize the signed transaction
serialized_tx = signed_tx.serialize()
hex_tx = signed_tx.hex_serialize()
```

### Transaction Attributes
Access various transaction properties:

```python
# Get transaction details
print(tx.sender)       # Sender's address
print(tx.nonce)        # Transaction nonce
print(tx.to)           # Recipient address
print(tx.value)        # Transaction value
print(tx.fee)          # Transaction fee
```

### Transaction Parsing
Parse an existing transaction from serialized data:

```python
# Parse a transaction from hex or binary data
parsed_tx = Transaction(serialized_transaction_data)
```

### Key Generation (Example from Manager)
Generate addresses from a seed:

```python
from manager import genaddr

# Generate a private key and address from a seed
private_key, address = genaddr("your_seed_string")
```

### Notes
- This is a low-level implementation of Ethereum-like transaction handling
- Always ensure proper key management and security practices
- Transaction validation occurs during blockchain processing

## Additional Notes

### Historical Context

This project represents an early prototype implementation of Ethereum-related blockchain technologies, capturing the fundamental mechanisms of transaction processing and blockchain data handling in Python.

### Technical Foundations

#### RLP Encoding
The implementation features a custom Recursive Length Prefix (RLP) encoding mechanism critical to Ethereum's data serialization:
- Supports encoding of complex data structures including nested lists
- Provides efficient binary conversion and length handling
- Enables compact representation of blockchain-related data

#### Cryptographic Primitives
The codebase demonstrates low-level cryptographic operations fundamental to blockchain technology:
- Address generation techniques
- Transaction signing mechanisms
- Basic cryptographic utilities for blockchain data processing

### Project Limitations

**Important Considerations**:
- This is an experimental, low-level prototype
- Not suitable for production blockchain applications
- Serves primarily as an educational and research-oriented implementation
- Represents an early-stage exploration of Ethereum protocol concepts

### Research and Educational Value

While not intended for direct production use, this implementation offers:
- Insights into early blockchain technology design
- Reference implementation of Ethereum protocol primitives
- Detailed example of transaction and block processing mechanisms
- Demonstration of core blockchain data handling techniques

### Dependency Characteristics

- Relies on external cryptographic libraries for core operations
- Implements custom encoding and processing mechanisms
- Demonstrates modular approach to blockchain component design

### Technical Exploration Areas

Developers and researchers may find this project valuable for:
- Understanding blockchain data serialization
- Exploring low-level transaction processing
- Studying early Ethereum protocol design principles
- Investigating blockchain cryptographic foundations

## Contributing

We welcome contributions to this project! To ensure a smooth collaboration, please follow these guidelines:

### Contribution Process

1. Fork the repository
2. Create a new branch for your feature or bugfix
3. Make your changes, ensuring they align with the project's existing code style
4. Write or update tests to cover your changes
5. Ensure all tests pass before submitting a pull request

### Code Style

- Follow Python conventions and best practices
- Use clear, descriptive variable and function names
- Add docstrings and comments to explain complex logic
- Maintain consistent indentation and formatting

### Testing

- All new features or bugfixes must include appropriate test cases
- Run existing tests before submitting a pull request
- Use the `trietest.py` as a reference for writing comprehensive tests

### Reporting Issues

- Use GitHub Issues to report bugs or suggest improvements
- Provide a clear and detailed description of the issue
- Include steps to reproduce the problem if applicable

### Pull Request Guidelines

- Provide a clear description of your changes
- Reference any related issues
- Ensure your code passes all existing tests
- Be prepared to make modifications based on reviewer feedback

### Code of Conduct

Treat all contributors with respect. Harassment, discrimination, or offensive behavior will not be tolerated.

## License

This project is currently unlicensed. 

### Licensing Status
As no specific license file is present in the repository, the code is considered unlicensed. This means:

- The code is not legally protected for reuse
- No explicit permissions are granted for modification or distribution
- Copyright may implicitly belong to the original authors
- Users should seek explicit permission before using, modifying, or distributing the code

### Usage Restrictions
Without a formal license, potential users should be aware that:
- There are no clear terms defining how the code can be used
- Reproducing or distributing the code may pose legal risks
- The original authors retain implicit copyright

### Recommended Action
For clarity and legal protection, it is strongly recommended to add an appropriate open-source license to define clear terms of use and contribution.