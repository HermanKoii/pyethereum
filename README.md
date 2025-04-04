# Blockchain Utility Library

## Project Overview

This Python library provides essential utilities for blockchain and cryptocurrency applications, focusing on core cryptographic and data encoding functions. The library offers tools for:

- Recursive Length Prefix (RLP) encoding and decoding
- Transaction handling and serialization
- Binary conversion and manipulation
- Cryptographic operations

### Key Features

- RLP encoding and decoding for complex data structures
- Transaction creation, signing, and serialization
- Low-level binary and numeric conversion utilities
- Minimal dependencies for lightweight integration

## Installation

### Prerequisites

- Python 2.7+ or Python 3.x
- `pybitcointools` library

### Install via pip (Recommended)

```bash
pip install blockchain-utility-lib
```

### Manual Installation

```bash
git clone https://github.com/your-repo/blockchain-utility-lib.git
cd blockchain-utility-lib
python setup.py install
```

## API Reference

### RLP Module (`rlp.py`)

#### Functions

- `binary_length(n: int) -> int`
  - Calculates the binary length of a number
  - Returns the number of bytes required to represent the integer
  
  Example:
  ```python
  length = binary_length(1024)  # Returns 2
  ```

- `to_binary(n: int, L: Optional[int] = None) -> str`
  - Converts an integer to its binary representation
  - `L`: Optional length specification
  
  Example:
  ```python
  binary = to_binary(255)  # Returns a binary string
  ```

- `encode(data: Union[int, str, list]) -> str`
  - Encodes data using Recursive Length Prefix (RLP) encoding
  - Supports integers, strings, and lists
  
  Example:
  ```python
  encoded = encode([1, 2, 3])  # RLP-encodes the list
  ```

- `decode(encoded_data: str) -> Any`
  - Decodes RLP-encoded data
  
  Example:
  ```python
  decoded = decode(some_encoded_data)
  ```

### Transaction Module (`transactions.py`)

#### `Transaction` Class

- `__init__(nonce, to, value, fee, data)`
  - Creates a new transaction
  
  Example:
  ```python
  tx = Transaction(nonce=1, to='address', value=100, fee=1, data='')
  ```

- `sign(private_key: str) -> Transaction`
  - Signs the transaction with a private key
  
  Example:
  ```python
  signed_tx = tx.sign(private_key)
  ```

- `serialize() -> str`
  - Serializes the transaction for transmission
  
- `hash() -> str`
  - Generates the transaction hash

## Repository Structure

- `rlp.py`: Recursive Length Prefix encoding utilities
- `transactions.py`: Transaction handling and cryptographic operations
- `trie.py`: Merkle Patricia Tree implementation
- `processblock.py`: Blockchain block processing utilities
- `trietest.py`: Test suite for trie implementation

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Running Tests

```bash
python -m unittest discover tests
```

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Disclaimer

This library is for educational and developmental purposes. Use in production environments requires thorough testing and security audits.