# Linux Commands Part 1

## Overview

These are fundamental Linux commands used for file management, data inspection, and basic system interaction. They are frequently used by cybersecurity professionals when analyzing logs, reviewing scan results, working with wordlists, and managing files during assessments.

---

# touch

## Purpose

Creates an empty file.

## Example

```bash
touch notes.txt
```

## Cybersecurity Use

Create notes, wordlists, output files, and temporary files during assessments.

---

# cat

## Purpose

Displays file contents.

## Example

```bash
cat notes.txt
```

## Cybersecurity Use

View configuration files, scan outputs, logs, and wordlists.

---

# cp

## Purpose

Copies files and directories.

## Example

```bash
cp report.txt backup.txt
```

## Cybersecurity Use

Create backups before modifying files.

---

# mv

## Purpose

Moves or renames files.

## Example

```bash
mv notes.txt pentest-notes.txt
```

## Cybersecurity Use

Organize reports, scan results, and project files.

---

# rm

## Purpose

Deletes files.

## Example

```bash
rm test.txt
```

## Cybersecurity Use

Remove temporary files and unnecessary outputs.

---

# head

## Purpose

Displays the first lines of a file.

## Example

```bash
head logfile.txt
```

## Cybersecurity Use

Quickly inspect large log files.

---

# tail

## Purpose

Displays the last lines of a file.

## Example

```bash
tail logfile.txt
```

## Cybersecurity Use

Review recent log activity and events.

---

# wc

## Purpose

Counts lines, words, and characters.

## Example

```bash
wc wordlist.txt
```

## Cybersecurity Use

Determine the size of logs, reports, or wordlists.

---

# sort

## Purpose

Sorts data alphabetically or numerically.

## Example

```bash
sort users.txt
```

## Cybersecurity Use

Organize usernames, IP addresses, and scan results.

---

# uniq

## Purpose

Removes duplicate lines.

## Example

```bash
sort users.txt | uniq
```

## Cybersecurity Use

Identify unique usernames, domains, or IP addresses.

---

## Key Takeaways

* Linux commands are tools for working efficiently with data.
* Most cybersecurity tasks involve manipulating files, logs, and outputs.
* Understanding a small set of commands deeply is more valuable than memorizing hundreds.
