# Simple Blockchain Implementation in Go

This repository contains a basic implementation of a blockchain in Go. The code provides a minimalistic approach to understanding how a blockchain works by creating a chain of blocks where each block contains some data, a timestamp, a hash of the previous block, and its own hash.

## Overview

The main components of the implementation are:

1. **Block**: A structure that represents each block in the blockchain. It contains:
   - `Timestamp`: The time when the block was created.
   - `Data`: The data stored in the block.
   - `PrevBlockHash`: The hash of the previous block in the chain.
   - `Hash`: The hash of the current block.

2. **Blockchain**: A structure that represents the blockchain itself. It contains a slice of pointers to `Block` structures.

3. **NewBlock**: A function to create a new block. It takes data and the hash of the previous block as input, and returns a pointer to the new block.

4. **SetHash**: A method of the `Block` structure that calculates the hash of the block by combining its `PrevBlockHash`, `Data`, and `Timestamp`.

5. **AddBlock**: A method of the `Blockchain` structure that adds a new block to the blockchain.

6. **NewGenesisBlock**: A function that creates the first block in the blockchain, known as the genesis block.

7. **NewBlockchain**: A function that creates a new blockchain with the genesis block.

## How It Works

1. **Creating a Blockchain**:
   - The `NewBlockchain` function initializes a new blockchain with the genesis block.

2. **Adding Blocks**:
   - The `AddBlock` method allows you to add new blocks to the blockchain. Each new block contains the hash of the previous block, thus maintaining the chain.

3. **Hash Calculation**:
   - The `SetHash` method calculates the hash of each block by concatenating the previous block's hash, the block's data, and its timestamp, and then applying the SHA-256 hash function.

## Usage

The main function demonstrates the creation of a new blockchain and the addition of blocks to it. It then prints out the details of each block, including the previous hash, the data, and the hash of the block.

```go
func main() {
    bc := NewBlockchain()

    bc.AddBlock("Send 1 BTC to Ivan")
    bc.AddBlock("Send 2 more BTC to Ivan")

    for _, block := range bc.blocks {
        fmt.Printf("Prev. hash: %x\n", block.PrevBlockHash)
        fmt.Printf("Data: %s\n", block.Data)
        fmt.Printf("Hash: %x\n", block.Hash)
        fmt.Println()
    }
}
```

## Conclusion

This simple implementation is designed for educational purposes to help understand the basic concepts of a blockchain. It lacks many features of a production-level blockchain such as decentralized consensus, proof-of-work, and security mechanisms. Nonetheless, it serves as a foundational example for those new to blockchain technology.
