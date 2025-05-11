# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:
```
Name: K Hasini
Reg: 212224240074
```

```
from math import gcd

# Function to find modular inverse
def mod_inverse(e, phi):
    for d in range(1, phi):
        if (e * d) % phi == 1:
            return d
    return None

# Step 1: User Inputs
p = int(input("Enter a prime number (p): "))
q = int(input("Enter another prime number (q): "))

n = p * q
phi = (p - 1) * (q - 1)

print(f"\nCalculated n = {n} and φ(n) = {phi}")

# Step 2: Choose 'e' such that 1 < e < phi and gcd(e, phi) = 1
for i in range(2, phi):
    if gcd(i, phi) == 1:
        e = i
        break

print(f"Chosen public exponent (e): {e}")

# Step 3: Compute the modular inverse of e
d = mod_inverse(e, phi)
print(f"Calculated private key (d): {d}")

print(f"\nPublic Key: (n={n}, e={e})")
print(f"Private Key: (n={n}, d={d})")

# Step 4: User input for message
msg = int(input("\nEnter the message (as a number): "))

# Encryption
cipher = pow(msg, e, n)
print(f"\nEncrypted Message: {cipher}")

# Decryption
plain = pow(cipher, d, n)
print(f"Decrypted Message: {plain}")

```
## Output:
![image](https://github.com/user-attachments/assets/9939b7c4-8341-4a1a-a9ef-841ba9f485c3)


## Result:
 The program is executed successfully.
