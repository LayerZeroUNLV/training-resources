---
title: "Beginner Linux Command Line Foundations"
order: 1
category: "linux"
description: "A beginner-friendly introduction to Linux command-line skills for cybersecurity training."
author: "Layer Zero"
tags: ["linux", "beginner", "command-line", "ctf", "foundations"]
---

# Beginner Linux Command Line Foundations

Linux command-line skills help you inspect files, run tools, read logs, and automate small tasks. Many cybersecurity challenges expect you to move around a filesystem, examine text, understand permissions, and combine simple commands.

This guide is a reference, not a list of commands to run blindly. A challenge can often be solved with several different commands. The important skill is knowing what question you are asking and choosing a command that answers it.

<!-- `notes`
Practice this topic with Linux and command-line challenges in the [Layer Zero Lab](https://lab.layer-zero.org).
Use this page as a guide while you work, but let the challenge evidence drive your decisions.
-->

## Prerequisites

- Basic keyboard comfort
- Willingness to read command output carefully
- A training environment where you are allowed to run commands

## Filesystem Basics

Linux organizes files in a tree that starts at `/`.

| Path | Common Meaning |
|------|----------------|
| `/home` | User home directories |
| `/tmp` | Temporary files |
| `/etc` | System configuration |
| `/var/log` | Logs on many systems |
| `.` | Current directory |
| `..` | Parent directory |
| `~` | Current user's home directory |

Beginner habit: always know where you are before running commands that change files.

```bash
pwd
ls
```

## Core Commands

| Task | Command Examples |
|------|------------------|
| Show current directory | `pwd` |
| List files | `ls`, `ls -la` |
| Change directory | `cd` |
| Print a file | `cat`, `less` |
| Search text | `grep`, `rg` |
| Find files | `find`, `locate` |
| Show file type | `file` |
| Show first or last lines | `head`, `tail` |
| Count lines or bytes | `wc` |
| Show running processes | `ps` |
| Show command help | `man`, `--help` |

You do not need to memorize every option. Learn how to ask for help and how to test commands on safe files.

## Permissions

Linux permissions control who can read, write, or execute a file.

Example:

```text
-rwxr-x---
```

Read the permission groups as:

| Group | Meaning |
|-------|---------|
| Owner | Permissions for the file owner |
| Group | Permissions for members of the file's group |
| Other | Permissions for everyone else |

Common letters:

- `r`: read
- `w`: write
- `x`: execute

Beginner challenge questions:

- Who owns the file?
- Can your user read it?
- Is a script executable?
- Are permissions different from what you expected?

## Pipes and Redirection

Pipes send the output of one command into another command.

```bash
cat access.log | grep "404"
```

Redirection sends output into a file or reads input from a file.

```bash
ls > files.txt
```

Useful pattern:

```bash
command | command | command
```

Build pipelines slowly. Run the first command, inspect the output, then add the next step.

## Text Inspection

Many beginner challenges hide clues in text files, logs, or command output.

Useful commands:

- `grep "word" file.txt`
- `rg "word"`
- `sort file.txt`
- `uniq -c`
- `cut -d ":" -f 1 file.txt`
- `tr`
- `strings suspicious-file`

Do not process text until you understand its structure. Look at a few lines first.

## Processes and Environment

Processes are running programs. Environment variables are values available to processes.

Useful commands:

```bash
ps aux
env
which python3
```

Beginner challenge questions:

- What process is running?
- Which user started it?
- What path is being used?
- Are there environment variables that affect behavior?

## A Beginner Linux Challenge Workflow

1. Identify your location and user.
   Use `pwd`, `whoami`, and `ls`.

2. Inventory the files.
   Look for names, sizes, permissions, hidden files, and file types.

3. Inspect before changing.
   Read files with safe commands before editing or executing anything.

4. Search with a purpose.
   Search for expected patterns, errors, usernames, flags, or configuration clues.

5. Build commands incrementally.
   Test each part before combining commands into a pipeline.

6. Explain what happened.
   A good solution describes which file, permission, process, or text pattern mattered.

## Questions To Ask Yourself

- Where am I in the filesystem?
- Which user am I?
- What files are present, including hidden files?
- What are the file permissions and owners?
- Is this file text, binary, compressed, or something else?
- What command answers my next question with the least risk?
- Can I reproduce the result from a clean starting point?

## Tooling Mindset

The shell is powerful because small commands can be combined. That also means mistakes can spread quickly.

Good habits:

- Use read-only commands first.
- Preview files before running scripts.
- Avoid copying commands you do not understand.
- Use `man` pages and `--help` output.
- Keep notes about commands that produced useful evidence.

## Safe Practice Habits

- Run commands only in systems where you have permission.
- Be careful with commands that delete, overwrite, or recursively change files.
- Do not run unknown binaries on your main workstation.
- Keep original challenge files unchanged when possible.
- Prefer learning why a command worked over only saving the final command.

## Practice Prompts

Use these prompts while working through beginner Linux challenges:

- Find all hidden files in a directory.
- Identify the type of an unknown file.
- Count how many times a word appears in a log.
- Show only lines that contain an error.
- Explain the permissions on a file in plain language.

## Summary

Linux command-line skill is mostly careful inspection and controlled experimentation.

Remember these key points:

- Know where you are before changing anything.
- Permissions, ownership, and file type are often important clues.
- Build command pipelines one step at a time.
- Tool output should answer a specific question.
- There are usually several valid command combinations for the same task.

Use this guide as a starting point, then choose commands based on the evidence in front of you.
