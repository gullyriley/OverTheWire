# Bandit Level 3 → Level 4

## Objective
Retrieve the password for the next level from a hidden file located inside the `inhere` directory.

---

## Given Information
- Logged in as user `bandit3`
- The password is stored inside a file within the `inhere` directory

---

## Approach

After listing the contents of the home directory:

```bash
ls
```

A directory named `inhere` was identified.

Navigated into the directory:

```bash
cd inhere
```

Listing files normally showed no visible files:

```bash
ls
```

Since no files were displayed, a listing including hidden files was performed:

```bash
ls -a
```

This revealed a hidden file named `...Hiding-From-You`.

---

## Solution

The hidden file was read using:

```bash
cat ./...Hiding-From-You
```

This displayed the password for the next level.

---

## Key Takeaways

- Files beginning with `.` are hidden by default in Unix systems
- The `ls -a` command reveals hidden files
- Always check for hidden files when enumeration appears empty
