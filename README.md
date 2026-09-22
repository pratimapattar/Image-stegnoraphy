# LSB Image Steganography

A command-line based Image Steganography project developed in **C** using the **Least Significant Bit (LSB) substitution technique**.
This application allows users to hide a secret file inside a **24-bit uncompressed BMP image** and later extract the hidden data from the stego image.

## Features
- Hide a secret file inside a BMP image using LSB substitution.
- Extract the hidden file from a stego image.
- Validate whether the carrier image has enough capacity to store the secret data.
- Preserve the BMP header while encoding data.
- Use a magic string to identify and validate stego images.
- Store and retrieve the secret file extension dynamically.
- Store and retrieve the secret file size dynamically.
- Perform binary file operations for image and secret-file processing.
- Command-line interface for encoding and decoding operations.

## Technologies Used
- **Programming Language:** C
- **Compiler:** GCC
- **Operating System:** Linux
- **Image Format:** 24-bit Uncompressed BMP
- **Development Environment:** VS Code / Linux Terminal

## C Concepts Used
This project demonstrates practical implementation of several C programming concepts:
- **Bitwise Operations** – Manipulating individual bits using `&`, `|`, `<<`, and `>>`.
- **Pointers** – Working with memory addresses, buffers, and file data.
- **Structures and typedef** – Managing encoding and decoding information.
- **File Handling** – Using `fopen()`, `fread()`, `fwrite()`, `fseek()`, `ftell()`, and related functions.
- **Command-Line Arguments** – Processing `argc` and `argv`.
- **Enumerations and Custom Types** – Managing operation and status values.
- **Modular Programming** – Separating encoding, decoding, and common functionality into different source files.
- **Binary File Processing** – Reading and writing image data at the byte level.

## How LSB Steganography Works
LSB steganography hides information by modifying the **Least Significant Bit** of the image pixel data.

For example:
```text
Original pixel byte : 10110110
Secret data bit     :        1
Modified pixel byte : 10110111
