Overview

The Breaking RSA room on TryHackMe focuses on the basic cryptographic concept of RSA encryption and how weak RSA key generation can be attacked. The challenge demonstrates how RSA’s security depends on the difficulty of factoring a large modulus into two primes. However, if the RSA key is generated poorly (e.g., using primes that are too close), the key can be factored and the private key can be derived.

Security Concept

RSA (Rivest–Shamir–Adleman) is one of the most widely used public-key cryptosystems. It involves a public key (e, n) and a private key (d).

The public key is used for encryption.

The private key is used for decryption.

RSA’s security relies on the fact that factoring the product of two large prime numbers (the modulus n) is computationally hard. If n can be factored into primes p and q, one can derive the private key d.

In this TryHackMe room, a deprecated library generates RSA keys with p and q that are too close, making the modulus factorable by using Fermat’s factorization method.

What Was Done

The typical approach to tackling this challenge includes:

Service enumeration on the deployed machine to identify open services and entry points.

Web enumeration to find hidden directories exposing the RSA public key.

Retrieving the public key for analysis.

Analyzing the RSA key:

Determine key length (in bits).

Extract the modulus (n) from the public key.

Factor the modulus into its prime components p and q.

Using p and q to compute the RSA private key and retrieve the flag.

Tools Used

Nmap (for port and service enumeration)

Gobuster or directory discovery tool (to find hidden content on the web server)

SSH key analysis (e.g., ssh-keygen to see key length)

Python with libraries such as pycryptodome or Fermat factorization scripts (for key breakdown)

Outcome

From this challenge, the following outcomes are typically achieved:

Enumeration revealed standard services (e.g., HTTP and SSH) running on the machine.

A hidden directory containing the RSA public key was identified on the web server.

The RSA key was found to be 4096 bits long.

The RSA modulus (n) was extracted and factored into its prime components using a suitable algorithm (e.g., Fermat’s).

With p and q known, the private key was derived from the public key.

Finally, the flag was obtained by using the private key to decrypt the encrypted content.

Key Takeaways

RSA security depends on large prime factorization.

Poor key generation (e.g., choosing p and q too close) can make RSA breakable.

Cryptographic weaknesses can be exploited with the right tools and mathematical understanding.

Basic enumeration (services + hidden directory) can lead to deeper cryptographic analysis.

Learning Outcome

This challenge strengthened my understanding of:

How asymmetric encryption works.

Why RSA key generation must use strong, well-separated primes.

How enumeration and cryptanalysis tools help uncover vulnerabilities in weak cryptographic implementations.
