\# Bandit Level 7 → Level 8



\## Objective

Retrieve the password for the next level by locating a specific keyword within a file.



---



\## Given Information

\- Logged in as user `bandit7`

\- The password is stored in the file `data.txt`

\- The password is next to the word `millionth`



---



\## Approach



First, the contents of the home directory were listed:



```bash

ls

```



This revealed a file named `data.txt`.



Since the file likely contained many lines, searching the entire file manually would be inefficient. Instead, `grep` was used to search for the specific keyword:



```bash

cat data.txt | grep millionth

```



This filtered the file’s contents and returned the line containing the required word.



---



\## Solution



The matching line displayed the password next to the keyword `millionth`.



---



\## Key Takeaways



\- `grep` is useful for searching specific patterns within files

\- Filtering output is more efficient than manually reviewing large files

\- Combining commands using pipes (`|`) allows targeted data processing



