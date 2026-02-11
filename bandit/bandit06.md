# Bandit Level 6 → Level 7

## Objective
Find the file with specific ownership and size constraints somewhere on the system and retrieve the password for the next level.

---

## Given Information
- Logged in as user `bandit6`
- The file is:
  - Owned by user `bandit7`
  - Group-owned by `bandit6`
  - Exactly 33 bytes in size

---

## Approach

The home directory did not contain any relevant files:

```bash
ls -a
```

Since the file could be located anywhere on the system, a system-wide search was performed using `find`:

```bash
find / -type f -size 33c -group bandit6 -user bandit7
```

This search produced several permission denied messages (expected when searching from `/` without elevated privileges), but one valid result was identified:

```
/var/lib/dpkg/info/bandit7.password
```

---

## Solution

The file was read using:

```bash
cat /var/lib/dpkg/info/bandit7.password
```

This displayed the password for the next level.

---

## Key Takeaways

- `find` can filter files by user ownership (`-user`) and group ownership (`-group`)
- System-wide searches may produce permission errors when scanning restricted directories
- Combining multiple constraints significantly reduces the search space
