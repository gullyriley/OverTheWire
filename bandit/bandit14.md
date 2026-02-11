\# Bandit Level 14 → Level 15



\## Objective

Retrieve the password for the next level by submitting the current level's password to a service running on port 30000 on localhost.



---



\## Given Information

\- Logged in as user `bandit14`

\- The password for the next level can be retrieved by submitting the current level password

\- The service is listening on `localhost` at port `30000`



---



\## Approach



An initial attempt was made using SSH:



```bash

ssh bandit15@localhost -p 30000

```



This failed because port 30000 is not running an SSH service.



Since the level description specified submitting data to a port, a TCP connection tool was required. The `nc` (netcat) utility was used to connect to the service:



```bash

nc localhost 30000

```



After establishing the connection, the current level password was entered and submitted.



---



\## Solution



Upon submitting the correct password to the service via `nc`, the server responded with:



```

Correct!

<next level password>

```



This returned the password for the next level.



---



\## Key Takeaways



\- Not all open ports run SSH services; protocol matters

\- `nc` (netcat) allows direct TCP communication with services

\- Some challenges require interacting with network services rather than files

\- Understanding client/server interaction is essential in security contexts



