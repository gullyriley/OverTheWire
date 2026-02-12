\# Bandit Level 17 → Level 18



\## Objective

Identify the password for the next level by comparing two files: `passwords.old` and `passwords.new`.



---



\## Given Information

\- Logged in as user `bandit17`

\- Two files are present: `passwords.old` and `passwords.new`

\- The password is the only line that differs between the two files



---



\## Approach



First, the directory contents were listed:



```bash

ls

```



This revealed two files: `passwords.new` and `passwords.old`.



To identify the difference between the files, the `diff` command was used:



```bash

diff passwords.new passwords.old

```



The output showed a single line difference between the two files.



---



\## Solution



The differing line displayed in the output represents the password for the next level.



---



\## Key Takeaways



\- `diff` compares files line-by-line and highlights differences

\- Understanding file comparison tools avoids manual inspection

\- Efficient command usage reduces human error in analysis



