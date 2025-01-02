# RSA-Programming-project
## Objective

The primary objective of this code is to implement and demonstrate the core functionalities of the RSA (Rivest-Shamir-Adleman) cryptosystem. It achieves this by reading RSA parameters and messages from an input file, calculating the private key using the provided public key components, performing RSA encryption on a given plaintext, and decrypting a specified ciphertext. The code begins by reading two prime numbers (p and q) and a public exponent (e) from the input file, then calculates the RSA modulus n (n = p * q) and Euler's totient function φ(n), subsequently computing the private key d using the modular multiplicative inverse of e mod φ(n). It encrypts the plaintext message and decrypts the ciphertext using the calculated private key. The results, including the private key, encrypted plaintext, and decrypted ciphertext, are then written to an output file named "output.txt."

### Skills Learned

- Understanding Cryptography: I gained foundational knowledge of cryptographic principles, particularly asymmetric encryption.
  
- Mathematical Concepts: I applied mathematical concepts such as modular arithmetic and prime factorization in practical scenarios.
  
- Key Management: I learned how to generate and manage public and private keys securely.
  
- BigInteger Manipulation: I worked with Java's `BigInteger` class for handling large numbers, which are essential in cryptographic applications.
  
- Algorithm Implementation: I gained experience in implementing algorithms from scratch without relying on external libraries or frameworks.
  
- Problem-Solving Skills: I enhanced my problem-solving abilities by tackling challenges associated with encryption and decryption processes.

### Tools Used

1. Java Development Kit (JDK): The project is written in Java, so I used the IntelliIDEA JDK for compiling and running the code.

2. BigInteger class: This Java class is heavily utilized for handling large numbers required in RSA calculations.

3. File I/O classes: The project uses BufferedReader and BufferedWriter for reading input and writing output to files.

4. Exception handling: Try-catch blocks are employed to manage potential errors during file operations and calculations.

5. Hexadecimal conversion: The code converts between hexadecimal strings and BigInteger objects.

6. Command-line interface: The program is designed to be run from the command line, reading from input.txt and writing to output.txt.


## Code and Implementation
Certainly! I'll explain the RSA implementation code section by section:

1. Imports and Class Declaration:
```java
import java.io.*;
import java.math.BigInteger;


The code imports necessary Java libraries for file I/O and big integer operations, which are crucial for RSA cryptography.
```
2. Utility Methods
```

public static BigInteger modInverse(BigInteger e, BigInteger phi) {
    return e.modInverse(phi);
}

public static BigInteger rsaEncrypt(BigInteger plaintext, BigInteger e, BigInteger n) {
    return plaintext.modPow(e, n);
}

public static BigInteger rsaDecrypt(BigInteger ciphertext, BigInteger d, BigInteger n) {
    return ciphertext.modPow(d, n);
}
```
These methods implement core RSA operations:
- `modInverse`: Calculates the modular multiplicative inverse, used to find the private key.
- `rsaEncrypt`: Performs RSA encryption using the formula c = m^e mod n.
- `rsaDecrypt`: Performs RSA decryption using the formula m = c^d mod n.

3. Main Method:
The `main` method contains the primary logic:

a. File Reading:
```java
BufferedReader reader = new BufferedReader(new FileReader("input.txt"));

```
This section reads the input file and checks for completeness.

b. Input Parsing:
```java
BigInteger p = new BigInteger(pStr.trim(), 16);
BigInteger q = new BigInteger(qStr.trim(), 16);

```
Converts hexadecimal strings to `BigInteger` objects.

c. RSA Calculations:
```java
BigInteger n = p.multiply(q);
BigInteger phi = (p.subtract(BigInteger.ONE)).multiply(q.subtract(BigInteger.ONE));
BigInteger d = modInverse(e, phi);
```
Calculates the RSA parameters: modulus (n), Euler's totient (phi), and private key (d).

d. Encryption and Decryption:
```java
BigInteger encryptedPlaintext = rsaEncrypt(plaintext, e, n);
BigInteger decryptedCiphertext = rsaDecrypt(ciphertext, d, n);
```
Applies RSA encryption and decryption operations.

e. Output Writing:
```java
BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"));
writer.write(d.toString(16) + "\n");

```
Writes the results (private key, encrypted plaintext, decrypted ciphertext) to the output file in hexadecimal format.

f. Exception Handling:
```java
catch (FileNotFoundException e) {
    
} catch (IOException e) {
    
} catch (Exception e) {
    
}
```
Handles various exceptions that might occur during file operations or calculations.

## Explanation of input and output files:

Input file (input.txt):

C34B79A3D1D187F51A2322E7: Prime number p (in hexadecimal)

D5F47D7A90A29E71A7BDB4EF: Prime number q (in hexadecimal)

010001: Public exponent e (in hexadecimal, commonly 65537 in decimal)

5468697320697320612074657374: Plaintext to be encrypted (in hexadecimal)

3B21541F8918B7A1E7C50A9E: Ciphertext to be decrypted (in hexadecimal)
![Screenshot 2025-01-02 012341](https://github.com/user-attachments/assets/cc398b49-99bb-4455-9695-73dee4be878c)


Output file (output.txt):

6e6106a26230d5f0e6b7f0fbde07c1ba535a6824d7f97e9: Calculated private key d (in hexadecimal)

7f8f42cc6113a53c65a1fad77dfd4a2136de31f8a0c01d62: Encrypted plaintext (in hexadecimal)

63c217c104f097e841be3e4bb755daa6b0970af630044214: Decrypted ciphertext (in hexadecimal)

The program reads the RSA parameters and messages from the input file, performs the necessary calculations (including finding the private key), encrypts the given plaintext, decrypts 

the given ciphertext, and writes the results to the output file. All values in both input and output files are represented in hexadecimal format.
![Screenshot 2025-01-02 012355](https://github.com/user-attachments/assets/d35fea91-a579-4bbb-af52-d243078c5b69)
