# Cryptography — Revision Notes

## 1. Basic Concept

**Cryptography** is the process of converting readable information into an unreadable form to protect it from unauthorized access.

### Basic Process

```text
Plaintext
   ↓
Encryption Algorithm + Key
   ↓
Ciphertext
   ↓
Decryption Algorithm + Key
   ↓
Plaintext
```

- **Plaintext:** Original readable message.
- **Ciphertext:** Encrypted, unreadable message.
- **Encryption:** Plaintext → Ciphertext.
- **Decryption:** Ciphertext → Plaintext.
- **Key:** Secret value used by the encryption/decryption process.

### Important Point

- The **encryption algorithm can be publicly known**.
- The **key must be kept secret**.
- If an attacker obtains the key, they may be able to decrypt the communication.

---

## 2. Definition of Cryptography

> **Cryptography is the art and science of transforming intelligible information (plaintext) into an unintelligible form (ciphertext) so that unauthorized parties cannot understand it easily.**

### Main Goal

Protect information during communication from unauthorized access.

---

# 3. Types of Cryptography

## A. Symmetric Cryptography

Also called **Private-Key Cryptography**.

- Uses **the same key** for encryption and decryption.
- Both sender and receiver must know the secret key.
- The key must be shared **securely**.

```text
Sender
Plaintext
   ↓
Encryption + Secret Key
   ↓
Ciphertext
   ↓
Decryption + Same Secret Key
   ↓
Receiver
Plaintext
```

### Key Point

**Same key → Encryption + Decryption**

---

## B. Asymmetric Cryptography

Also called **Public-Key Cryptography**.

- Uses **two different keys**:
  - **Public Key** → Can be shared publicly.
  - **Private Key** → Must be kept secret.

- The keys are mathematically related.
- Provides a solution to the key-sharing problem found in symmetric cryptography.

```text
Plaintext
   ↓
Encryption + Public Key
   ↓
Ciphertext
   ↓
Decryption + Private Key
   ↓
Plaintext
```

### Key Point

**Two keys → Public Key + Private Key**

---

## 4. Symmetric vs Asymmetric

| Feature        | Symmetric             | Asymmetric                     |
| -------------- | --------------------- | ------------------------------ |
| Number of keys | 1                     | 2                              |
| Encryption key | Secret key            | Public key                     |
| Decryption key | Same secret key       | Private key                    |
| Key sharing    | Must be done securely | Public key can be shared       |
| Main issue     | Key distribution      | More computationally expensive |

---

# 5. Security Schemes

## A. Unconditionally Secure

An encryption scheme is **unconditionally secure** if:

> The ciphertext contains **no information that can help an attacker determine the plaintext**, regardless of the attacker's computational power or available data.

### Key Point

Even with **unlimited computing power**, the attacker cannot break the encryption.

---

## B. Computationally Secure

An encryption scheme is **computationally secure** if:

> The time and computational resources required to break the encryption are greater than the value or useful lifetime of the encrypted information.

### Key Point

```text
Cost/Time to Break Encryption
              >
Value/Useful Lifetime of Information
```

Therefore, breaking the encryption is **practically infeasible**.

---

# Quick Revision

### Cryptography

**Plaintext → Encryption + Key → Ciphertext**

### Symmetric

**Same key** for encryption and decryption.

### Asymmetric

**Public key + Private key**.

### Unconditionally Secure

Cannot be broken **even with unlimited computational power**.

### Computationally Secure

Can theoretically be broken, but breaking it is **practically infeasible** because it requires excessive time/resources.

# Cryptography — Fundamental Concepts

## 1. The Basics of Cryptography

Cryptography is the science of converting **plaintext** (readable information) into **ciphertext** (scrambled, secure data) using an **encryption algorithm**.

The reverse process, turning ciphertext back into readable information, is called **decryption**.

---

## 2. Symmetric vs. Asymmetric Cryptography

### Symmetric Cryptography

- Uses the **same key** for both encryption and decryption.
- Since the same key performs both tasks, it must be kept **strictly private** between the sender and receiver.
- Also called **Private Key Cryptography**.

### Asymmetric Cryptography

- Uses a **pair of keys**:
  - **Public Key:** Can be shared with anyone.
  - **Private Key:** Must be kept secret.

- If a sender uses the **receiver's public key** to encrypt a message, only the receiver's corresponding **private key** can decrypt it.

---

## 3. Essential Cryptographic Terminology

### Plaintext

The **original message**.

### Ciphertext

The **encrypted, unintelligible output**.

### Cipher (Encryption Algorithm)

The **mathematical method** used to scramble the data.

- The algorithm itself can be **public**.
- The **key must remain secure**.

### Key

The most critical component of cryptography.

- If an attacker obtains the key, the **entire security of the message is compromised**.

### Cryptanalysis

The study of methods to **break or decode ciphertext without having the key**.

- Often called **code-breaking**.

### Cryptology

The overarching field that includes both:

- **Cryptography:** Creating secure codes.
- **Cryptanalysis:** Breaking or analyzing codes.

# Cryptanalysis — Revision Notes

## General Approaches to Breaking Encryption Systems

### 1. Brute Force Attack

- The attacker systematically tries **every possible key** in the **key space**.
- The attack succeeds when the correct secret key is found.
- Success depends heavily on the **size of the key space**.

### 2. Cryptanalytic Attack

- The attacker analyzes the **encryption algorithm** and the relationship between **plaintext and ciphertext**.
- Uses **logic and mathematical analysis** rather than simple trial-and-error.
- The goal is to discover the **secret key**.

---

# Types of Cryptanalytic Attacks

The attacks are classified based on the **information available to the attacker**.

### 1. Ciphertext-Only Attack

- Attacker has access **only to the ciphertext**.
- Does not have the original plaintext or secret key.
- Generally the **most difficult** type of attack.

### 2. Known-Plaintext Attack

- Attacker possesses:
  - **Plaintext**
  - Corresponding **Ciphertext**

- The attacker uses this information to find clues about the **secret key**.

### 3. Chosen-Plaintext Attack

- Attacker can **choose specific plaintexts**.
- The system encrypts these plaintexts.
- Attacker analyzes the resulting **ciphertexts** to deduce the key.

### 4. Chosen-Ciphertext Attack

- Attacker can **choose specific ciphertexts**.
- The system decrypts them.
- Attacker analyzes the resulting **plaintexts** to obtain information about the key or encryption system.

### 5. Chosen-Text Attack

- A broader classification.
- The attacker can influence **both plaintext and ciphertext inputs/outputs** to facilitate cryptanalysis.

---

## Important Assumption

In all these attacks, the attacker is assumed to **know the underlying encryption algorithm**.

### Key Idea

> **The algorithm can be known publicly; the security should depend on keeping the key secret.**

# Brute Force Attack — Revision Notes

## 1. Approaches to Attacking Cryptosystems

There are two primary approaches:

1. **Cryptanalytic Attack**
2. **Brute Force Attack**

---

## 2. Brute Force Attack

A **brute force attack** is an attack in which the attacker systematically tries **all possible keys** until the correct key is found.

### Core Concept

The attacker generally knows:

- The **encryption/decryption algorithm**
- The **ciphertext**

But does **not** know:

- The **secret key**

Since the attacker knows the decryption algorithm, they can try different keys to decrypt the ciphertext.

```text
Ciphertext
     ↓
Decryption Algorithm
     ↓
Try Key 1 → Candidate Plaintext
Try Key 2 → Candidate Plaintext
Try Key 3 → Candidate Plaintext
     ↓
    ...
     ↓
Try Key N → Candidate Plaintext
```

The attacker checks each resulting plaintext until the **correct/meaningful plaintext** is obtained.

### Example

Suppose a system uses a key from:

```text
0000 → 9999
```

The attacker can try:

```text
0000 → decrypt
0001 → decrypt
0002 → decrypt
...
5837 → decrypt → meaningful plaintext
```

If `5837` produces the correct plaintext, the attacker has found the key.

---

## 3. Key Space

**Key space** = The total number of possible keys that an attacker may have to try.

A larger key space makes brute force attacks more difficult.

For example:

```text
4-bit key → 2⁴ = 16 possible keys
8-bit key → 2⁸ = 256 possible keys
128-bit key → 2¹²⁸ possible keys
```

Therefore, increasing the key size greatly increases the number of possibilities.

---

## 4. Important Point

The security of a brute-force attack depends heavily on:

- **Key length**
- **Number of possible keys**
- **Speed of trying keys**

### Key Idea

> **Brute force = Try possible keys one by one until the correct key is found.**

---

## 5. Brute Force vs Cryptanalytic Attack

| Brute Force                                       | Cryptanalytic Attack                                             |
| ------------------------------------------------- | ---------------------------------------------------------------- |
| Tries possible keys systematically                | Analyzes weaknesses/patterns                                     |
| Does not necessarily exploit algorithm weaknesses | Uses mathematical/logical analysis                               |
| Can work even if algorithm is strong              | Attempts to exploit properties of the cryptosystem               |
| Difficulty mainly depends on key space            | Difficulty depends on the cryptosystem and available information |

---

## 6. Prevention

### CAPTCHA

**CAPTCHA** stands for:

**Completely Automated Public Turing test to tell Computers and Humans Apart**

CAPTCHAs help prevent automated brute-force attempts against login systems.

They require the user to perform tasks such as:

- Identifying objects in images
- Solving simple visual puzzles
- Entering displayed characters
- Performing simple logic-based tasks

This makes automated mass login attempts more difficult.

---

## Quick Revision

```text
Attacker knows:
    ↓
Algorithm + Ciphertext

Attacker does:
    ↓
Try Key 1
Try Key 2
Try Key 3
   ...
Try Key N

    ↓
Find correct key
    ↓
Decrypt ciphertext
    ↓
Obtain plaintext
```

**Brute Force Attack = Exhaustively trying possible keys until the correct key is found.**

# Classical Encryption Techniques

## Key Concepts

### Need for Encryption

- Classical encryption techniques are **no longer secure for modern internet communications**.
- They are important for understanding the **evolution of cryptographic security**.

### Substitution Techniques

- Involves **replacing plaintext letters or symbols with different ones**.
- Characters are mapped to specific substitutes using a **key**.

### Transposition Techniques

- Involves **rearranging the position of existing characters** in the plaintext.
- The characters themselves remain the same, but their **order changes**.

## Comparison

| Substitution                           | Transposition                          |
| -------------------------------------- | -------------------------------------- |
| Changes the **identity** of characters | Changes the **location** of characters |
| Uses new letters or symbols            | Does not add new characters            |

## Algorithms

### Substitution Algorithms

- Caesar Cipher
- Monoalphabetic Cipher
- Playfair Cipher
- Hill Cipher
- Polyalphabetic Cipher
- One-Time Pad

### Transposition Algorithms

- Rail-fence Transposition
- Row-Column Transposition

# Monoalphabetic Cipher

## 1. Classical Cryptosystems

Two fundamental types of classical substitution techniques:

- **Caesar Cipher**
- **Monoalphabetic Cipher**

---

## 2. Caesar Cipher

- Uses a **uniform shift** for all letters.
- Example: Shift by 3

```text
Plaintext:   A B C D E
Ciphertext:  D E F G H
```

- The difference between plaintext and ciphertext remains **uniform throughout the message**.
- Has a small number of possible keys.
- Therefore, it is vulnerable to **brute-force attacks**.

---

## 3. Monoalphabetic Cipher

A **monoalphabetic cipher** uses a **random permutation/mapping** of the alphabet.

### Permutation

If there are `n` elements:

$$
\text{Number of permutations} = n!
$$

For 3 elements:

```text
ABC
ACB
BAC
BCA
CAB
CBA
```

So:

$$
3! = 6
$$

For the English alphabet:

$$
26!
$$

possible keys.

This is a very large key space, making simple brute-force attacks theoretically impractical.

---

## 4. Monoalphabetic Cipher Mechanism

Unlike the Caesar cipher, which uses a uniform shift, a monoalphabetic cipher uses a **random mapping**.

Each plaintext letter is replaced by a corresponding ciphertext letter.

### Example

Suppose the mapping is:

| Plaintext  | A   | B   | C   | D   | E   | F   |
| ---------- | --- | --- | --- | --- | --- | --- |
| Ciphertext | X   | M   | Q   | R   | T   | P   |

Then:

```text
Plaintext:   A B C D E F
Ciphertext:  X M Q R T P
```

For example:

```text
Plaintext:   BAD
Ciphertext:  MXR
```

### Important Point

The substitution is **fixed throughout the message**.

If:

```text
A → X
```

then every occurrence of `A` will be replaced by `X`.

---

# 5. Why Is Monoalphabetic Cipher Weak?

Even though it has a huge key space, it is vulnerable to **frequency analysis**.

### Frequency Analysis

The **relative frequency of letters remains unchanged** because the substitution is static.

Common English letters include:

```text
E, T, A, O, I, N, S, R, H, D
```

### Example

Suppose a ciphertext contains:

```text
X X X X X X X
```

and `X` is the most frequently occurring symbol.

An attacker may guess:

```text
X → E
```

because `E` is one of the most frequently occurring letters in English.

The attacker can also observe patterns such as common two-letter words:

```text
IS
TO
IN
IT
```

Using letter frequencies and word patterns, the attacker can gradually recover the substitution.

---

# 6. How Does Frequency Analysis Break Ciphers?

```text
Ciphertext
    ↓
Count frequency of symbols
    ↓
Find most frequent symbols
    ↓
Compare with common English letters
    ↓
Analyze word/letter patterns
    ↓
Guess substitutions
    ↓
Recover plaintext
```

The key reason is:

> **The same plaintext letter is always replaced by the same ciphertext letter.**

Therefore, the statistical patterns of the language remain visible.

---

# 7. Monoalphabetic vs Polyalphabetic

| Monoalphabetic                                                  | Polyalphabetic                                                |
| --------------------------------------------------------------- | ------------------------------------------------------------- |
| Uses a **single substitution alphabet**                         | Uses **multiple substitution alphabets**                      |
| Same plaintext letter always maps to the same ciphertext letter | Same plaintext letter can map to different ciphertext letters |
| Vulnerable to frequency analysis                                | Provides better resistance to frequency analysis              |

---

# 8. How to Improve Security?

### Homophonic Substitution

Multiple ciphertext symbols can represent the same plaintext letter.

Example:

```text
E → 1, 5, or 9
```

This helps **flatten the frequency distribution**.

### Polyalphabetic Cipher

Uses multiple substitution alphabets so that the **same plaintext letter does not always map to the same ciphertext character**.

---

# 9. Pros and Cons

### Advantages

- Much larger key space than the **Caesar cipher**.
- Simple brute-force attack becomes impractical.

### Disadvantage

- Vulnerable to **frequency analysis** because the substitution is static.

---

## Quick Revision

```text
Caesar Cipher
→ Uniform shift
→ Small key space
→ Brute-force vulnerable

Monoalphabetic Cipher
→ Random fixed mapping
→ 26! possible keys
→ Brute-force difficult
→ Frequency analysis vulnerable

Polyalphabetic Cipher
→ Multiple substitution alphabets
→ Same letter can have different ciphertext symbols
→ Better resistance to frequency analysis
```

# Playfair Cipher

- Aka **Playfair Square** or **Wheatstone-Playfair Cipher**.
- **Manual symmetric encryption technique.**
- The first **literal digram substitution cipher**.
- Invented in **1854 by Charles Wheatstone**.
- Bore the name of **Lord Playfair** for promoting its use.
- **Multiple letter encryption cipher.**
- Works with **digrams**.

## 1. 5 × 5 Matrix Construction

A **5 × 5 matrix** is constructed using a **keyword**.

Example keyword: **MONARCHY**

The matrix is:

M O N A R

---

C H Y B D
E F G I/J K
L P Q S T
U V W X Z

- The keyword is used to construct the matrix.
- **I and J are combined** into one cell.

## 2. Rules for Encryption Using Playfair Cipher

1.  **Digrams**
2.  **Repeating Letters → Filler Letter**
3.  **Same Column → ↓ → Wrap around**
4.  **Same Row → → → Wrap around**
5.  **Rectangle → Swap**

## 3. Examples of Digrams

### Example 1

```text
Plaintext: attack
Digrams:   at ta ck
```

### Example 2

```text
Plaintext: neso academy
Digrams:   ne so ac ad em yx
```

### Example 3

```text
Plaintext: balloon
Digrams:   ba ll oo n
```

For repeating letters, a **filler letter** is used:

```text
Digrams: ba lx lo on
```

## 4. Encryption Rules

### Same Column

- If both letters are in the **same column**, move each letter
  **down**.
- If a letter reaches the bottom, **wrap around** to the top.

### Same Row

- If both letters are in the **same row**, move each letter **right**.
- If a letter reaches the end, **wrap around** to the beginning.

### Rectangle

- If the two letters form a **rectangle**, keep the same rows and
  **swap the columns**.

# Hill Cipher

The **Hill Cipher** is a polygraphic substitution cipher developed by **Lester Hill in 1929**.

Unlike simpler methods, it encrypts **groups of letters simultaneously using linear algebra**, providing improved security.

---

## 1. Core Concepts & Mathematics

To work with the Hill Cipher, basic knowledge of **linear algebra** is required.

- **Matrix Arithmetic Modulo 26:** All calculations are performed relative to the 26 letters of the alphabet.
- **Square Matrices:** The key must be a square matrix, such as **2 × 2** or **3 × 3**.
- **Mathematical Prerequisites:** Understanding **determinants** and finding **multiplicative inverses** is essential for decryption.

---

## 2. Hill Cipher Formulas

Encryption and decryption rely on **matrix multiplication**.

### Encryption

The ciphertext is generated by multiplying the plaintext vector by the key matrix, modulo 26:

\[
C = P \times K \pmod{26}
\]

### Decryption

The plaintext is recovered by multiplying the ciphertext vector by the inverse of the key matrix, modulo 26:

\[
P = C \times K^{-1} \pmod{26}
\]

---

## 3. Encryption Process

1. **Convert Plaintext:** Convert English letters to numbers.

2. **Group Letters:** The size of the key matrix determines how many letters are encrypted at once.
   - A **3 × 3 matrix** encrypts letters in groups of 3.

3. **Multiply:** Perform matrix multiplication between the letter vector and the key matrix.

4. **Modulo 26:** Apply modulo 26 to the resulting numbers to bring them back into the **0–25 range**.

5. **Convert Back:** Translate the resulting numbers back into their corresponding alphabetical characters.

### Note

If the plaintext does not perfectly fit the matrix dimensions, add **filler characters** such as `X`.

# Hill Cipher Decryption

The **Hill Cipher decryption** process reverses the encryption process by applying the **inverse of the key matrix** to the ciphertext.

## 1. Core Mathematical Concepts

Decryption requires several linear algebra operations under **modulo 26 arithmetic**:

- **Determining the Determinant:** Used to verify the existence of the inverse.
- **Finding the Adjoint Matrix:** Required to compute the inverse.
- **Multiplicative Inverse:** Finding the modular inverse of the determinant, which is essential when the formula involves division.

# Hill Cipher Decryption

## 1. Core Mathematical Concepts

Decryption requires several linear algebra operations under **modulo 26 arithmetic**:

- **Determining the Determinant:** Used to verify the existence of the inverse.
- **Finding the Adjoint Matrix:** Required to compute the inverse.
- **Multiplicative Inverse:** Finding the modular inverse of the determinant, which is essential when the formula involves division.

## 2. Hill Cipher Decryption Formula

The decryption of the **plaintext (P)** from the **ciphertext (C)** using a **key matrix (K)** is:

$$
P = C \times K^{-1} \pmod{26}
$$

The **Key Inverse Matrix** is calculated as:

$$
K^{-1} = (\det K)^{-1} \times \mathrm{adj}(K) \pmod{26}
$$

## 3. Summary of the Process

1. **Find the Determinant:** Calculate the determinant of the original key matrix and find its multiplicative inverse modulo 26.

2. **Find the Adjoint:** Compute the adjoint of the key matrix.

3. **Compute the Key Inverse:** Multiply the modular inverse of the determinant by the adjoint matrix.

4. **Decrypt:** Multiply the ciphertext vector by the key inverse matrix modulo 26 to recover the plaintext.

2. **Find the Adjoint:** Compute the adjoint of the key matrix.

3. **Compute the Key Inverse:** Multiply the modular inverse of the determinant by the adjoint matrix.

4. **Decrypt:** Multiply the ciphertext vector by the key inverse matrix modulo 26 to recover the plaintext.

# Euler’s Totient Function (Phi Function)

This video from Neso Academy provides an introduction to Euler’s Totient Function, also known as the Phi Function, a core concept in Network Security and Cryptography.

## Definition and Concept

Euler’s Totient Function is defined as the number of positive integers less than or equal to `n` that are relatively prime (or co-prime) to `n`.

Two numbers are relatively prime if their Greatest Common Divisor (GCD) is 1.

## Method for Finding φ(n)

To calculate the function for smaller numbers, you follow these steps:

1. List integers from `1` up to `n`.
2. Compute the GCD for each integer with `n`.
3. Count how many of those integers have a GCD of 1 with `n`.

## Solved Examples

### Example 1: φ(5)

Numbers to check: `1, 2, 3, 4, 5`.

GCDs with 5: `1, 1, 1, 1, 5`.

Result: `φ(5) = 4` because there are four numbers relatively prime to 5.

### Example 2: φ(11)

Since 11 is a prime number, all numbers from 1 to 10 are relatively prime to it.

Result: `φ(11) = 10`.

### Example 3: φ(8)

Numbers to check: `1, 2, 3, 4, 5, 6, 7, 8`.

Numbers relatively prime to 8 are: `1, 3, 5, 7`.

Result: `φ(8) = 4`.

## Conclusion

While the manual counting method is effective for small numbers, this approach becomes impractical for larger numbers. Future sessions will cover formulas to compute the Phi Function for larger values efficiently.

# Revision Notes: Euler’s Totient Function

Euler's Totient Function, denoted as `φ(n)`, counts the number of positive integers up to `n` that are **relatively prime** to `n` (i.e., the greatest common divisor is `1`).

## 1. Fundamental Rules for Calculation

### If `n` is a Prime Number

The totient is simply `φ(n) = n - 1` because all numbers smaller than a prime are relatively prime to it.

**Example:** `φ(5) = 4`

### If `n` is a Product of Two Distinct Primes

If `n = p × q`, since all multiples of `p` and `q` share a factor, we exclude them using the formula:

`φ(n) = n(1 - 1/p)(1 - 1/q)`

**Example:** For `n = 15` (`3 × 5`),

`φ(15) = 15(1 - 1/3)(1 - 1/5) = 8`

### If `n` is a Product of Composite and Prime Numbers

You break `n` down into its prime factorization:

`n = p₁^a × p₂^b × ...`

The general formula is:

`φ(n) = n(1 - 1/p₁)(1 - 1/p₂)...`

**Example:** For `n = 12` (`2² × 3`),

`φ(12) = 12(1 - 1/2)(1 - 1/3) = 4`

## 2. Key Takeaways

- **Manual vs. Formula:** While manual counting works for small numbers, the formulaic approach is essential for large numbers in cryptography.
- **Relatively Prime:** Always verify if numbers are relatively prime; if they share a common divisor (like `4` and `6`, which share `2`), they are not relatively prime, meaning `GCD(4, 6) ≠ 1`.
- **Cryptography Context:** `φ(n)` is a foundational concept in network security and algorithms like RSA.


# Fermat's Little Theorem

This video from *Neso Academy* provides an explanation of **Fermat's Little Theorem**, a key concept used in *cryptography* and *network security*.

## What is Fermat's Little Theorem?

### The Statement

If `p` is a prime number and `a` is any positive integer not divisible by `p`, then:

`a^(p-1) ≡ 1 (mod p)`

### Purpose

It is a powerful tool for solving complex problems involving modular exponentiation in cryptographic applications.

## Solved Examples

### Example 1

Verifying the theorem for `p = 5` and `a = 2`.

Since `5` is prime and `2` is not divisible by `5`, the theorem holds:

`2^(5-1) ≡ 1 (mod 5)`

and

`2^4 ≡ 1 (mod 5)`.

### Example 2

Verifying for `p = 7` and `a = 3`.

The video demonstrates how to use modular exponentiation shortcuts to simplify:

`3^6 ≡ 1 (mod 7)`.

### Example 3 (Invalid Case)

Proving the theorem does **not** hold for `p = 4` and `a = 2`.

Because `4` is **not a prime number**, the condition is not met, and the congruence is invalid.

# Multiplicative Inverse

## 1. Multiplicative Inverse

The standard multiplicative inverse of a number \(a\) is:

$$
\frac{1}{a}
$$

such that:

$$
a \times \frac{1}{a} = 1
$$

---

## 2. Multiplicative Inverse Under Modular Arithmetic

In modular arithmetic, the multiplicative inverse of \(a\) modulo \(m\) is a number \(x\) such that:

$$
(a \times x) \mod m = 1
$$

The inverse depends on the modulus.

For example, the inverse of a number can be different for different moduli.

---

## 3. Finding Multiplicative Inverse Manually

### Example 1: Inverse of 3 mod 5

We need to find \(x\) such that:

$$
(3 \times x) \mod 5 = 1
$$

Try \(x = 2\):

$$
3 \times 2 = 6
$$

$$
6 \mod 5 = 1
$$

Therefore:

$$
\boxed{3^{-1} \equiv 2 \pmod{5}}
$$

### Example 2: Inverse of 2 mod 11

We need to find \(x\) such that:

$$
(2 \times x) \mod 11 = 1
$$

Try \(x = 6\):

$$
2 \times 6 = 12
$$

$$
12 \mod 11 = 1
$$

Therefore:

$$
\boxed{2^{-1} \equiv 6 \pmod{11}}
$$

---

## 4. Existence of Multiplicative Inverse

A multiplicative inverse of \(a\) modulo \(m\) exists **if and only if**:

$$
\gcd(a,m)=1
$$

That means \(a\) and \(m\) must be **relatively prime**.

### Example

For \(3\) and \(5\):

$$
\gcd(3,5)=1
$$

So, the inverse exists.

For \(5\) and \(10\):

$$
\gcd(5,10)=5
$$

Since:

$$
\gcd(5,10)\neq1
$$

the multiplicative inverse does **not** exist.

---

## 5. Finding Inverse for Large Numbers

For large numbers, finding the inverse by trial and error is inefficient.

The **Extended Euclidean Algorithm** is used to efficiently find the multiplicative inverse.

# Extended Euclidean Algorithm

## 1. Purpose

The **Extended Euclidean Algorithm** is used to find the **multiplicative inverse** of a number under a given modulus.

If we want to find the inverse of \(a\) modulo \(m\), we need to find \(x\) such that:

$$
a \times x \equiv 1 \pmod{m}
$$

---

## 2. Algorithm

The Extended Euclidean Algorithm is based on the Euclidean Algorithm.

It finds integers \(x\) and \(y\) such that:

$$
ax + my = \gcd(a,m)
$$

If:

$$
\gcd(a,m)=1
$$

then:

$$
ax + my = 1
$$

Taking modulo \(m\):

$$
ax \equiv 1 \pmod{m}
$$

Therefore, \(x\) is the **multiplicative inverse of \(a\) modulo \(m\)**.

---

## 3. Steps

1. Apply the **Euclidean Algorithm** to find \(\gcd(a,m)\).
2. Continue the divisions until the remainder becomes \(1\).
3. Use **back substitution** to express \(1\) as a combination of \(a\) and \(m\).
4. The coefficient of \(a\) gives the multiplicative inverse.
5. If the coefficient is negative, take its positive equivalent using modulo \(m\).
6. Verify the answer by checking:

$$
(a \times x)\mod m = 1
$$

---

## 4. Important Condition

The multiplicative inverse exists only when:

$$
\boxed{\gcd(a,m)=1}
$$

If:

$$
\gcd(a,m)\neq1
$$

then the multiplicative inverse does not exist.

---

## 5. Verification

After finding the inverse \(x\), verify it using:

$$
\boxed{(a\times x)\mod m=1}
$$

If the result is \(1\), the calculated inverse is correct.
# Chinese Remainder Theorem (CRT)

This video from *Neso Academy* provides a clear, step-by-step tutorial on the **Chinese Remainder Theorem (CRT)**, specifically focusing on how to solve a system of linear congruent equations with relatively prime moduli.

## Key Concepts Covered

### The CRT Statement

The theorem establishes that a system of congruent equations with one variable $x$ and pairwise relatively prime moduli

$$
m_1, m_2, \ldots, m_n
$$

has a unique solution.

### The General Formula

The formula used to find $x$ is:

$$
x = \sum_{i=1}^{n} a_i M_i M_i^{-1} \pmod{M}
$$

where:

$$
M = m_1m_2\cdots m_n
$$

and

$$
M_i = \frac{M}{m_i}
$$

---

# Solved Example

Solve the following system:

$$
x \equiv 2 \pmod{3}
$$

$$
x \equiv 3 \pmod{5}
$$

$$
x \equiv 2 \pmod{7}
$$

## 1. Find Moduli ($M$)

Calculate the product:

$$
M = 3 \times 5 \times 7
$$

$$
M = 105
$$

## 2. Calculate Partial Products ($M_i$)

$$
M_1 = 35
$$

$$
M_2 = 21
$$

$$
M_3 = 15
$$

## 3. Find Multiplicative Inverses

Solve for each inverse such that:

$$
M_i \cdot M_i^{-1} \equiv 1 \pmod{m_i}
$$

The values are:

$$
M_1^{-1} = 2
$$

$$
M_2^{-1} = 1
$$

$$
M_3^{-1} = 1
$$

## 4. Final Calculation

Using the formula:

$$
x = (a_1M_1M_1^{-1} + a_2M_2M_2^{-1} + a_3M_3M_3^{-1}) \pmod{M}
$$

Substitute the values:

$$
x = (2 \times 35 \times 2 + 3 \times 21 \times 1 + 2 \times 15 \times 1) \pmod{105}
$$

$$
x = 233 \pmod{105}
$$

$$
x = 23
$$

Therefore:

$$
\boxed{x = 23}
$$

## Verification

Plug $23$ back into the original equations to confirm that the remainders match the given values.
# Fermat's Factoring Method

This video explains **Fermat's Factoring Method**, a technique used in network security and cryptography to factor a number $n$ that is the product of two prime numbers, $x$ and $y$.

## Core Principle

Fermat's method works best when the two prime factors, $x$ and $y$, are close to each other.

It relies on the algebraic identity:

$$
n = x^2 - y^2
$$

Which can be rewritten to isolate the value of $x$:

$$
x = \sqrt{n + y^2}
$$

## Step-by-Step Procedure

1. **Setup:** Take the number $n$ you wish to factor.

2. **Iteration:** Test successive integer values for $y$ (starting from $1, 2, 3, \ldots$).

3. **Identify Integer:** Calculate

   $$
   \sqrt{n + y^2}
   $$

   Keep increasing $y$ until the result is a perfect integer.

4. **Solve:** Once you find an integer $x$ for a specific $y$, use the factored form of the difference of squares:

   $$
   n = (x+y)(x-y)
   $$

## Example Walkthrough

### Factoring 187

Trial:

$$
\sqrt{187 + 1^2} = \sqrt{188}
$$

No.

$$
\sqrt{187 + 2^2} = \sqrt{191}
$$

No.

$$
\sqrt{187 + 3^2} = \sqrt{196} = 14
$$

Yes.

Calculation:

$$
(14+3)(14-3)
$$

$$
= 17 \times 11
$$

The prime factors are **17 and 11**.

### Factoring 3233

Through iteration, the algorithm finds:

$$
x = 57
$$

and

$$
y = 4
$$

Calculation:

$$
(57+4)(57-4)
$$

$$
= 61 \times 53
$$

The prime factors are **61 and 53**.

## Summary

While Fermat's method is efficient for numbers with close prime factors, its performance decreases significantly as the distance between the factors increases.

The instructor concludes with a homework challenge:

$$
n = 3009
$$
