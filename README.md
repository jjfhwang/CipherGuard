# CipherGuard

## Description

CipherGuard is a comprehensive collection of cryptography algorithms, protocols, and implementations written in TypeScript. Its primary purpose is to provide a secure and reliable foundation for developers to build secure applications by offering a wide range of cryptographic tools. CipherGuard aims to be easily accessible, well-documented, and thoroughly tested, allowing developers to quickly integrate robust cryptographic solutions into their projects without needing to be cryptography experts. The value proposition lies in its ease of use, security focus, and comprehensive nature, saving developers significant time and effort while increasing the overall security posture of their applications.

## Features

*   **AES Encryption/Decryption:** Implementation of the Advanced Encryption Standard (AES) algorithm with various key sizes (128, 192, 256 bits) and modes of operation (CBC, CTR, GCM). Provides strong symmetric encryption for data confidentiality.
*   **RSA Key Generation and Encryption/Decryption:** Offers RSA key pair generation and asymmetric encryption/decryption capabilities. Supports different key sizes and padding schemes for secure communication and digital signatures.
*   **Hashing Algorithms (SHA-256, SHA-512):** Includes secure hashing algorithms like SHA-256 and SHA-512 for data integrity verification and password storage. Provides collision resistance and one-way functionality.
*   **Elliptic Curve Cryptography (ECC):** Implements ECC algorithms like ECDSA and ECDH for key exchange and digital signatures. Offers high security with smaller key sizes compared to RSA.
*   **Random Number Generation:** Provides a cryptographically secure pseudorandom number generator (CSPRNG) for generating random keys, initialization vectors (IVs), and other security-sensitive values.

## Installation

To install CipherGuard and its dependencies, follow these steps:

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/CipherGuard.git
    cd CipherGuard
    ```

2.  **Install dependencies using npm or yarn:**

    ```bash
    npm install
    # or
    yarn install
    ```

3.  **(Optional) Build the project:**

    ```bash
    npm run build
    # or
    yarn build
    ```

    This step compiles the TypeScript code into JavaScript, which is necessary for running the examples and using the library in your projects.

## Usage

Here are some examples of how to use CipherGuard in your TypeScript projects:

**AES Encryption/Decryption:**

```typescript
import { AES } from './src/aes'; // Adjust path based on your project structure

async function aesExample() {
  const key = 'This is a 256-bit key!'; // Replace with a secure key
  const iv = 'InitializationVe'; // 16-byte IV for CBC/CTR

  const plaintext = 'This is the message to be encrypted.';

  try {
    const ciphertext = await AES.encrypt(plaintext, key, iv, 'cbc'); // 'cbc' or 'ctr' or 'gcm'
    console.log('Ciphertext:', ciphertext);

    const decryptedText = await AES.decrypt(ciphertext, key, iv, 'cbc');
    console.log('Decrypted Text:', decryptedText);
  } catch (error) {
    console.error('AES Error:', error);
  }
}

aesExample();
```

**RSA Key Generation and Encryption/Decryption:**

```typescript
import { RSA } from './src/rsa'; // Adjust path based on your project structure

async function rsaExample() {
  try {
    const { publicKey, privateKey } = await RSA.generateKeys(2048); // Key size: 2048 bits

    const message = 'This is a secret message!';

    const encryptedMessage = await RSA.encrypt(message, publicKey);
    console.log('Encrypted Message:', encryptedMessage);

    const decryptedMessage = await RSA.decrypt(encryptedMessage, privateKey);
    console.log('Decrypted Message:', decryptedMessage);
  } catch (error) {
    console.error('RSA Error:', error);
  }
}

rsaExample();

```

**Hashing with SHA-256:**

```typescript
import { SHA256 } from './src/sha256'; // Adjust path based on your project structure

function sha256Example() {
  const data = 'This is the data to be hashed.';
  const hash = SHA256.hash(data);
  console.log('SHA-256 Hash:', hash);
}

sha256Example();
```

**Important Considerations:**

*   **Key Management:**  Securely manage your cryptographic keys.  Do not hardcode keys directly into your application. Use secure key storage mechanisms.
*   **Initialization Vectors (IVs):** Always use unique and unpredictable IVs for each encryption operation when using block cipher modes like CBC or CTR.
*   **Error Handling:** Implement proper error handling to catch and address potential cryptographic exceptions.
*   **Security Audits:** Regularly audit your code and cryptographic implementations to identify and address potential vulnerabilities.

## Contributing

We welcome contributions to CipherGuard! To contribute, please follow these guidelines:

1.  **Fork the repository:** Create your own fork of the CipherGuard repository on GitHub.

2.  **Create a branch:** Create a new branch in your fork for your contribution.  Use a descriptive name for your branch.

    ```bash
    git checkout -b feature/your-feature-name
    ```

3.  **Implement your changes:** Make your changes, adhering to the project's coding style and conventions. Ensure your code is well-documented and includes unit tests.

4.  **Run tests:** Ensure all tests pass before submitting your contribution.

    ```bash
    npm test
    # or
    yarn test
    ```

5.  **Commit your changes:** Commit your changes with clear and concise commit messages.

    ```bash
    git commit -m "Add: Implemented new feature"
    ```

6.  **Push to your fork:** Push your branch to your forked repository.

    ```bash
    git push origin feature/your-feature-name
    ```

7.  **Create a pull request:** Submit a pull request from your branch to the main CipherGuard repository.  Provide a detailed description of your changes and the problem they solve.

8.  **Code Review:** Your pull request will be reviewed by the project maintainers.  Address any feedback or suggestions provided during the review process.

## License

CipherGuard is licensed under the MIT License. See the `LICENSE` file for more information.
