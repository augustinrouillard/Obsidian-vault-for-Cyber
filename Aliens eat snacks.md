---
share: true
---
```markdown
# CTF Challenge: Brute-force Attack on an Incomplete AES Key

## Provided Files

- `output.txt`: Contains the encrypted flag.
- `AES.py`: Python script used to encrypt the flag.
- `readme`: Additional information about the challenge.

## Description

The flag has been encrypted using an incomplete AES key.  
The last three bytes of the key are missing.  
Your goal is to recover the full key by brute-forcing these last three bytes.

## Steps to Solve

1. **Analyze the AES Script**  
   Understand how the key is used and how the flag is encrypted.

2. **Brute-force the Last Three Bytes**  
   Generate all possible combinations for the missing three bytes of the key.

3. **Convert to Hexadecimal Format**  
   The complete key must be converted to hexadecimal format for decryption.

4. **Search for the Flag**  
   When decrypting, look for the flag format:  
   > BITCTF{...}  
   or any other format specified in the challenge.

## Tips

- Specify that you are searching for the flag format (`BITCTF{}`) to identify the correct key during brute-force.
- Automate the process with a Python script to quickly test all combinations.
```

---

**Summary**  
To solve this challenge, you need to recover the complete AES key by brute-forcing the last three bytes, decrypt the flag, and check if it matches the expected format.