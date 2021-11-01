[Home](README.md)

<br>

# Cryptography

<br>

## Readings from [Encryption, decryption, and cracking](https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:online-data-security/xcae6f4a7ff015e7d:data-encryption-techniques/a/encryption-decryption-and-code-cracking)

<br>

### Encrypting a message

<br>

> Imagine Caesar wants to send this message:

> `SECRET MEETING AT THE PALACE`.

> Here's what that might look like encrypted:

> `YKIXKZ SKKZOTM GZ ZNK VGRGIK`.

> The Caesar Cipher is a simple substitution cipher which replaces each original letter with a different letter in the alphabet by shifting the alphabet by a certain amount.

> To make the encrypted message above, shift the alphabet by 6.

<br>

### Decrypting a message

<br>

> According to historical records, Caesar always used a shift of 3.

> As long as his message recipient knew the shift amount, it was trivial for them to decode the message.

<br>

### Cracking the cipher

<br>

> There are three main techniques he could use: `frequency analysis`, `known plaintext`, and `brute force`.

<br>

- Frequency analysis
 
> Human languages tend to use some letters more than others.
 
> For example, "E" is the most popular letter in the English language.
 
> We can analyze the frequency of the characters in the message and identify the most likely "E" and narrow down the possible shift amounts based on that.

<br>

- Known plaintext

> Another term for the original unencrypted message is plaintext. If the enemy already knew some part of the plaintext, it will be easier for them to crack the rest of the encrypted version.

> For example, messages tend to start with similar beginnings. In WWII, encrypted German messages always started with a weather forecast, which ultimately made them easier for British mathematician Alan Turing to crack.

<br>

- Brute force

> There are only 25 possible shifts (not 26 — why not?).

> The enemy could take some time to try out each of them and find one that yielded a sensible message.

> They wouldn't even need to try the shifts on the entire message, just the first word or two.

<br>

### Encryption, decryption, and cracking

<br>

> `Encryption`: scrambling the data according to a secret key (in this case, the alphabet shift).

> `Decryption`: recovering the original data from scrambled data by using the secret key.

> `Code cracking`: uncovering the original data without knowing the secret, by using a variety of clever techniques.

<br>

## Readings from [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher)

<br>

### Encrypting a message

<br>

> In cryptography, a Caesar cipher, also known as Caesar's cipher, the shift cipher, Caesar's code or Caesar shift, is one of the simplest and most widely known encryption techniques.

> It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.

> For example, with a left shift of 3, D would be replaced by A, E would become B, and so on. The method is named after Julius Caesar, who used it in his private correspondence.

<br>

> The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the scheme, `A → 0, B → 1, ..., Z → 25`.

> Encryption of a letter x by a shift n can be described mathematically as: `En(x)=(x+n) mod {26}`.

> Decryption is performed similarly, `Dn(x)=(x-n) mod 26`.

<br>

### Breaking the cipher

<br>

- The Caesar cipher can be easily broken even in a ciphertext-only scenario:
  - An attacker knows (or guesses) that some sort of simple substitution cipher has been used, but not specifically that it is a Caesar scheme.
    - the cipher can be broken using the same techniques as for a general simple substitution cipher, such as frequency analysis or pattern words.
    - While solving, it is likely that an attacker will quickly notice the regularity in the solution and deduce that a Caesar cipher is the specific algorithm employed.
  - An attacker knows that a Caesar cipher is in use, but does not know the shift value.
    - Since there are only a limited number of possible shifts (25 in English), they can each be tested in turn in a brute force attack.
    - One way to do this is to write out a snippet of the ciphertext in a table of all possible shifts - a technique sometimes known as "completing the plain component".
  - Another brute force approach is to match up the frequency distribution of the letters. By graphing the frequencies of letters in the ciphertext, and by knowing the expected distribution of those letters in the original language of the plaintext, a human can easily spot the value of the shift by looking at the displacement of particular features of the graph.
    - This is known as frequency analysis. For example, in the English language the plaintext frequencies of the letters E, T, (usually most frequent), and Q, Z (typically least frequent) are particularly distinctive.
