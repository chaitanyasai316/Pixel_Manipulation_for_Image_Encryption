# PRODIGY_CS_02

## Task-02

# BMP Image Encryption/Decryption in C

This program demonstrates how to read, encrypt, decrypt, and write a BMP image file using basic pixel manipulation. It operates on uncompressed 24-bit BMP files, where each pixel is represented by RGB (Red, Green, Blue) values. The program allows encryption and decryption of images by applying a simple key-based mathematical operation on the pixel values.

## Features

- **Read BMP image files**: Reads uncompressed 24-bit BMP images and extracts pixel data.
- **Encrypt/Decrypt images**: Modifies pixel values by adding or subtracting a user-provided key to encrypt or decrypt the image.
- **Write BMP image files**: Saves the modified (encrypted or decrypted) image as a new BMP file.

## How It Works

1. **Reading the BMP file**: The program reads the BMP file header and extracts important metadata such as the width, height, and pixel data of the image. Padding bytes are handled to ensure correct alignment.
   
2. **Encryption/Decryption**: 
   - **Encryption**: For each pixel, the program adds the key to the RGB values, ensuring the result remains within the 0-255 range.
   - **Decryption**: The program subtracts the key from each pixel's RGB values, restoring the original image if the correct key is used.

3. **Writing the BMP file**: The modified pixel data is written back into a new BMP file with the correct headers, including padding to align rows properly.

## Functions

### `Pixel* read_image(const char *filename, int *width, int *height, int *padding)`
Reads an uncompressed 24-bit BMP image file and returns the pixel data as a `Pixel` array.

- **Parameters**:
  - `filename`: Path to the BMP file.
  - `width`: Pointer to an integer that will store the width of the image.
  - `height`: Pointer to an integer that will store the height of the image.
  - `padding`: Pointer to an integer that will store the number of padding bytes in each row.

- **Returns**: 
  - An array of `Pixel` structures representing the image's pixel data.

### `void write_image(const char *filename, Pixel *pixels, int width, int height, int padding)`
Writes a BMP image file with the given pixel data.

- **Parameters**:
  - `filename`: Path to save the new BMP file.
  - `pixels`: Array of pixel data to write.
  - `width`: Width of the image.
  - `height`: Height of the image.
  - `padding`: Number of padding bytes per row.

### `void encrypt_decrypt_image(Pixel *pixels, int width, int height, int key, int mode)`
Encrypts or decrypts the image by applying a key-based mathematical operation on the pixel data.

- **Parameters**:
  - `pixels`: Array of pixel data to encrypt or decrypt.
  - `width`: Width of the image.
  - `height`: Height of the image.
  - `key`: Integer key used for encryption/decryption.
  - `mode`: Operation mode (`1` for encryption, `0` for decryption).

## Usage

### Compile the program

To compile the program, use a C compiler such as `gcc`. For example:

```bash
gcc bmp_encrypt_decrypt.c -o bmp_encrypt_decrypt
