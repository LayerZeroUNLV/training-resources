---
title: "Setting Up Your Environment"
order: 2
category: "getting-started"
description: "A beginner-friendly guide to choosing and preparing a safe cybersecurity training environment."
author: "Layer Zero"
tags: ["getting-started", "environment", "kali", "parrot", "virtual-machines", "beginner"]
---

# Setting Up Your Environment

A good training environment lets you practice without putting your personal computer, school systems, work systems, or real data at unnecessary risk. You do not need a perfect setup on day one. You need a setup that is safe enough to learn, easy enough to reset, and flexible enough to support different challenge categories.

This guide helps you choose where to practice, which tools to install first, and when Kali, Parrot OS, virtual machines, or browser-based tools make sense.

<!-- `notes`
Practice hands-on in the [Layer Zero Lab](https://lab.layer-zero.org).
Use official downloads for operating systems and tools whenever possible.
Start simple: a browser, notes, and one Linux VM are enough for many beginner challenges.
-->

## Prerequisites

- A computer you are allowed to use for training
- A stable internet connection
- Enough free storage for tools or virtual machines
- Basic comfort installing software

You do not need an expensive workstation to start. Many beginner challenges can be solved with a browser, terminal, and a few free tools.

## Start With The Safest Simple Setup

For most beginners, the recommended path is:

1. Use your normal computer as the host.
2. Install a virtualization tool.
3. Run a dedicated Linux security VM for training.
4. Take snapshots before major changes.
5. Keep personal files and training files separate.

This gives you a reset point when something breaks, and it avoids mixing real personal data with lab activity.

## Host, Guest, and VM Basics

| Term | Meaning |
|------|---------|
| Host | Your physical computer and main operating system |
| Guest | The operating system running inside a virtual machine |
| Virtual machine | A simulated computer running inside your host |
| Snapshot | A saved VM state you can return to later |
| Shared folder | A folder exposed between host and guest |
| NAT network | A common VM network mode that lets the guest reach the internet through the host |

Think of a VM as a practice workspace. It is not magic protection, but it is easier to reset and isolate than your main operating system.

## Kali Linux, Parrot OS, Or Something Else?

Kali Linux and Parrot OS are both popular security-focused Linux distributions. Either can work for beginner training.

| Option | Good For | Beginner Notes |
|--------|----------|----------------|
| Kali Linux | Penetration testing, CTFs, common security tooling | Widely used in training; official prebuilt VMs are available |
| Parrot OS Security Edition | Security labs, privacy tooling, general-purpose security work | Also beginner-usable; choose the Security Edition for training tools |
| Ubuntu or Debian | General Linux learning and scripting | Less security-tool-focused by default, but good for learning Linux fundamentals |
| Browser-only setup | Web, OSINT, some crypto, and some lab tasks | Fastest start, but not enough for every category |

Do not spend too much time trying to pick the perfect distribution. If you are unsure, start with one official prebuilt VM and learn the workflow. You can add another VM later.

## Recommended VM Approach

Use a prebuilt VM image when one is available. It usually saves time because the operating system is already configured for common virtualization tools.

Helpful official resources:

| Resource | Use It For | Link |
|----------|------------|------|
| Kali Linux Downloads | Kali installers, VM images, ARM images, and other official downloads | [Kali Downloads](https://www.kali.org/get-kali/) |
| Kali Virtual Machines | Prebuilt Kali VM images | [Kali Virtual Machines](https://www.kali.org/get-kali/#kali-virtual-machines) |
| Parrot OS Downloads | Official Parrot OS downloads, including Security Edition | [Parrot OS Downloads](https://parrotsec.org/download/) |
| VirtualBox | Free virtualization tool available on several platforms | [VirtualBox Downloads](https://www.virtualbox.org/wiki/Downloads) |
| VMware Workstation Pro | Desktop virtualization for Windows and Linux | [VMware Workstation Pro](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion) |
| UTM | Virtualization option commonly used on macOS, including Apple Silicon systems | [UTM](https://mac.getutm.app/) |
| QEMU | Lower-level emulator and virtualizer used directly or by other tools | [QEMU](https://www.qemu.org/) |

<!-- `warning` Download operating systems and virtualization tools from official sources. Unofficial VM images can contain unwanted changes, malware, or outdated software. -->

## Hardware Guidelines

Exact requirements depend on your machine and tools, but these are reasonable beginner targets:

| Resource | Comfortable Beginner Target |
|----------|-----------------------------|
| Memory | 8 GB system RAM minimum; 16 GB or more is better |
| VM memory | 2 GB to 4 GB for many beginner Linux VMs |
| Storage | At least 30 GB free for one VM; more if you keep multiple snapshots |
| CPU | Virtualization support enabled in BIOS or firmware when available |
| Network | NAT mode for most beginner labs |

If your computer is limited, use browser-based tools where possible and keep only one VM running at a time.

## VM Safety Habits

Build these habits early:

- Take a snapshot after the VM is installed and updated.
- Take another snapshot before major tool installs or risky experiments.
- Store lab files in a dedicated training folder.
- Be careful with shared folders between host and guest.
- Avoid saving personal passwords, browser sessions, or private keys inside a training VM.
- Do not run unknown binaries on your host machine.
- Keep the VM updated, but avoid upgrading everything in the middle of a challenge unless there is a reason.

Snapshots are useful because training environments break. Breaking a VM is normal. Being able to reset it is the point.

## Bare Metal, VM, WSL, Or Cloud?

Different environments have different tradeoffs.

| Environment | Best Use | Tradeoff |
|-------------|----------|----------|
| Virtual machine | Most beginner cybersecurity training | Uses more memory and storage |
| Bare metal install | Hardware-heavy work such as some wireless testing | More risk to your main system; harder to reset |
| WSL | Linux command-line practice on Windows | Not the same as a full Linux VM for all security tools |
| Cloud VM | Remote practice environments and hosted labs | Costs, account setup, and exposure risks need attention |
| Browser tools | Quick experiments and lightweight tasks | Not appropriate for sensitive files or every challenge type |

For beginner Layer Zero training, start with a VM unless a specific lab tells you otherwise.

## Core Tools To Have Early

You do not need every tool at once. Start with a small toolkit and add more when the challenge requires it.

| Tool | Category | Use It For |
|------|----------|------------|
| Browser developer tools | Web security | Inspecting requests, responses, storage, and page source |
| CyberChef | Crypto and data formats | Encoding, decoding, hashing, and transformation experiments |
| Python 3 | General problem solving | Small scripts, parsing, automation, and repeatable tests |
| Wireshark | Networking and forensics | Packet capture analysis |
| Burp Suite Community or OWASP ZAP | Web security | Intercepting and replaying authorized web requests |
| Ghidra or Dogbolt | Reverse engineering | Decompilation and static analysis |
| exiftool | Forensics and OSINT | Metadata inspection |
| Git | General workflow | Saving notes, scripts, and training artifacts |
| A notes app or Markdown editor | All categories | Recording evidence, commands, and conclusions |

<!-- `tip` Install tools when you need them. A smaller environment you understand is better than a large toolkit you cannot explain. -->

## Notes And Workspace Setup

Good notes make you better at solving challenges and asking for help.

Create a simple folder structure:

```text
training/
  notes/
  artifacts/
  scripts/
  screenshots/
```

For each challenge, record:

- Challenge name and category
- Date started
- Files or links provided
- What you observed
- What you tried
- What worked
- What failed
- Final explanation

Failed attempts are useful. They show what you ruled out and help someone else understand your thinking.

## Working With Online Tools

Online tools are convenient, especially for quick beginner practice. They are not always appropriate.

Good online-tool habits:

- Use them for public training challenge data.
- Avoid uploading real organizational files.
- Avoid uploading malware, private binaries, secrets, credentials, or incident artifacts.
- Prefer local tools when the file contents are sensitive.
- Keep notes about which tool changed or decoded the data.

This matters for reverse engineering, forensics, cryptography, and OSINT. If you are unsure whether a file is sensitive, treat it as sensitive.

## A Beginner Setup Checklist

- Install or choose a modern browser.
- Create a dedicated training folder.
- Choose a notes format.
- Install a virtualization tool.
- Download a Kali or Parrot OS VM from an official source.
- Boot the VM and confirm internet access.
- Update the VM when appropriate.
- Take a clean snapshot.
- Sign in to the [Layer Zero Lab](https://lab.layer-zero.org).
- Join or check the [Layer Zero Discord](https://discord.gg/ftmmWdnGmC) for updates and CTF information.

You can start practicing before every item is perfect. The checklist is there to reduce friction, not to delay learning.

## Questions To Ask Yourself

- Am I working in an environment I am allowed to use?
- Can I reset my setup if I break something?
- Am I keeping personal data separate from training data?
- Did I download tools from official sources?
- Do I understand what this tool is doing at a basic level?
- Is this file safe to upload to an online tool?
- Did I write down enough notes to repeat my process?

## Summary

Your first cybersecurity environment should be safe, understandable, and easy to reset.

Remember these key points:

- A VM is the best starting point for most beginners.
- Kali and Parrot OS are both valid training choices.
- Official downloads matter.
- Snapshots make experimentation safer.
- Online tools are useful, but not for sensitive files.
- Notes are part of the work, not an extra task.

Start with a simple setup, practice in the Layer Zero Lab, and improve your environment as your training needs become clearer.
