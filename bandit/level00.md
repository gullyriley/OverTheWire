# Bandit Level 0 → Level 1

## Objective
Log into the Bandit server and retrieve the password for the next level.

---

## Given Information
- SSH access to the Bandit server
- Username: `bandit0`
- Password: `bandit0`

---

## Approach

After connecting to the server via SSH, the contents of the home directory were listed to identify any files of interest:
```bash
ls
```

A file named readme was present in the directory.

## Solution

The contents of the file were displayed using the cat command:
```bash
cat readme
```

This revealed the password required to access the next level.

## Key Takeaways:

    Basic SSH usage for remote access

    Listing directory contents with ls

    Reading file contents using cat
