# Linux Commands — Part 2

This section covers essential Linux commands for navigation, file discovery, text searching, file identification, permissions, and command documentation. These commands are particularly useful when working with logs, files, scripts, scan results, and forensic data.

---

## 1. `pwd`

### Meaning

Prints the current working directory.

### Example

```bash
pwd
```

### Cybersecurity Use

Helps determine exactly where you are in the filesystem before running commands or working with files.

---

## 2. `ls`

### Meaning

Lists files and directories in the current location.

### Example

```bash
ls
```

To show hidden files and detailed information:

```bash
ls -la
```

### Cybersecurity Use

Useful for inspecting directories, hidden configuration files, permissions, ownership, and timestamps.

---

## 3. `cd`

### Meaning

Changes the current working directory.

### Example

```bash
cd /tmp
```

Go back one directory:

```bash
cd ..
```

Go to your home directory:

```bash
cd ~
```

### Cybersecurity Use

Essential for navigating through tools, scripts, evidence, logs, and other files during security work.

---

## 4. `mkdir`

### Meaning

Creates a new directory.

### Example

```bash
mkdir scans
```

Create nested directories:

```bash
mkdir -p project/recon/results
```

### Cybersecurity Use

Useful for organizing scan results, reconnaissance data, scripts, reports, and lab files.

---

## 5. `find`

### Meaning

Searches for files and directories based on specified criteria.

### Example

```bash
find . -name "test.txt"
```

Find all `.log` files:

```bash
find /var/log -name "*.log"
```

### Cybersecurity Use

Useful for locating logs, configuration files, scripts, evidence, and specific file types during system analysis or forensic investigations.

---

## 6. `grep`

### Meaning

Searches text for a specified pattern.

### Example

```bash
grep "Failed" auth.log
```

Search recursively:

```bash
grep -r "password" .
```

### Cybersecurity Use

Extremely useful for filtering logs, scan output, configuration files, source code, and other text-based data.

---

## 7. `file`

### Meaning

Determines the type of a file based on its contents rather than simply relying on its filename extension.

### Example

```bash
file suspicious.bin
```

### Cybersecurity Use

Useful during malware analysis and digital forensics when investigating unknown or suspicious files.

---

## 8. `less`

### Meaning

Displays a file one screen at a time, making it easier to read large files.

### Example

```bash
less large.log
```

Useful controls:

```text
Space  → Next page
b      → Previous page
/word  → Search
q      → Quit
```

### Cybersecurity Use

Useful for examining large logs, scan results, reports, and other files without loading the entire contents into the terminal at once.

---

## 9. `chmod`

### Meaning

Changes the permissions of files and directories.

### Example

```bash
chmod 700 script.sh
```

Make a script executable:

```bash
chmod +x script.sh
```

### Cybersecurity Use

Important for understanding Linux access control and managing permissions for scripts, sensitive files, and security tools.

---

## 10. `man`

### Meaning

Opens the manual page for a command.

### Example

```bash
man ls
```

For Nmap:

```bash
man nmap
```

### Cybersecurity Use

Learning to use documentation is an essential security skill. Instead of memorizing every command option, use the manual to understand available functionality and syntax.

---

# Key Takeaways

* `pwd`, `ls`, and `cd` provide basic filesystem navigation.
* `find` helps locate files and directories.
* `grep` is extremely useful for searching and filtering security-related data.
* `file` helps identify unknown files.
* `less` makes large files easier to inspect.
* `chmod` introduces Linux permissions and access control.
* `man` provides built-in documentation for Linux commands.

These commands form part of the Linux foundation needed for working effectively with Kali Linux and cybersecurity tools.
