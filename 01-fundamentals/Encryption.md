# Enc concepts
Plaintext - unencrytped data - images/apps/documents
algorithams - AES, RC4, DES, RC5/RC6
Key - eg. Password
Ciphertext - encrytped data

## Keys
Symmetric Key - local file encryption really good. Not so good when data transferred between parties, as no way to safely use same key.

Asymmetric key - Public (only usedd to encrypt) and private key (only used to decrypt). So all good to share Public, must guard private key. Generally used by multiple parties, used by SSL, TLS, SSH. 

Key signing - used for ID verification. Can use public key to verify encryption done by Private key ( so return traffic can be verified this way).

Steganography - Another layer of protection; embed the data within something. Eg. hidden data within an image.

Private Key - Decrypt and also sign/verification
Public Key - encrypt 

## Hashing
    - examples - MD5 < SHA2-256
    - DATA + has func = HASH
    - Same Data = Same hash
    - Cannot get original data from a hash
    - dif data = diff hash

## Digitial Signatures
- Verify integrity ( what) and Authenticity ( who)
