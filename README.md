# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
def mod_exp(base, exp, mod):
    result = 1
    base = base % mod
    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod
        exp = exp >> 1
        base = (base * base) % mod
    return result

def main():
    # Publicly known values
    p = 23  # A large prime number
    g = 5   # A primitive root modulo p

    # Private keys
    priya_private_key = int(input("Enter priya's private key: "))
    venkat_private_key = int(input("Enter venkat's private key: "))

    # Public keys
    priya_public_key = mod_exp(g, priya_private_key, p)
    venkat_public_key = mod_exp(g, venkat_private_key, p)

    print(f"priya's Public Key: {priya_public_key}")
    print(f"venkat's Public Key: {venkat_public_key}")

    # Shared secret keys
    shared_key_priya = mod_exp(venkat_public_key, priya_private_key, p)
    shared_key_venkat = mod_exp(priya_public_key, venkat_private_key, p)

    print(f"Shared Secret Key (priya): {shared_key_priya}")
    print(f"Shared Secret Key (venkat): {shared_key_venkat}")

    # Check if the shared keys match
    if shared_key_priya == shared_key_venkat:
        print(f"Key Exchange Successful! Shared Secret Key: {shared_key_priya}")
    else:
        print("Key Exchange Failed!")

if __name__ == "__main__":
    main()

```
## Output:
![image](https://github.com/user-attachments/assets/03bd367b-1dcb-4f78-9363-55cc61dcdd81)



## Result:
  The program is executed successfully

