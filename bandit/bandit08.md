\# Bandit Level 8 → Level 9



\## Objective

Retrieve the password for the next level by identifying the unique line in a file where all other lines are duplicated.



---



\## Given Information

\- Logged in as user `bandit8`

\- The password is stored in `data.txt`

\- The password is the only line that occurs once



---



\## Approach



First, the contents of the home directory were listed:



```bash

ls

```



This revealed a file named `data.txt`.



Since all lines except one are duplicated, the file needed to be sorted before using `uniq`, as `uniq` only detects adjacent duplicates.



The following command was used:



```bash

sort data.txt | uniq -u

```



This sorts the file and then prints only lines that appear exactly once.



---



\## Solution



The output returned a single unique line, which is the password for the next level.



---



\## Key Takeaways



\- `uniq` requires sorted input to properly detect duplicates

\- `uniq -u` prints only lines that appear once

\- Piping commands allows efficient data filtering without manual inspection



