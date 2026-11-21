# Computational_Theory

This repository contains my work for the Computational Theory module assessment (Winter 2026/27).

The assessment is based on the Secure Hash Standard (SHA-256) and involves investigating, developing and implementing the SHA-256 cryptographic hash algorithm in Python.

This Repository contain six problems, covering the Representation of SHA-256 data, bitwise operations, generation of constants, message padding and parsing, the compression function, and the complete SHA-256 implementation.

Each problem is documented in the Jupyter notebook, problems.ipynb, using Markdown explanations, Python code examples, testing and relevant references.

Status: Work in progress (TBC)

## Problems 
### Problem 1 - Representing SHA-256 Data
Status: Completed

This problem involved investigating how the different types of data used in SHA-256 can be represented in Python before implementing the algorithm.

I explored the use of Python integers to represent 32-bit words, using bitwise masks to ensure values remain within the required 32-bit range. Lists were used to store sequences of 32-bit words, while string were converted into bytes using UTF-8 encoding to represent input messages.

I also investigated how to represent 512-bit message blocks and 256-bit hash values using Python's bytes data type. Finally, I explored big-endian integer representation using Python's int.from_bytes() method.

Small Python code examples were included throughout to demonstrate each representation and explain why the chosen data types are appropriate for SHA-256.

### Problem 2 - SHA-256 Bitwise Operations
Status: Completed

This problem involved implementing the six Boolean and bitwise functions used within the SHA-256 algorithm. NumPy was used to represent values as 32-bit unsigned integers (np.uint32), ensuring that the operations follow the required 32-bir format.

I first implemented the Ch(x, y, z) function, which selects bits from either y or z depending on the corresponding bits in x. Then I implemented the Maj(x, y, z) function, which determines the majority bit value across three inputs.

Next, I implemented...
- Sigma0(x) -> combines right rotations of 2, 13 and 22 bits using XOR.
- Sigma1(x) -> combines right rotations of 6, 11 and 25 bits using XOR.

These functions are used during SHA-256 compression process to mis and transform the working variables.

Finally, I implemented...
- sigma0(x) -> combines right rotations of 7 and 18 bits with a logical right shift of 3 bits.
- sigma1(x) -> combines right rotations of 17 and 19 bits with a logical right shift of 10 bits.

Each functions includes a docstring or explanatory comments, alongside a Markdown explanation describing its purpose and operation. Testing was carried out using different inputs, including all-zero values, all-one values and mixed bit patterns. Assertions were used to compared the outputs against the expected hexadecimal values and verify that the functions behaved as intended.

### Problem 3 - Generating SHA-256 Round Constants
Status: Completed

This problem involved generating 64 round constants used in the SHA-256 algorithm. These constants are derived from the fractional parts of the cube roots of the first 64 prime numbers, as defined in the Secure Hash Standard.

I first implemented the primes(n) function to generate the first n prime numbers. This functions checks each number to determine whether it is prime and stores the result in a list. Then, I used the function to generate the first 64 prime numbers required for SHA-256.

Next, I used NumPy's np.cbrt() function to calculate the cube roots of those 64 prime numbers. The resulting values were used to extract their fractional parts and convert them into 32-bit unsigned integers.

Finally, I displayed the generated constants in hexadecimal form and compared them against the official SHA-256 round constants provided in the Secure Hash Standard to verify their accuracy.

## Requirements

This project uses Python and Jupyter Notebook, alongside NumPy for 32-bit unsigned integer operations.
The required Python packages are listed in requirements.txt.

## Getting Started

-1. Clone the repository
- git clone <git@github.com:CaoimheKelly26/Computational_Theory.git>
- cd <Computational_Theory>
- 2.Install the required dependencies
- pip install -r requirements.txt
- Launch the Jupyter Notebook
- jupyter notebook problems.ipynb

## References

The following sources were consulted during Problem 1 to help understand the representation of SHA-256 data and its underlying concepts.

- https://www.tutorialspoint.com/cryptography/sha_512_algorithm.htm -> researching 512-bit message blocks.
- https://www.ssldragon.com/blog/sha-256-algorithm/ -> understanding final 256-bit hash value
- https://www.geeksforgeeks.org/dsa/little-and-big-endian-mystery/ -> understanding big-endian byte ordering

The following sources were consulted during Problem 2 to help understand bitwise operations.

- https://deepwiki.com/in3rsha/sha256-animation/3.3-choice-and-majority-functions#choice-and-majority-functions -> researching choice and majority functions

- https://deepwiki.com/in3rsha/sha256-animation/3.3-choice-and-majority-functions#purpose-of-the-choice-and-majority-functions -> researching choice and majority functions

- https://deepwiki.com/in3rsha/sha256-animation/3.3-choice-and-majority-functions#the-choice-function-ch -> researching choice function

- https://deepwiki.com/in3rsha/sha256-animation/3.3-choice-and-majority-functions#the-majority-function-maj -> researching majority function

- https://deepwiki.com/in3rsha/sha256-animation/3.2-sigma-functions#uppercase-sigma-functions-0-1 -> researching and understanding Sigma0(x)

- https://deepwiki.com/in3rsha/sha256-animation/3.2-sigma-functions#1-usigma1-function -> researching and understand Sigma1(x)

- https://deepwiki.com/in3rsha/sha256-animation/3.2-sigma-functions#lowercase-sigma-functions-0-1 -> researching lowercase sigma 0-1 functions

- https://deepwiki.com/in3rsha/sha256-animation/3.2-sigma-functions#0-sigma0-function -> researching sigma0(x) functins

- https://deepwiki.com/in3rsha/sha256-animation/3.2-sigma-functions#1-sigma1-function -> researching sigma1(x) function

- The following sources were consulted during Problem 3 to help understand bitwise operations.

- https://en.wikipedia.org/wiki/SHA-2 -> Researching and understanding SHA-256

- https://www.ssldragon.com/blog/sha-256-algorithm/ -> Researching and understanding SHA-256

- https://deepwiki.com/in3rsha/sha256-animation/4.1-sha-256-constants#what-are-sha-256-constants -> Understanding prime constants

- https://www.cuemath.com/algebra/cubes-and-cube-roots/ -> understanding cube roots

- https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf?utm_source=chatgpt.com -> SHA-256 constants

- https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf -> Secure Hash Standard
