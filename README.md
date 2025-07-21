# Password Hashing & Brute Force Demonstrator

This Python-based program demonstrates key concepts in password security, including hashing, brute-force attacks, and realistic password cracking time estimation. It simulates cracking 4-digit PINs (using plaintext, SHA-256, and SHA-512 with salt) and evaluates the estimated time to crack more complex passwords hashed with Argon2, bcrypt, and PBKDF2.

This is my first independent cybersecurity project, created outside of university coursework as part of my learning journey and portfolio development. It is intended as a hands-on exploration of password security fundamentals.

**Tech Stack:** Python 3 • hashlib • bcrypt • argon2-cffi • pbkdf2_hmac • time • itertools • math • string • random

## Usage

Run the program and follow the interactive menu. Below are two example sessions.

<details>
<summary><strong> Example: Pincode Cracker</strong></summary>

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
<summary><strong> Example: Realistic Password Crack Estimator</strong></summary>
  
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

## How It Works

This project demonstrates two types of password attacks:

1. **Real-time Brute-force Attacks** on 4-digit PINs hashed with SHA-256 and SHA-512 (with configurable salt length).
2. **Crack Time Estimation** for user-entered passwords using modern key derivation functions: Argon2, bcrypt, and PBKDF2.

The program benchmarks how long each algorithm takes to hash the user's password on the local machine. It then estimates how long a brute-force attack would take, based on the password’s entropy and hashing speed.

A range of attacker profiles (from hobbyists to nation-states) illustrate how computational resources influence crack time.

## How It Works

This project demonstrates two core security concepts:
1. Real-Time Brute-Force Attacks on Hashed PINs

The program allows users to select or generate a 4-digit PIN, which is then hashed using either:

- SHA-256

- SHA-512

A randomly generated alphanumeric salt (with user-configurable length) is prepended to the PIN before hashing. The program performs a brute-force attack by systematically attempting every possible combination of salt and 4-digit PIN, simulating a realistic offline cracking scenario.

This demonstrates how salting significantly increases the computational complexity of cracking even a simple PIN and shows how the difficulty grows exponentially with longer salt lengths.

2. Password Crack Time Estimation Using Industry Hashing Algorithms

When a user enters a password, the program:

- Estimates entropy in bits based on character set diversity and password length

- Benchmarks the time required to hash the password using three industry-standard key derivation functions:

        Argon2

        bcrypt

        PBKDF2-HMAC-SHA256

- Calculates an estimated brute-force crack time based on the entropy and hash time:

Estimated Time = 2^entropy bits × time per hash
Estimated Time = 2^entropy bits × time per hash

It then presents crack time estimates across four attacker profiles:
- Hobbyist (10 hashes/second)
- Mid-tier GPU Rig (100,000 hashes/second)
- High-end GPU Farm (10,000,000 hashes/second)
- Nation State (1,000,000,000 hashes/second)

## Limitations & Security Considerations

This project is designed for educational purposes and demonstration only. While it simulates password hashing and brute-force attacks, there are several important limitations to keep in mind:
1. Hash Time Does Not Equal Security

The time it takes to compute a hash on a local machine does not directly reflect the security strength of that algorithm.

For example, Argon2 often appears faster than bcrypt in this tool, but that is misleading without context. Argon2 is designed to be memory-hard, meaning its security comes from requiring large amounts of memory — making it much harder to parallelize efficiently on GPUs or ASICs. Bcrypt and PBKDF2, by contrast, are CPU-bound.

- Key Point: Argon2 is considered stronger than bcrypt or PBKDF2 despite sometimes hashing faster in single-threaded benchmarks.

2. Real-World Attack Techniques Are More Sophisticated

This program models brute-force attacks (i.e., trying every possible password), but real attackers rarely do this for long passwords due to infeasibility. Instead, they often use:

    Rainbow tables (precomputed hash lookups — mitigated by salting)

    Dictionary attacks (trying common or leaked passwords)

    Credential stuffing (reusing stolen hashes from breaches)

    Phishing, malware, and social engineering

    Side-channel attacks on poorly implemented hashers

This tool does not simulate those attack vectors and should not be used to draw conclusions about security in real-world systems.
3. No Multi-Factor Authentication (MFA) Consideration

The tool evaluates crack times based solely on password strength. In reality, many systems today implement multi-factor authentication, which significantly reduces the effectiveness of brute-force or hash cracking attacks.

- Key Point: A strong password is important, but layered defenses like MFA, account lockout policies, and rate limiting are equally vital.

4. Simplified Entropy and Assumptions

Entropy estimation in this tool is based on character set and password length. This does not account for:

    Predictable patterns or keyboard walks

    Leaked passwords in known breaches

    User behavior biases

As a result, the estimated entropy and crack times are theoretical best-case scenarios, not guarantees.
