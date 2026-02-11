# Bandit Level 1 → Level 2

## Objective
Retrieve the password for the next level from a file named `-`.

---

## Given Information
- Logged in as user `bandit1`
- The password is stored in a file called `-`

---

## Approach

After logging in, the contents of the home directory were listed:

```bash
ls

This revealed a single file named -.

Attempting to read the file directly using cat "-" caused the command to wait for input,
as - is commonly interpreted by Unix utilities as standard input rather than a filename.
Solution

To explicitly reference the file, a relative path was used:

```bash
cat ./-
```

This correctly treated - as a filename and displayed the password for the next level.

Key Takeaways:

- "-" is often used to represent standard input in Unix commands

- Special filenames may require explicit paths to avoid ambiguity

- Understanding how commands interpret arguments is essential when working in Unix environments
