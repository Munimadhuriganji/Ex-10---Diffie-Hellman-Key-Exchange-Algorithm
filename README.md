# Ex 10-Diffie-Hellman-Key-Exchange-Algorithm
# AIM
The aim of this project is to demonstrate the Diffie-Hellman Key Exchange algorithm in C. This 
algorithm allows two parties to securely exchange a shared secret key over an insecure
communication channel without the need to transmit the key directly.
# ALGORITHM
```
1. Two parties agree on a large prime number P and a primitive root G, which are public values.
2. Each party selects a private key (a for Alice, b for Bob).
3. Each party computes their public key:
4. Alice computes A = G^a % P
5. Bob computes B = G^b % P
6. The public keys A and B are exchanged between the parties.
7. Both parties compute the shared secret key:
8. Alice computes the key as Key = B^a % P
9. Bob computes the key as Key = A^b % P
10. The shared key generated by both parties will be identical and can be used for further
encryption.
```
# PROGRAM
```
#include <stdio.h>
#include <math.h>
// Function to perform modular exponentiation
long long int power(long long int base, long long int exp, long long int mod) {
long long int result = 1;
while (exp > 0) {
if (exp % 2 == 1)
result = (result * base) % mod;
base = (base * base) % mod;
exp = exp / 2;
}
return result;
}
int main() {
// Publicly known values: large prime number and primitive root
long long int P = 23; // Prime number
long long int G = 5; // Primitive root of P
// Private keys selected by Alice and Bob
long long int a = 6; // Alice's private key
long long int b = 15; // Bob's private key


// Public keys calculated by Alice and Bob
long long int A = power(G, a, P); // A = G^a % P
long long int B = power(G, b, P); // B = G^b % P
// Exchange public keys (A and B) over the network
// Both compute the shared secret key
long long int keyA = power(B, a, P); // Key calculated by Alice: (B^a) % P
long long int keyB = power(A, b, P); // Key calculated by Bob: (A^b) % P
// The shared key must be the same for both Alice and Bob
printf("Shared secret key calculated by Alice: %lld\n", keyA);
printf("Shared secret key calculated by Bob: %lld\n", keyB);
return 0;
}
```
# OUTPUT
![image](https://github.com/user-attachments/assets/3a1d04cd-6ce3-4a72-81ab-d4b247b1f824)

# RESULT
The program successfully demonstrates the key exchange process, where both parties calculate the
same shared secret key without directly transmitting it.
