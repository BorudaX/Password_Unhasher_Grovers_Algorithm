# Implementing Grovers Algorithm: Password Unhasher
Submission for Wisconsin Quantum Hackathon 2023, IBM Qiskit Fall Fest '23


Media claims Quantum Computing can crack modern cryptography and break the internet. But is this true? This implementation demonstrates how it might for certain non-quantum-proof hashing algorithms

## Inspiration
In the WQCC Qiskit Fall fest 2023 Introduction to Quantum Computing presentation, Ari and the WQCC team breezed through a bunch of Quantum Computing applications. These include coming up with new molecules, allow huge advances in Materials Science Research, or raise important security breaches in modern cryptography. Cryptography, the one field that sustaing the internet. Both media and professionals claim Quantum Computing can break the internet. 

Is this claim real or hype? And if it's real, how? After all, I only know about qubits and applying x or cx gates. How can this crack the internet?


## What's the idea
Everyone talks about Shor's algorithm, capable of breaking current crytography standards such as RSA (if we had the hardware potential). But what about Grover's?

In this project I showcase the implementation of a less spoken algorithm that raises concerns to password security: Grover's algorithm. Here's a reasonable explanation of Grover's algorithm: https://www.quantum-inspire.com/kbase/grover-algorithm/


Summarized in simple terms:
Grover's algorithm is a search algorithm that can search in an unordered database at O(sqrt(N)) instead of the fastest classical for an unordered database, O(N), as long as an Oracle function is provided.

Cool. But what is the Oracle? What can it be?

The Oracle is a function that recognizes the value(s) we're looking for, and can be implemented as a quantum circuit. 
(More technical description: https://quantumcomputing.stackexchange.com/questions/1419/does-the-oracle-in-grovers-algorithm-need-to-contain-information-about-the-enti)

The main issue behind the Oracel is it's creation, which can be resource expensive in certain search implementations. This means it may (or rather will) perform worse than in the classical implementations of the same search cases. 

There's one example, however, where the oracle is required in both classical and quantum implementations, making quantum the clear outperformer: password hashing.

 
Here's everything you need to know about password hashing and salting: https://stytch.com/blog/what-is-password-hashing/



## What it actually does
This implementation simulates a password hashing situation with Grover's algorithm. It runs in a very simple and small test case:

1. Password is an integer with a defined amount of bits (recommended example, 8 bits / max int 512, as it gets very slow)
2. The hash algorithm (in classical) takes the password as bits, and flips every even bit. E.g. 1001 becomes 0011
3. The hash algorithm adds two random salt bits at the end. E.g. 1001 becomes 100100 or 100110 or ...
4. Grover's algorithm is ran with the hash algorithm as the Oracle and with the fully hashed value.
5. Grover's algorithm finds both the inputted hash and the password in bits (+2 bits which are removed) with the Quantum Circuit.

This example has some obvious limitations, as it's unrealistic to simplify a hashing algorithm to such extent and it only works with a password from 0 to 512 (which is ridiculous), but it's a working depiction of how the Grover's algorithm could potentially be implemented with real hashing algorithms and real cryptography scenarios, assuming we can get to the necessary quantum hardware potential and we can adequately replicate hashing algorithms in quantum circuits.


## How I built it
The implementation was built with Python and Qiskit on a Jupyter Notebook. 


## Challenges I ran into
1. Understanding Quantum Algorithm.
2. Understanding Quantum Algorithm.
3. Running Qiskit in local device instead of Quantum Lab.
4. Implementing Quantum Algorithm.
5. Understanding Quantum Alrogithm.
6. More doubting on how the algorithm actually solves the issue
7. Finding the real life implementation that could work
8. WHAT IS AN ORACLE


## Accomplishments that I'm proud of / What I've learned
1. The implementation works! :D
2. I learned the general idea behind Grover's algorithm
3 I've learned about a bunch of quantum algorithms out of the leading Shore's algorithm
4 I've learned from scratch about password hashing and salting, and recreated a simple, 100% secure-you-should-definitely-use hashing algorithm
5. I've learned about setting up environments locally and how to pair it with GitHub (such that, if I change devices, I can redownload everything again easily, requirements.txt)
6. Practiced my python again after not using it in a while. 


## What's next for Grover's Algo implementation in reversing Hashing Algo
There's a bunch of areas that can be improved with the implementation:
1. Implement with a real hashing algorithm
2. Implement with larger passwords, more qubits
3. Give a more neat interface, or add functionality for public to use
4. Run on real quantum computer

These are mainly limitedby our current quantum hardware potential, so it's hard to plan how much of this can be implemented.

