# CheatSheet

| **Symmetric** [Performance]                                  | **CipherType** | **Asymmetric** (Public Key) [Key Exchange]                   |
| ------------------------------------------------------------ | -------------- | ------------------------------------------------------------ |
| Vernam (One Time Pad) Used in WWII in the German Enigma      | XOR            | RSA (Rivest, Shamir & Aldeman) - Uses large prime numbers. Encrypt/decrypt digital signatures. |
| AES (Advanced Encryption Standard) [Rijndael] (128, 192, 256 bits) Used by WPA2. | Block          | DSA (Digital Signature Algorithm) - Modifies Diffie-Hellman for use in digital signatures. Combines with elliptic curves to create ECDSA. |
| DES (Data Encryption Standard) [Lucifer] (56 bits) Easily brute forced. | Block          | Diffie-Hellman Key Exchange (DH) - A standard for exchanging keys. Primarily used to send private keys over public networks. ECDHE (Elliptic Curve DH) Used for perfect forward secrecy. |
| 3DES (2 keys - 112 bits & 3 keys - 168 bits) Not used today. | Block          | ECC (Elliptic Curve Cryptography) - Needs large integers composed of two or more large prime factors. Great for low powered machines bc uses less CPU. Uses curves instead of prime numbers. |
| RC4 (Rivest Cipher 4) (40-2048 bits) Used by WEP and WPA.[deprecated] | Stream         | PGP (Pretty Good Privacy) - Used for emails and is used by IDEA algorithm; GPG(GNU Privacy Guard): A free version of PGP with sames specs. |
| Blowfish (1-448 bits) Fast, not patented limited.            | Block          |                                                              |
| Twofish (256 bits)                                           | Block          | **Hashing Algorithms - Integrity**                           |
| E0. Used by BlueTooth                                        | Stream         | MD5 (Message-Digest Algorithm v5) - 128 bit digest. Collision was found so it is not used as much. |
|                                                              |                | SHA (Secure Hash Algorithm) - 160 bit digest. Standard today. Wnet from SHA-1(160 bit) to SHA-2(512 bit). by NSA. |
| **Block cipher modes**                                       |                | HMAC (Hash-Based Message Authentication Code) - Combines itself with a symmetric key. Used in network encryption protocols. |
| CBC (Cipher Block Chaining) - Symmetric, uses IV. Slow       |                | RIPEMD (RACE Integrity Primitives Evaluation Message Digest) - Based on MD4. Collisions were found. |
| GCM (Galois Counter Mode) - Encryption with auth. Very efficient. Provides data authenticity/intregrity. Widely used. |                |                                                              |
| ECB (Electronic Code Book) - Simplest mode, each block with same key. Not recommended. |                | SSL (Secure Sockets Layer) protocol -  Has two parts. The SSL Handshake Protocol establishes the secure channel. And the SSL Application Data Protocol is used to exchange data over the channel. 6 Steps in the handshaking process. |
| CTR (Counter Mode) - Converts block into stream, uses IV. Widely used. |                | ISAKMP (Internet Security Association and Key Management Protocol) - Used to negotiate and provide authenticated keying material for security associations in a protected manner |
|                                                              |                | X.509 - A standard defining the format of public key certificates. Used in many Internet protocols, (TLS/SSL) and offline applications, like electronic signatures. Contains a public key and an identity, and is either signed by a CA or self-signed. |
| **Wireless** [Crypto protocols]                              |                | Perfect Forward Secrecy (PFS) - Prevents point of failure where a stolen private key can decrypt all connections by generating a new key each session. Protects past sessions against future compromises of secret keys. |
| WPA (Wi-Fi Protected Access) - Uses RC4 with TKIP. Replaced by WPA2. |                |                                                              |
| WPA2 (WPA v2) - Uses CCMP for encryption and AES.            |                |                                                              |
| CCMP (Counter Mode with Cipher Block Chaining Message Authentication Code Protocol) - Is based on 128-bit AES. |                |                                                              |
| TKIP (Temporal Key Integrity Protocol) - Mixes a root key with an IV, a new key for each packet. Prevents replay attacks and protects against tampering. |                |                                                              |
| WEP (Wired Equivalent Privacy)                               |                |                                                              |
|                                                              |                | **Goals of Cryptography**                                    |
| **Wireless** [Auth  protocols]                               |                | Confidentiality - Asymmetric (Public Key) & Symmetric Encryption |
| EAP (Extensible Authentication Protocol): Authentication framework that provides general guidance for authentication methods. |                | Authenticity/Authentication/Accountability - Asymmetric Encryption (Private Key), MAC/MIC, & Digital Signature |
| PEAP (Protected EAP): An extension of EAP that is sometimes used with 802.1x, a certificate is required on the 802.1x server. |                | Integrity - Hashing, Checksum, Parity and Check Digit        |
| EAP-FAST (EAP Flexible Authentication with Secure  Tunneling): A Cisco-designed replacement for Lightweight EAP, supports certificates. |                | Non-Repudiation - Digital Signature (Only)                   |
| EAP-TLS (EAP Transport Layer Security): One of  the most secure EAP standards and is widely implemented on many networks. It uses PKI, so certificates are required on the 802.1x server and on the clients. |                |                                                              |
| EAP-TTLS (EAP Tunneled TLS): Allows for systems to use older authentication methods such as PAP within a TLS tunnel. Certificate is required on the 802.1x server but not on the clients. |                | Diffusion - Changing one character causes the plaintext to drastically change the outputed cipher. |
| IEEE 802.1x: An authentication protocol used in VPNs,  wired and wireless networks. In VPNs it is used as a RADIUS server, wired use it as a port-based authentication, and wireless use it in Enterprise mode. Can be used with certificate-based authentication. |                | Obfuscation: Taking something and making it difficult to understand, however it is not impossible to convert it  back to the original form. |
| RADIUS Federation: Members of one organization can  authenticate to the network of another network using their normal credentials. Uses 802.1X as authentication method. |                | Confusion - The cipher doesn't look anything like the plain text. |
|                                                              |                |                                                              |
|                                                              |                | **Public key infrastructure**                                |
| **Stapling**: Combining related items in order to reduce  communication steps. The device that holds the certificate will also be  the one to provide status of any revocation. |                | CA (Certificate Authority): A trusted third-party agency that is responsible for issuing digital certificates. |
| **Pinning**: The application has hard-coded the server’s certificate into the application itself. |                | Intermediate CA (Intermediate Certificate Authority):  An entity that processes the CSR and verifies the authenticity of the  user on behalf of a CA. |
|                                                              |                | CRL (Certificate Revocation List): A list of  certificates that are no longer valid, expired, or that have been revoked by the issuer. |
| **Cert formats**                                             |                | CSR (Certificate Signing Request): A user request for a digital certificate. |
| **DER** (Distinguished Encoding Rules): Are common and  designed for X.509 certificates, they are used to extend binary encoded  certificates. Cannot be edited by a plain text editor. Used with Java  commonly. |                | OCSP (Online Certificate Status Protocol): A request  and response protocol that obtains the serial number of the certificate  that is being validated and reviews revocation lists for the client. |
| **PEM** (Privacy Enhanced Mail): Most common format in  which certificates are issued. Multiple certificates and the private key can be included in one file. The file is encoded ASCII. PEM file  extensions include .pem, .crt, .cer, and .key. Apache servers typically  use PEM-format files. |                | Certificate: Digitally signed statement that associates a public key to the corresponding private key. |
| **PFX**: A precursor to P12, has the same usage. Administrators often use this to format on Windows to import and export certificates. |                | Object identifiers (OID): A serial number that authenticates a certificate. |
| **CER** (Certificate File): May be encoded as binary DER or as ASCII PEM. |                |                                                              |
| **P12**: Is a PFX extension used in windows.                 |                |                                                              |
| **PKCS #12** (Public Key Cryptography Standards #12): Is  part of the RFC standard. Stores many types of certificates and can be  password protected. |                |                                                              |
| **RFC** (Remote Function Call): A formal document describes the specifications for a particular technology, was drafted by the  Internet Engineering Task Force. |                |                                                              |
| **P7B**: Is stored in Base64 ASCII, containing certificates and chains but not the private key. |                |                                                              |

| **Port** | **Use**   |
| -------- | --------- |
| 21       | FTP       |
| 22       | SSH       |
| 23       | Telnet    |
| 25       | SMTP      |
| 49       | TACACS    |
| 53       | DNS       |
| 67-68    | DHCP      |
| 80       | HTTP      |
| 110      | POP3      |
| 143      | IMAP4     |
| 161      | SNMP      |
| 389-636  | LDAP      |
| 443      | HTTPS/SSL |
| UDP 1701 | L2TP      |
| TCP 1723 | PPTP      |
