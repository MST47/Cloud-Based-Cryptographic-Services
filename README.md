# Cloud-Based-Cryptographic-Services
Implemented a Proof of Concept (PoC) for various cryptography-related services on AWS
## Overview
This repository provides code for basic client-side encryption using JavaScript and the CryptoJS library. Below is a detailed breakdown of the implementation.

HTML Structure
The HTML file includes:

The necessary CryptoJS library.
Sections for plaintext input, key input, encrypted text output, and decryption sections.
Encryption Function
The encrypt function performs the following steps:

Retrieves the plaintext and key values from the corresponding HTML elements.
Uses CryptoJS.AES.encrypt to encrypt the plaintext with the provided key, utilizing a key size of 256 bits.
Converts the ciphertext into a hexadecimal string by iterating through each character and converting its char code to hexadecimal format, padding with zeros if necessary.
Displays the encrypted text in the designated output area.
Decryption Function
The decrypt function follows these steps:

Retrieves the ciphertext from the HTML element.
Iterates through the ciphertext string in pairs of characters, converting each hexadecimal pair back to its corresponding ASCII character code using parseInt.
Uses the decrypted ASCII string and the key to decrypt the ciphertext with CryptoJS.AES.decrypt.
Displays the decrypted plaintext in the designated output area.
AES-256 Encryption with AWS KMS
Signing AWS Requests with Signature Version 4
This section explains the computation of AWS Signature Version 4 components for a hypothetical request:

KDate Calculation:

Uses HMAC-SHA256 with the secret access key and the date in YYYYMMDD format.
KRegion Calculation:

Computes using HMAC-SHA256 with kDate and the region name (e.g., us-east-1).
KService Calculation:

Calculates using HMAC-SHA256 with kRegion and the targeted AWS service name (e.g., iam).
KSigning Calculation:

Determines using HMAC-SHA256 with kService and the string "aws4_request".
Signature Calculation:

Generates the signature using HMAC-SHA256 with kSigning and a string combining various request elements like HTTP method, canonical URI, timestamp, etc.
AWS Key Management Service (KMS)
CMK Calculation:
Although not directly related to KMS, it demonstrates calculating a hypothetical Customer Master Key (CMK) using SHA3-256 with a student ID and full name. CMKs should be kept secret.
DK (Data Key) Generation:
KMS generates data keys using algorithms like SHA3-256, which are used for data encryption.
Encryption Process:
Uses the data key (DK) with AES-256 to encrypt sensitive information (e.g., name, address, mobile number).
Data Storage in AWS KMS:
After encryption, KMS securely stores the encrypted data and the encrypted copy of the data key.
Importance of Deleting Plaintext Data Key:
Emphasizes deleting the plaintext data key from memory post-use to prevent unauthorized access.
Decrypting the Encrypted Data:
KMS decrypts the encrypted data key (DK) using the CMK, and the decrypted DK decrypts the actual data.
AWS Site-to-Site VPN based on Diffie-Hellman Key Establishment
This section outlines the Diffie-Hellman key exchange protocol calculations without implementing the actual VPN connection establishment.
