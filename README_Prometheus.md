# EthPy: A Lightweight Python Implementation of Ethereum Blockchain Core Components

## Project Overview

A lightweight Python implementation of core Ethereum blockchain components, focusing on fundamental blockchain data structures and transaction processing. This project provides a low-level implementation of key Ethereum blockchain mechanisms, including block management, transaction handling, and state tracking.

### Core Functionality

The project implements critical blockchain infrastructure with a focus on:
- Block creation and serialization
- Transaction processing
- State management using Merkle Patricia Tries
- Cryptographic address generation
- Basic blockchain object storage and retrieval

### Key Features

- Supports RLP (Recursive Length Prefix) encoding for blockchain data serialization
- Implements a Block class with comprehensive validation and state management
- Provides transaction processing and fee handling mechanisms
- Includes a basic transaction pool and object management system
- Generates cryptographic addresses from seed values
- Supports genesis block creation and blockchain state tracking

### Design Principles

The implementation follows core Ethereum blockchain design principles, offering a minimal yet functional representation of blockchain components. It provides a foundation for understanding blockchain data structures and transaction mechanisms through a Python-based implementation.

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Dependencies

Before installing the project, ensure you have the following Python libraries:

- `rlp`: Recursive Length Prefix encoding library
- `leveldb`: Key-value storage library
- `pybitcointools`: Bitcoin and cryptocurrency utility library

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/ethereum-python-project.git
   cd ethereum-python-project
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

#### Development Mode

To run the project in development:

1. Ensure you're in the project directory and virtual environment
2. Run Python scripts directly, for example:
   ```bash
   python manager.py
   ```

#### Key Modules

- `manager.py`: Main management module for blockchain operations
- `blocks.py`: Block creation and management
- `transactions.py`: Transaction handling
- `processblock.py`: Block processing logic

### Configuration

The project uses a default LevelDB database located at `./objects/` for storing blockchain data.

### Exploring the Project

You can interact with different modules by importing them in your Python scripts or running them directly:

```python
from manager import mainblk, genaddr
from transactions import Transaction

# Generate test addresses
private_key, address = genaddr("your_seed")
```

### Troubleshooting

- Ensure all dependencies are correctly installed
- Check Python version compatibility
- Verify you have write permissions in the project directory

## Project Structure

The project is organized as a set of Python modules focused on Ethereum-related functionality:

#### Core Modules
- `blocks.py`: Handles blockchain block-related operations and structures
- `manager.py`: Likely manages overall system or blockchain state management
- `parser.py`: Provides parsing capabilities for Ethereum-related data
- `processblock.py`: Implements block processing logic
- `rlp.py`: Implements RLP (Recursive Length Prefix) encoding/decoding
- `transactions.py`: Manages Ethereum transaction processing and related functionality
- `trie.py`: Implements Merkle Patricia Trie data structure
- `trietest.py`: Contains tests for the Trie implementation

#### File Organization
Each module represents a specific functional component of the Ethereum system, with clear separation of concerns. The project uses standalone Python modules that can be imported and used independently.

#### Key Implementation Notes
- Modular design allows for flexible integration
- Focuses on core Ethereum protocol components
- Implements fundamental data structures and processing mechanisms

## Technologies Used

### Programming Language
- Python 3

### Core Libraries and Modules
- Standard Python Libraries:
  - `typing` for type hints
  - `collections` for data structures
  - Built-in data manipulation modules

### Cryptography and Blockchain Specific
- RLP (Recursive Length Prefix) encoding/decoding
- Merkle Patricia Trie implementation
- Ethereum-related data structures and transaction processing

### Development Tools
- Python standard development tools
- Potential testing framework (based on presence of `trietest.py`)

### Theoretical Foundations
- Blockchain data structure concepts
- Ethereum protocol specifications

## Additional Notes

### Cryptographic Primitives and Transaction Handling

This implementation provides low-level cryptographic and transaction processing utilities primarily focused on Ethereum-like blockchain transaction management. Key characteristics include:

#### RLP Encoding and Decoding
- Supports Recursive Length Prefix (RLP) encoding and decoding
- Handles various data types including integers, strings, and lists
- Provides flexible binary conversion and encoding mechanisms
- Supports encoding/decoding of data up to 2^256 in size

#### Transaction Processing
- Implements a `Transaction` class with comprehensive transaction lifecycle management
- Supports transaction signing and signature verification
- Handles transaction serialization and deserialization
- Includes methods for:
  - Transaction initialization
  - Parsing raw transaction data
  - Signing transactions with cryptographic keys
  - Generating transaction hashes
  - Extracting sender information

### Security Considerations
- Uses cryptographic primitives from pybitcointools
- Implements ECDSA signature recovery
- Handles hexadecimal and binary data transformations
- Provides low-level cryptographic operations suitable for blockchain-related development

### Limitations
- Represents an early/experimental implementation of Ethereum transaction processing
- Lacks comprehensive error handling
- Minimal documentation within the source code
- Intended for educational or research purposes rather than production use

### Compatibility
- Dependent on external `pybitcointools` library
- Python 2.x implementation (note potential compatibility issues with modern Python versions)

## Contributing

We welcome contributions to this project! Here are some guidelines to help you contribute effectively:

### How to Contribute

1. **Fork the Repository**: Create a fork of the project on GitHub.

2. **Create a Branch**: 
   - Create a new branch for your feature or bugfix
   - Use a clear and descriptive branch name
   - Example: `feature/add-new-transaction-type` or `bugfix/resolve-parsing-error`

### Contribution Guidelines

#### Code Style
- Follow Python PEP 8 style guidelines
- Use meaningful variable and function names
- Add type hints where appropriate
- Maintain consistent indentation (4 spaces)

#### Testing
- All new features or bugfixes must include corresponding tests
- Run existing test suite using the project's testing framework
- Ensure all tests pass before submitting a pull request
- Add new test cases to cover added functionality

### Submitting a Pull Request

1. Ensure your code follows the project's coding standards
2. Write clear, concise commit messages
3. Include a detailed description of your changes in the pull request
4. Reference any related issues in your PR description

### Code of Conduct

- Be respectful and considerate of other contributors
- Collaborate constructively
- Provide constructive feedback

### Questions or Concerns?

If you have any questions about contributing, please open an issue in the repository for discussion.

## License

This project is currently unlicensed. Without a specific license, the default copyright laws apply:

- No one else can reproduce, distribute, or create derivative works from this code
- The original authors retain all rights to the code
- Others cannot legally use, modify, or share the code without explicit permission

If you intend to use or contribute to this project, it is recommended to contact the repository owners to clarify the licensing terms or to establish an open-source license that defines usage permissions.