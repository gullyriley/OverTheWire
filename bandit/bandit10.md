\# Bandit Level 10 → Level 11



\## Objective

Decode the contents of `data.txt` to retrieve the password for the next level.



---



\## Given Information

\- Logged in as user `bandit10`

\- The password is stored in `data.txt`

\- The file contains Base64-encoded data



---



\## Approach



First, the contents of the home directory were listed:



```bash

ls

```



The file `data.txt` was identified.



Upon inspecting the file contents, it appeared to be Base64-encoded data.  

To decode it, the `base64` utility was used with the decode flag:



```bash

cat data.txt | base64 -d

```



This decoded the file and revealed a readable message containing the password.



---



\## Solution



The decoded output displayed the password for the next level.



---



\## Key Takeaways



\- Base64 is an encoding scheme used to represent binary data in ASCII format

\- The `base64 -d` flag decodes Base64-encoded content

\- Recognizing common encodings allows quick and efficient problem solving



