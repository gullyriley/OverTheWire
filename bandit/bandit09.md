\# Bandit Level 9 → Level 10



\## Objective

Retrieve the password for the next level from `data.txt`, which contains binary data.



---



\## Given Information

\- Logged in as user `bandit9`

\- The password is stored in `data.txt`

\- The password appears within human-readable strings in the file (near `=` characters)



---



\## Approach



After confirming the file was present:



```bash

ls

```



An attempt was made to search directly using `grep`:



```bash

grep "=" data.txt

```



This returned:



```

binary file matches

```



This indicates `grep` detected non-text data and did not print matching lines normally.



To extract readable text from the file first, `strings` was used, then filtered using `grep`:



```bash

strings data.txt | grep '='

```



This produced readable output containing several lines with `=` characters, including the line containing the password.



---



\## Solution



The password was identified from the human-readable output produced by:



```bash

strings data.txt | grep '='

```



---



\## Key Takeaways



\- `grep` may treat files as binary and suppress normal output when non-text bytes are present

\- `strings` extracts human-readable sequences from binary files

\- A common workflow is to extract (`strings`) then filter (`grep`) to locate relevant content



