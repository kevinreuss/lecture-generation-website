# Diffie-Hellman Key Exchange

The Diffie-Hellman Key Exchange is a method of securely exchanging cryptographic keys over a public network. The protocol is based on the "discrete logarithm" problem which makes it computationally impractical to obtain the private key.

## How it Works

There are two publicly known numbers: a prime number `p`, and a base `g` (primitive root modulo). The two parties, Alice and Bob, generate private keys `a` and `b` respectively.

Alice calculates her public key `A` using the formula `A = g^a mod p` and sends `A` to Bob. Similarly, Bob calculates his public key `B` using the formula `B = g^b mod p` and sends `B` to Alice.

They then calculate the shared secret key using the other party's public key and their private key. Alice computes `s = B^a mod p` and Bob computes `s = A^b mod p`. It's mathematically proven that both equations will produce the same result `s`.

```python
# Python example: 

# public numbers
p = 23
g = 5

# Alice's private key
a = 6
# Alice's public key
A = (g**a) % p

# Bob's private key
b = 15
# Bob's public key
B = (g**b) % p

# Shared secret key
s_Alice = (B**a) % p
s_Bob = (A**b) % p

assert s_Alice == s_Bob  # This will be True
```

## Security Aspects

The security of the Diffie-Hellman protocol comes from the difficulty of the discrete logarithm problem. While it's easy to generate the public keys given `g`, `p` and the private key, it's computationally infeasible to reverse the process and obtain the private key given `g`, `p` and the public key. 

However, the protocol is vulnerable to man-in-the-middle attacks if the authenticity of public keys is not verified. To mitigate this, use Diffie-Hellman in conjunction with a method for verifying public keys, like digital signatures.