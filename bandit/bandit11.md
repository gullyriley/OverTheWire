\# Bandit Level 11 → Level 12



\## Objective

Decrypt the contents of `data.txt` to retrieve the password for the next level.



---



\## Given Information

\- Logged in as user `bandit11`

\- The password is stored in `data.txt`

\- The file contents are encrypted using ROT13



---



\## Approach



After listing the directory contents:



```bash

ls

```



The file `data.txt` was identified.



An initial attempt using unrelated tools was unsuccessful. After reviewing the level description more carefully, it became clear that the file was encoded using ROT13, a simple letter substitution cipher.



To decode ROT13 in the terminal, the `tr` command was used to translate characters:



```bash

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

```



This performs a character substitution shifting letters by 13 positions in the alphabet.



---



\## Solution



The translated output revealed a readable message containing the password for the next level.



---



\## Key Takeaways



\- ROT13 is a simple substitution cipher shifting letters by 13 positions

\- The `tr` command can perform character-by-character translation

\- Understanding basic encoding schemes allows efficient decryption in the terminal



