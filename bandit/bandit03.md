# Bandit Level 2 → Level 3

## Objective
Retrieve the password for the next level from a file with spaces in its name.

---

## Given Information
- Logged in as user `bandit2`
- The password is stored in a file named `--spaces in this filename--`

---

## Approach

After listing the contents of the directory:

```bash
ls
```

The file --spaces in this filename-- was identified.

An initial attempt to read the file directly failed:

```bash
cat ./--spaces in this filename--
```

This produced errors because the shell interpreted each space-separated word as a separate argument.

Attempting to wrap the filename in quotes also failed:

```bash
cat "--spaces in this filename--"
```

This caused cat to interpret the name as a command-line option due to the leading --.
Solution

To ensure the filename was interpreted correctly, spaces were escaped using backslashes:

```bash
cat ./--spaces\ in\ this\ filename--
```

This successfully displayed the password for the next level.
Key Takeaways

- The shell splits arguments on spaces unless they are quoted or escaped

- Filenames beginning with -- may be interpreted as command options

- Escaping characters allows precise control over how the shell parses input
