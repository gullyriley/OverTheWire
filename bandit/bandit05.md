# Bandit Level 5 → Level 6

## Objective
Locate the file that meets specific conditions (size and readability) and retrieve the password for the next level.

---

## Given Information
- Logged in as user `bandit5`
- The password is located somewhere inside the `inhere` directory
- The file is human-readable and exactly 1033 bytes in size

---

## Approach

Navigating into the `inhere` directory:

```bash
cd inhere
```

A filtered search was performed using `find`, targeting only files that matched the required size:

```bash
find * -type f -size 1033c ! -executable
```

This returned a single result:

```
maybehere07/.file2
```

---

## Solution

The identified file was opened:

```bash
cat maybehere07/.file2
```

This displayed the password for the next level.

---

## Key Takeaways

- The `find` command can filter files based on specific criteria such as size
- Combining search constraints is more efficient than manually inspecting files
- Careful reading of challenge requirements helps reduce unnecessary enumeration
