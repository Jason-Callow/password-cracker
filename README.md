# Password Hashing & Brute Force Demonstrator

This Python-based program demonstrates key concepts in password security, including hashing, brute-force attacks, and realistic password cracking time estimation. It simulates cracking 4-digit PINs (using plaintext, SHA-256, and SHA-512 with salt) and evaluates the estimated time to crack more complex passwords hashed with Argon2, bcrypt, and PBKDF2.

This is my first independent cybersecurity project, created outside of university coursework as part of my learning journey and portfolio development. It is intended as a hands-on exploration of password security fundamentals.

**Tech Stack:** Python 3 • hashlib • bcrypt • argon2-cffi • pbkdf2_hmac • time • itertools • math • string • random

## Usage

Run the program and follow the interactive menu. Below are two example sessions.

<details>
<summary><strong>▶ Example: Pincode Cracker</strong></summary>

```
Welcome to my password hashing and brute force demo!
Please select one of the following options:
1) Pincode Cracker
2) Realistic Password Crack Estimator
3) Exit
Enter Choice: 1

Would you like to choose a pincode or generate one randomly?
1) Choose my own
2) Generate randomly
Enter Choice: 2

Pincode generated: 5494

Pincode Menu

What would you like to do?
1) Plaintext brute force
2) SHA-256 with salt
3) SHA-512 with salt
4) Choose another pincode
5) Return to main menu
Enter Choice: 2

Choose the salt length for SHA-256 brute force:
1) 1 salt - 620,000 possibilities - 8.1 seconds approx
2) 2 salt - 38,440,000 possibilities - 8.4 minutes approx
3) 3 salt - 2.38 billion possibilities - 8.7 hours approx
4) 4 salt - 148 billion possibilities - 22.5 days approx
5) Return to previous menu
Enter Choice: 2

5494 in SHA-256 is:
9200f63b0f18a3e2dbb65859e96103bb790a9a56c8cc0cce621ad549b3e42547

Enter '1' to start brute force crack
Enter '2' to return to previous menu
Enter Choice: 1

Attempts: 14,585,495 (37.94%) — 17,161 attempts/s

Pincode Cracked!

- PIN:       5494
- Salt:      xG
- Attempts:  14,585,495
- Time:      849.91 seconds
- Avg speed: 17,161 attempts/sec

```

</details>

<details>
<summary><strong>▶ Example: Realistic Password Crack Estimator</strong></summary>
  
```
Welcome to my password hashing and brute force demo!
Please select one of the following options:
1) Pincode Cracker
2) Realistic Password Crack Estimator
3) Exit
Enter Choice: 2

Passwords in real life use a hashing tool similar to Argon2, bcrypt or PBKDF2.
This tool allows you to enter a password, and see how long a brute force attack
would take to crack it, based on the hashing algorithm and your systems hardware.

What would you like to do?
1) Enter a password to estimate crack time
2) Return to main menu
Enter Choice: 1
Enter your password: password1234

Estimated entropy: 62 bits

Hashing & Cracking Estimates (on your computer):
Argon2   : 0.0607s/hash — Estimated crack time: 8.87 billion years
Bcrypt   : 0.1963s/hash — Estimated crack time: 28.70 billion years
PBKDF2   : 0.0331s/hash — Estimated crack time: 4.85 billion years

Would you like to see estimated crack times based on different attacker profiles?
1) Yes
2) No, return to previous menu
Enter Choice: 1

Estimated crack times by attacker profile:

Hobbyist:
- Argon2   : 887.34 million years
- Bcrypt   : 2.87 billion years
- PBKDF2   : 484.58 million years

Mid-tier GPU rig:
- Argon2   : 88,734.14 years
- Bcrypt   : 287,028.66 years
- PBKDF2   : 48,458.34 years

High-end GPU farm:
- Argon2   : 887.34 years
- Bcrypt   : 2,870.29 years
- PBKDF2   : 484.58 years

Nation-State (ASICs):
- Argon2   : 8.87 years
- Bcrypt   : 28.70 years
- PBKDF2   : 4.85 years

```
</details>

