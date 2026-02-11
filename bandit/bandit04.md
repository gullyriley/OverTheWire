# Bandit Level 4 → Level 5

## Objective
Identify the human-readable file in a directory of files and retrieve the password for the next level.

---

## Given Information
- Logged in as user `bandit4`
- The password is stored in the only human-readable file inside the `inhere` directory

---

## Approach

After listing the home directory:

```bash
ls
```

A directory named `inhere` was present. Navigated into it:

```bash
cd inhere
```

The directory contained multiple files with names beginning with `-`:

```bash
ls -a
```

An attempt to check file types using a wildcard failed:

```bash
file *
```

This occurred because filenames beginning with `-` can be interpreted as command options rather than filenames.

To safely analyze all files in the directory, the wildcard was expanded using an explicit path:

```bash
file ./*
```

This displayed the type of each file and revealed that one file was `ASCII text`.

---

## Solution

The readable (ASCII text) file was opened:

```bash
cat ./-file07
```

This displayed the password for the next level.

---

## Key Takeaways

- Filenames beginning with `-` can be interpreted as options by commands
- Using an explicit path like `./` or `./*` helps ensure filenames are treated as arguments
- The `file` command is useful for quickly identifying human-readable text among unknown files
