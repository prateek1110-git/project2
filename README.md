# Huffman Coding Compression and Decompression Project

This project implements Huffman coding, a popular method for lossless data compression. The program includes functions to compress a file using Huffman encoding and then decompress the file back to its original state. Huffman coding is efficient for encoding data with varying frequency of characters, achieving better compression ratios than fixed-length encoding schemes.

## Introduction
This program leverages Huffman coding to compress and decompress files. It efficiently encodes data by assigning variable-length codes to characters based on their frequencies.

## Requirements
- C++ compiler (MinGW recommended)
- Basic understanding of data structures and algorithms

## Features
- **Compression**: Reads a file, constructs a frequency table for its characters, builds a Huffman tree, and generates the Huffman codes. The compressed data is written to an output file along with a header containing the Huffman codes.
- **Decompression**: Reads the compressed file, extracts the Huffman codes from the header, and reconstructs the original file from the compressed bitstream.

## Components
### Data Structures
- **Tree**: Represents a node in the Huffman tree.
  - `int frequency`: The frequency of the character.
  - `unsigned char character`: The character the node represents.
  - `Tree *left, *right`: Pointers to the left and right child nodes.
- **TreeComparator**: A comparator class used to order nodes in the priority queue based on their frequencies.

### Functions
- **buildHuffmanTree**: Constructs the Huffman tree from a frequency table using a priority queue.
- **toBinary**: Converts a character to its binary string representation.
- **traverseHuffmanTree**: Recursively traverses the Huffman tree to generate Huffman codes for each character.
- **readFileIntoBuffer**: Reads a file into a buffer. Returns a pointer to the buffer and the size of the buffer.
- **writeFileFromBuffer**: Writes data from a buffer to a file.
- **convertToVector**: Converts a frequency map to a vector of pairs.
- **getHuffmanBitstring**: Generates a bitstring for the entire file using Huffman codes and pads it to a multiple of 8 bits.
- **getBufferFromString**: Converts a bitstring to a buffer of bytes.
- **getStringFromBuffer**: Converts a buffer of bytes to a bitstring.
- **getDecodedBuffer**: Decodes a bitstring using Huffman codes to reconstruct the original data.
- **writeHeader**: Writes Huffman codes and padding information to the output file.
- **readHeader**: Reads Huffman codes and padding information from the input file.
- **compressFile**: Manages the entire process of reading a file, generating Huffman codes, compressing the file, and writing the compressed data to an output file.
- **decompressFile**: Manages the entire process of reading a compressed file, extracting Huffman codes, and reconstructing the original file.

## Huffman Tree Construction
The buildHuffmanTree function creates a Huffman tree from a frequency table. It uses a priority queue to ensure that nodes with the lowest frequencies are combined first.

## Code Generation
The traverseHuffmanTree function recursively traverses the Huffman tree to generate a unique binary code for each character, stored in a map.

## Compression
The compressFile function orchestrates the compression process:

Reads the input file into a buffer.
Builds the frequency table.
Constructs the Huffman tree and generates the codes.
Creates a bitstring for the entire file using the Huffman codes.
Pads the bitstring to a multiple of 8 bits.
Writes the Huffman codes and the bitstring to the compressed file.
Decompression
The decompressFile function handles the decompression:

Reads the compressed file into a buffer.
Extracts Huffman codes and padding information from the header.
Converts the remaining data in the buffer back into the original bitstring.
Uses Huffman codes to decode the bitstring and reconstruct the original file.
Header Format
The header of the compressed file contains:

The number of padding bits.
The number of unique characters.
Each character followed by the length of its Huffman code and the code itself.

## Conclusion
This Huffman compression and decompression program is a practical implementation of one of the most efficient lossless compression algorithms. By leveraging variable-length codes, it effectively reduces the size of files with varying character frequencies. This program serves as a robust tool for compressing and decompressing files using Huffman coding.