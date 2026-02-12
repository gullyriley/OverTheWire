\# Bandit Level 18 → Level 19



\## Objective

Log in as `bandit18` and retrieve the password for the next level, despite being immediately logged out upon normal SSH login.



---



\## Given Information

\- Logged in as user `bandit17`

\- The next level user is `bandit18`

\- A normal SSH login immediately logs the user out

\- A file named `readme` contains the password



---



\## Approach



A normal SSH login attempt resulted in immediate logout. This indicated that a shell configuration file (such as `.bashrc`) was likely forcing termination of the session.



To bypass this behavior, a new shell was started without loading user configuration files.



SSH was invoked with forced terminal allocation and a custom command:



```bash

ssh -t bandit18@bandit.labs.overthewire.org -p 2220 "bash --norc"

```



Explanation:



\- `-t` forces SSH to allocate a pseudo-terminal

\- `"bash --norc"` starts Bash without reading `~/.bashrc`

\- This prevents execution of the logout command contained in the startup configuration



This provided an interactive shell.



The directory contents were then listed:



```bash

ls

```



A file named `readme` was identified.



---



\## Solution



The file was read using:



```bash

cat readme

```



This displayed the password for the next level.



---



\## Key Takeaways



\- Bash reads configuration files such as `~/.bashrc` during startup

\- The `--norc` flag prevents Bash from reading user configuration files

\- The `-t` flag forces SSH to allocate a terminal

\- Understanding shell initialization behavior can bypass restrictive environments



