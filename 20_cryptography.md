# Cryptography

## Useful tool

- Hash Identifier <https://www.onlinehashcrack.com/hash-identification.php>
- Hash-identifier (CLI)
- Hash Crack  
    <https://crackstation.net/>  
    <https://hashes.com/en/decrypt/hash>
- Hashcat  
    `Hashcat -a 3 -m 900 hash.txt /rockyou.txt`  
    -m hashtype  
    900 md4  
    1000 NTLM  
    1800 SHA512CRYPT  
    110 SHA1 with SALT HASH  
    0  MD5  
    100 SHA1  
    1400 SHA256  
    3200 BCRYPT  
    160 HMAC-SHA1  
- John  
  1. First analyze hash type - `john hashfile.hash`
  2. Then crack hash - `john hashfile.hash --wordlist=/usr/share/wordlists/rockyou.txt --format=Raw-SHA1`
  3. Show the cracked password - `john --show --format=Raw-SHA1 hashfile.hash` OR `john --show hashfile.hash

## Encrypt the information using various cryptography tools

- Calculate one-way hashes using **HashCalc**  
    windows application

- Calculate MD5 hashes using **MD5 Calculator**  
    windows application

- Calculate MD5 hashes using **HashMyFiles**  
    windows software (nirsoft)

- Perform file and text message encryption using **CryptoForge**  
    windows software

- Perform file encryption using **Advanced Encryption Package**  
    windows software

- Encrypt and decrypt data using **BCTextEncoder**  
    windows software

## Create a self-signed certificate

- Create and use self-signed certificates  
    from iis console

## Perform email encryption

- Perform email encryption using RMail  
    <https://www.rmail.com/free-trial/>  
    require sign up

## Perform disk encryption

- Perform disk encryption using **VeraCrypt**  
    windows software
  1. Create Volume
  2. Create an encrypted file container
  3. Standard VeraCrypt volume
  4. AES/SHA-512

- Perform disk encryption using **BitLocker** Drive Encryption

- Perform disk encryption using **Rohos Disk Encryption**
    windows software

## Perform cryptanalysis using various cryptanalysis tools

- Perform cryptanalysis using **CrypTool**
    windows software

- Perform cryptanalysis using **AlphaPeeler**
    windows software
