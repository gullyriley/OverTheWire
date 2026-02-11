\# Bandit Level 15 → Level 16



\## Objective

Retrieve the password for the next level by submitting the current level password to a service running on port 30001 using SSL/TLS.



---



\## Given Information

\- Logged in as user `bandit15`

\- A service is listening on `localhost` at port `30001`

\- The service requires an SSL/TLS connection

\- The current level password must be submitted to receive the next password



---



\## Approach



Since the service required SSL/TLS, a normal `nc` connection would not work.



The `openssl s\_client` utility was used to establish a secure connection:



```bash

openssl s\_client -connect localhost:30001

```



The connection initiated an SSL handshake and displayed certificate information.  

After the handshake completed, the service waited for input.



The current level password was entered and submitted.



---



\## Solution



After submitting the correct password over the SSL connection, the service responded with:



```

Correct!

<next level password>

```



This returned the password for the next level.



---



\## Key Takeaways



\- Some services require SSL/TLS rather than plain TCP

\- `openssl s\_client` allows manual interaction with encrypted services

\- Certificate warnings (such as self-signed certificates) are expected in controlled environments

\- Understanding protocol requirements is essential when interacting with network services



