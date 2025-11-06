# EX-NO-12-ELGAMAL-ALGORITHM
```
GEERTHIVASH J.D. - 212223060067
```
## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:

```
#include <stdio.h>
#include <math.h>
long long power_mod(long long base, long long exp, long long mod) {
long long result = 1;
base = base % mod;
while (exp > 0) {
if (exp % 2 == 1)
result = (result * base) % mod;
exp = exp / 2;
base = (base * base) % mod;
}
return result;
}
long long mod_inverse(long long a, long long m) {
long long x;
for (x = 1; x < m; x++) {
if ((a * x) % m == 1)
return x;
}
return -1;
}
int main() {
long long p, g, x, y, k, m;
long long c1, c2, s, s_inv, decrypted;
printf("Enter a prime number p: ");
scanf("%lld", &p);
printf("Enter a primitive root g: ");
scanf("%lld", &g);
printf("Enter private key x (less than p): ");
scanf("%lld", &x);
y = power_mod(g, x, p);
printf("\nPublic Key: (p=%lld, g=%lld, y=%lld)\n", p, g, y);
printf("Private Key: x=%lld\n", x);
printf("\nEnter message m (as number): ");
scanf("%lld", &m);
printf("Enter random key k: ");
scanf("%lld", &k);
c1 = power_mod(g, k, p);
c2 = (m * power_mod(y, k, p)) % p;
printf("\nCipher Text: (c1=%lld, c2=%lld)\n", c1, c2);
s = power_mod(c1, x, p);
s_inv = mod_inverse(s, p);
decrypted = (c2 * s_inv) % p;
printf("\nDecrypted Message: %lld\n", decrypted);
return 0;
}
```
## Output:
<img width="613" height="462" alt="image" src="https://github.com/user-attachments/assets/dac61770-d120-48b1-86a9-5888630e1642" />


## Result:
The program is executed successfully.
