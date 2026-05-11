---
title: "File Inspection And Text Processing"
order: 2
category: "linux"
description: "A beginner-friendly guide to inspecting files and processing text from the Linux command line."
author: "Layer Zero"
tags: ["linux", "files", "text-processing", "command-line", "beginner"]
---

# File Inspection And Text Processing

Many cybersecurity challenges begin with a file, directory, archive, script, log, or command output. Linux gives you small tools for answering simple questions about those artifacts.

This guide focuses on inspecting before changing. The goal is to understand what you have, what it contains, and what question to ask next.

<!-- `notes`
Practice this topic with Linux and command-line challenges in the [Layer Zero Lab](https://lab.layer-zero.org).
Review [Beginner Linux Command Line Foundations](https://www.layer-zero.org/training/linux/beginner-linux-command-line-foundations) if you need the broader context first.
Build commands one step at a time so you know which part produced the result.
-->

## Prerequisites

- Basic terminal comfort
- A training environment where you are allowed to run commands
- A folder for challenge files and notes

## Inspect Before You Act

When you receive a file or directory, start with read-only questions.

| Question | Useful Commands |
|----------|-----------------|
| Where am I? | `pwd` |
| What files are here? | `ls`, `ls -la` |
| What type of file is this? | `file` |
| How large is it? | `ls -lh`, `wc -c` |
| Is it readable text? | `head`, `less`, `cat` |
| Does it contain readable strings? | `strings` |
| What are the first bytes? | `xxd`, `hexdump` |

Do not run an unknown file just because it is executable. Inspect it first.

<!-- `warning` Avoid executing unknown binaries or scripts on your host machine. Use a lab VM or container when running unknown code is part of an authorized exercise. -->

## Listing Files

Basic listing:

```bash
ls
```

Detailed listing:

```bash
ls -la
```

Look for:

- Hidden files that start with `.`
- Unexpected file sizes
- Executable permissions
- Recently modified files
- Archives or compressed files
- Names that hint at the challenge theme

## Identifying File Types

The `file` command checks file signatures and other clues.

```bash
file unknown
```

Example output:

```text
unknown: PNG image data, 800 x 600, 8-bit/color RGB, non-interlaced
```

File extensions can be wrong. Trust evidence over names.

## Viewing Text Safely

For small files:

```bash
cat notes.txt
```

For larger files:

```bash
less access.log
```

For a quick preview:

```bash
head access.log
tail access.log
```

Use `less` when you are not sure how large a file is.

## Searching Text

Search one file:

```bash
grep "error" access.log
```

Search recursively with ripgrep:

```bash
rg "password"
```

Useful search ideas:

- `flag`
- `error`
- `admin`
- Usernames
- File extensions
- URLs
- Timestamps
- Repeated IDs

Search terms should come from the challenge evidence. Do not only search for `flag` and stop.

## Counting And Sorting

Count lines, words, and bytes:

```bash
wc access.log
```

Count matching lines:

```bash
grep "404" access.log | wc -l
```

Sort values:

```bash
sort names.txt
```

Count repeated lines:

```bash
sort names.txt | uniq -c
```

Pipelines are powerful. Build them slowly and inspect each stage.

## Cutting Columns

Some files are structured by delimiters such as commas, spaces, tabs, or colons.

Example:

```text
alice:1001:admin
bob:1002:user
```

Print the first colon-separated field:

```bash
cut -d ":" -f 1 users.txt
```

Output:

```text
alice
bob
```

Before cutting columns, look at the file and identify its structure.

## Viewing Bytes

Text tools are not enough for every file. Use a hex viewer when the file is binary or when signatures matter.

```bash
xxd unknown | head
```

Look for:

- File signatures
- Readable text inside binary data
- Repeated byte patterns
- Appended data near the end of a file

If you see readable text inside binary data, treat it as a clue, not an automatic answer.

## Useful Command Patterns

| Goal | Pattern |
|------|---------|
| Preview file | `head file.txt` |
| Search recursively | `rg "term"` |
| Count matches | `rg "term" file.txt | wc -l` |
| Sort and count repeated lines | `sort file.txt | uniq -c` |
| Show file type | `file artifact` |
| Show strings in binary | `strings artifact` |
| View first bytes | `xxd artifact | head` |

## A Beginner File Inspection Workflow

1. Create a working copy if the file is important.
2. List the directory with `ls -la`.
3. Identify file types with `file`.
4. Preview text files with `head` or `less`.
5. Search for meaningful terms with `grep` or `rg`.
6. Use `strings` or `xxd` for binary files.
7. Record what each command revealed.
8. Decide the next command based on the evidence.

## Practice Prompts

Use these prompts in a lab directory:

- Find all hidden files.
- Identify the type of every file in a directory.
- Count how many lines contain the word `error`.
- Find the most repeated line in a file.
- Extract the first field from a colon-separated file.
- Inspect the first bytes of an unknown file.

## Summary

Linux file inspection is about asking small questions and using small tools to answer them.

Remember these key points:

- Inspect before executing.
- File extensions can be misleading.
- Use `less`, `head`, and `tail` for safe previews.
- Use `grep` or `rg` to search with purpose.
- Build pipelines one command at a time.
- Use `xxd` and `strings` when files are not plain text.

A good command is one you can explain. Start simple, inspect the result, and then add complexity.
