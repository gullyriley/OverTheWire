# Bandit Level 8 → Level 9

## Objective
Retrieve the password for the next level by identifying the unique line in a file where all other lines are duplicated.

---

## Given Information
- Logged in as user `bandit8`
- The password is stored in `data.txt`
- The password is the only line that appears once

---

## Approach

After listing the directory contents:

```bash
ls
```

The file `data.txt` was identified.

An initial attempt was made to filter unique lines directly:

```bash
cat data.txt | uniq -u
```

This returned no output.

This occurred because `uniq` only detects duplicate lines that are adjacent. Since the file was not sorted, duplicates were not grouped together.

To correct this, the file was sorted before applying `uniq`:

```bash
sort data.txt | uniq -u
```

This successfully isolated the single line that appears only once.

---

## Solution

The sorted and filtered output returned one unique line, which is the password for the next level.

---

## Key Takeaways

- `uniq` only compares adjacent lines
- Sorting input is often necessary before using `uniq`
- Understanding tool behavior is essential for correct data processing
