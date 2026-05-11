---
title: "Tools And Resources"
order: 4
category: "getting-started"
description: "A beginner-friendly reference for common cybersecurity training tools, resources, and safe usage habits."
author: "Layer Zero"
tags: ["getting-started", "tools", "resources", "beginner", "reference"]
---

# Tools And Resources

Cybersecurity tools help you inspect evidence, repeat tests, and understand systems. They do not replace reasoning. A tool can show you output, but you still need to decide what the output means.

This page is a starting reference for common tools and Layer Zero resources. You do not need to install everything at once. Add tools as the challenges require them.

<!-- `notes`
Practice hands-on in the [Layer Zero Lab](https://lab.layer-zero.org).
Check the [Layer Zero Discord](https://discord.gg/ftmmWdnGmC) for CTF updates, community guidance, and event announcements.
If you are new to lab setup, read [Setting Up Your Environment](https://www.layer-zero.org/training/getting-started/setting-up-your-environment) first.
-->

## Layer Zero Resources

| Resource | Use It For | Link |
|----------|------------|------|
| Layer Zero Training | Reading training documents and topic guides | [Layer Zero Training](https://www.layer-zero.org/training) |
| Layer Zero Lab | Practicing hands-on cybersecurity challenges | [Layer Zero Lab](https://lab.layer-zero.org) |
| Layer Zero Discord | Community updates, CTF information, and help | [Layer Zero Discord](https://discord.gg/ftmmWdnGmC) |

Use the documents, lab, and Discord together. Read enough to get oriented, practice in the lab, then ask better questions when you get stuck.

## Tool Selection Mindset

Before using a tool, ask:

- What question am I trying to answer?
- What input does this tool need?
- What output do I expect?
- Is the data safe to paste, upload, or scan?
- Can I reproduce what I did later?

<!-- `tip` A small tool you understand is usually better than a large tool you are using blindly. -->

## Setup And Environment

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| Kali Linux | Security-focused Linux distribution commonly used in training | [Kali Downloads](https://www.kali.org/get-kali/) |
| Parrot OS | Security-focused Linux distribution with a Security Edition | [Parrot OS Downloads](https://parrotsec.org/download/) |
| VirtualBox | Running local virtual machines | [VirtualBox Downloads](https://www.virtualbox.org/wiki/Downloads) |
| VMware Workstation Pro | Running local virtual machines on Windows or Linux | [VMware Workstation Pro](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion) |
| UTM | Running virtual machines on macOS | [UTM](https://mac.getutm.app/) |
| QEMU | Emulation and virtualization used directly or by other tools | [QEMU](https://www.qemu.org/) |
| Python | Scripting, parsing, automation, and small experiments | [Python Downloads](https://www.python.org/downloads/) |
| Git | Version control for notes, scripts, and training artifacts | [Git Downloads](https://git-scm.com/downloads) |
| Visual Studio Code | Text editing, notes, scripts, and terminal workflows | [VS Code](https://code.visualstudio.com/) |

Start with one VM and a notes folder. A clean, resettable environment matters more than having every tool installed.

## Web Security

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| Browser developer tools | Inspecting HTML, storage, console output, and network requests | [Chrome DevTools](https://developer.chrome.com/docs/devtools/) |
| MDN browser devtools guide | Learning what browser developer tools are and how to use them | [MDN DevTools Guide](https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Tools_and_setup/What_are_browser_developer_tools) |
| Burp Suite Community Edition | Intercepting, modifying, and replaying authorized web requests | [Burp Suite Community](https://portswigger.net/burp/communitydownload) |
| OWASP ZAP | Intercepting and testing authorized web applications | [ZAP Download](https://www.zaproxy.org/download/) |

Use interception tools only against systems you are authorized to test. For beginner labs, focus on understanding requests and responses before scanning.

## Cryptography And Data Formats

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| CyberChef | Encoding, decoding, hashing, XOR, compression, and data transformation experiments | [CyberChef](https://gchq.github.io/CyberChef/) |
| CyberChef GitHub | Source code and local-running options for CyberChef | [CyberChef GitHub](https://github.com/gchq/CyberChef) |
| Python | Writing small repeatable scripts for transformations and brute-force experiments | [Python Downloads](https://www.python.org/downloads/) |
| hashcat | Authorized password-recovery and hash-cracking labs | [hashcat](https://hashcat.net/hashcat/) |
| John the Ripper | Authorized password-auditing and hash-cracking labs | [John the Ripper](https://www.openwall.com/john/) |

<!-- `warning` Password-recovery tools should only be used on hashes, files, and systems you are authorized to test. Do not use them against real accounts or data you do not own. -->

## Networking

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| Wireshark | Packet capture analysis and protocol inspection | [Wireshark Download](https://www.wireshark.org/download.html) |
| Nmap | Authorized host and service discovery | [Nmap Download](https://nmap.org/download) |
| curl | HTTP requests from the command line | [curl](https://curl.se/) |
| dig | DNS query inspection | [BIND Tools](https://www.isc.org/bind/) |

Networking tools can affect real systems. Scan only targets that are explicitly in scope.

## Linux And Command Line

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| man pages | Local command documentation | Run `man command` in Linux |
| ExplainShell | Breaking down shell commands while learning | [ExplainShell](https://explainshell.com/) |
| Python | Scripting and data processing | [Python Downloads](https://www.python.org/downloads/) |
| Git | Tracking notes and scripts | [Git Downloads](https://git-scm.com/downloads) |

Many Linux skills come from combining small commands. Build pipelines one step at a time and inspect output before adding the next command.

## Digital Forensics

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| ExifTool | Reading and editing file metadata | [ExifTool](https://exiftool.org/) |
| Autopsy | Disk image and filesystem forensics | [Autopsy](https://www.autopsy.com/) |
| Volatility 3 | Memory forensics | [Volatility 3 GitHub](https://github.com/volatilityfoundation/volatility3) |
| Wireshark | Network forensics and packet capture review | [Wireshark Download](https://www.wireshark.org/download.html) |

Keep original evidence unchanged. Work from copies and record what each tool did.

## OSINT

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| Wayback Machine | Viewing archived versions of public web pages | [Wayback Machine](https://web.archive.org/) |
| crt.sh | Searching public certificate transparency records | [crt.sh](https://crt.sh/) |
| Have I Been Pwned | Checking whether your own email appears in known breach data | [Have I Been Pwned](https://haveibeenpwned.com/) |
| VirusTotal | Checking URLs, domains, and files in public security datasets | [VirusTotal](https://www.virustotal.com/) |

Be careful with OSINT tools. Public does not mean harmless, and online services may store or share submitted data.

## Reverse Engineering

| Tool Or Resource | Use It For | Link |
|------------------|------------|------|
| Ghidra | Local decompilation, disassembly, graphing, and scripting | [Ghidra](https://github.com/NationalSecurityAgency/ghidra) |
| Dogbolt Decompiler Explorer | Comparing decompiler output in the browser | [Dogbolt](https://dogbolt.org/) |
| Binary Ninja Free | Local reverse engineering with a free non-commercial option | [Binary Ninja Free](https://binary.ninja/free) |
| Binary Ninja Cloud | Browser-based binary analysis | [Binary Ninja Cloud](https://cloud.binary.ninja/) |
| IDA Free | Free non-commercial disassembler and cloud decompiler option | [IDA Free](https://hex-rays.com/ida-free) |
| Compiler Explorer | Learning how source code compiles to assembly | [Compiler Explorer](https://godbolt.org/) |

<!-- `warning` Do not upload private binaries, proprietary software, malware from real incidents, or unknown sensitive files to online reverse engineering tools. Use local tools when the file contents matter. -->

## Online Tool Safety

Before using an online tool, ask:

- Is this public training data?
- Could this file contain personal data, credentials, tokens, keys, or proprietary code?
- Does the service store submissions?
- Does the service share submissions with partners or other users?
- Can I use a local tool instead?

If you are unsure, treat the data as sensitive and do not upload it.

## Building Your Toolkit Over Time

Recommended beginner progression:

1. Browser, notes, and Layer Zero Lab access
2. Linux VM with basic terminal tools
3. Python and CyberChef
4. Browser developer tools and Burp or ZAP
5. Wireshark
6. ExifTool and basic forensics tools
7. Ghidra, Dogbolt, or Binary Ninja for reverse engineering

Add tools when you have a reason. Installing tools is not the same as learning them.

## Summary

Tools are useful when they answer clear questions.

Remember these key points:

- Use official downloads when possible.
- Learn a small toolkit before expanding.
- Keep notes about commands, settings, and outputs.
- Do not upload sensitive data to online tools.
- Use scanners and offensive tools only in authorized environments.
- Let the challenge evidence choose the tool, not the other way around.

Return to this page when you need a tool, but rely on your observations to decide what to try next.
