\# Bandit Level 16 → Level 17



\## Objective

Identify the correct SSL service among multiple open ports and submit the current level password to retrieve a private SSH key.



---



\## Given Information

\- Logged in as user `bandit16`

\- Multiple ports between 31000–32000 are open on localhost

\- One of these ports is an SSL service that will respond correctly when sent the current level password



---



\## Approach



First, the relevant ports were scanned:



```bash

nmap -p 31046,31518,31691,31790,31960 localhost

```



All listed ports were open.



Version detection was then performed to identify service types:



```bash

nmap -sV -p 31046,31518,31691,31790,31960 localhost

```



This revealed that some ports were plain `echo` services, while others were `ssl` services.



The SSL ports were tested using:



```bash

openssl s\_client -connect localhost:<port>

```



One port required the `-quiet` flag due to TLS message noise:



```bash

openssl s\_client -connect localhost:31790 -quiet

```



After establishing the SSL connection, the current level password was submitted.



---



\## Solution



The correct SSL service responded with:



```

Correct!

-----BEGIN RSA PRIVATE KEY-----

...

-----END RSA PRIVATE KEY-----

```



This private key was used to authenticate as the next level user.



---



\## Key Takeaways



\- `nmap -sV` helps identify service types, not just open ports

\- Not all open ports provide useful services

\- SSL services require tools like `openssl s\_client`

\- The `-quiet` flag can suppress TLS control messages

\- Careful enumeration prevents unnecessary brute-force attempts



