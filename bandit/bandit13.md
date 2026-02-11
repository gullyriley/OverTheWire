\# Bandit Level 13 → Level 14



\## Objective

Use the provided private SSH key to log in as `bandit14` and retrieve the password for the next level.



---



\## Given Information

\- Logged in as user `bandit13`

\- A private SSH key file named `sshkey.private` is present

\- The key must be used to authenticate as user `bandit14`

\- The SSH service runs on port 2220



---



\## Approach



After listing the directory contents:



```bash

ls

```



The file `sshkey.private` was identified.



Attempting to use the key from within the Bandit server failed because SSH connections from localhost are restricted:



```bash

ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

```



The server rejected the connection due to local connection restrictions.



To resolve this, the private key was copied to the local machine and used from there:



```bash

ssh -i banditprivatekey.txt bandit14@bandit.labs.overthewire.org -p 2220

```



This successfully authenticated using key-based login.



---



\## Solution



After logging in as `bandit14`, the password for the next level was retrieved from:



```bash

cat /etc/bandit\_pass/bandit14

```



---



\## Key Takeaways



\- SSH supports key-based authentication using the `-i` flag

\- Some environments restrict localhost SSH connections

\- Private keys must be used from an external machine when internal connections are blocked

\- Sensitive credentials are commonly stored in `/etc` in restricted environments



