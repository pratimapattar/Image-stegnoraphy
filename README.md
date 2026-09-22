LSB Image Steganography System
A command-line based Image Steganography application developed in C using the Least Significant Bit (LSB) substitution technique. The tool allows users to securely conceal any secret text file within a 24-bit uncompressed BMP image and extract it back with zero loss of data or noticeable image distortion.

Features
Encode Secret Data: Conceal arbitrary text payloads inside carrier BMP images without visual degradation.

Decode Secret Data: Extract and reconstruct the concealed secret file from the stego image.

Capacity Validation: Automatically verifies if the carrier image has sufficient pixel data to hold the secret payload before encoding.

Header Integrity Protection: Skips and preserves the standard 54-byte BMP header to keep the output image readable by standard image viewers.

Authentication via Magic String: Embeds and checks a predefined signature to ensure only valid stego images can be decoded.

Dynamic File Handling: Stores and retrieves file extension sizes, extensions, and file lengths dynamically.

Technologies Used
Programming Language: C
Compiler: GCC
Operating System: Linux
Carrier Format: 24-bit Uncompressed BMP Image Format

C Concepts Used
This project demonstrates practical usage of:
Bitwise Operations: Shifting (<<, >>), bitwise AND (&), and bitwise OR (|) to manipulate individual bits.
Structures and Typedefs: Organizing file pointers, image metadata, and configuration options.
Pointers: Memory referencing, buffer indexing, and byte-level manipulation.
File Handling: Binary file I/O (fopen, fread, fwrite, fseek, ftell).
Enums & Custom Types: Managing operation status codes (Status, OperationType).
Command-Line Arguments: Parsing runtime arguments (argc, argv).
Modular Programming: Separation of encoding and decoding logic into isolated modules.

Project Structure
Image-Steganography/
│
├── test_encode.c        # Main driver and CLI parser
├── encode.c             # Encoding engine and bitwise substitution logic
├── encode.h             # Encoding structures and function prototypes
├── decode.c             # Decoding engine and bit extraction logic
├── decode.h             # Decoding structures and function prototypes
├── common.h             # Shared constants and magic string definitions
├── types.h              # Status codes and custom enum definitions
├── beautiful.bmp        # Clean sample carrier image (24-bit BMP)
├── secret.txt           # Sample secret text payload
├── Documentation.txt    # Project workflow and design notes
└── README.md

How to Compile
Clone the repository, navigate to the project directory, and compile the source files using GCC:

Bash
gcc *.c -o stego

How to Run
1. Encoding (Concealing Data)
Syntax:
Bash
./stego -e <source_image.bmp> <secret_file.txt> [output_stego.bmp]
Example:
Bash
./stego -e beautiful.bmp secret.txt stego.bmp

3. Decoding (Extracting Data)
Syntax:
Bash
./stego -d <stego_image.bmp> [output_secret_file.txt]
Example:
Bash
./stego -d stego.bmp output.txt

Application Flow
Start (Command Line)
  |
  v
Validate Arguments (-e / -d)
  |
  +---- [-e] Encode Mode
  |       |
  |       +---> Check Image Capacity
  |       +---> Copy 54-byte BMP Header
  |       +---> Encode Magic String (#*)
  |       +---> Encode Secret File Extension & Size
  |       +---> Encode Secret File Size
  |       +---> Encode Secret File Payload into LSBs
  |       +---> Copy Remaining Image Bytes
  |       +---> Output: stego.bmp
  |
  +---- [-d] Decode Mode
  |       |
  |       +---> Skip BMP Header
  |       +---> Verify Magic String
  |       +---> Decode Secret File Extension & Size
  |       +---> Decode Secret File Size
  |       +---> Extract Secret Bytes from LSBs
  |       +---> Output: Decoded text file
  |
  v
Done

Learning Outcomes
Through this project, I gained practical experience in:
Implementing bit-level data manipulation using C bitwise operators.
Understanding image file architectures, specifically the 24-bit uncompressed BMP format and its header structure.
Performing binary file I/O operations for reading and writing raw byte streams.
Implementing data integrity checks and capacity calculations before execution.
Designing modular, multi-file C architectures for real-world cryptographic applications.
Debugging memory and bit-level corruption issues in a Linux environment.

Author
Pratima C Pattar
