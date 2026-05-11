---
title: "Beginner Networking Foundations"
order: 1
category: "networking"
description: "A beginner-friendly introduction to networking concepts, traffic analysis, and challenge-solving habits."
author: "Layer Zero"
tags: ["networking", "beginner", "ctf", "tcp-ip", "foundations"]
---

# Beginner Networking Foundations

Networking is how computers communicate. In cybersecurity training, networking challenges often ask you to understand traffic, identify services, inspect packets, or explain how data moved from one system to another.

This guide is a reference, not a complete solution path. A network challenge might be solved by reading a packet capture, checking a port, following a protocol, or comparing what should happen against what did happen.

<!-- `notes`
Practice this topic with networking challenges in the [Layer Zero Lab](https://lab.layer-zero.org).
Use this page as a guide while you work, but let the challenge evidence drive your decisions.
-->

## Prerequisites

- Basic comfort with IP addresses and URLs
- Basic command-line comfort
- Willingness to inspect details instead of guessing from tool output alone

## Core Networking Ideas

| Concept | What It Means | Example |
|---------|---------------|---------|
| IP address | A network address for a device or interface | `192.168.1.25` |
| Port | A numbered entry point for a service | `80`, `443`, `22` |
| Protocol | Rules for communication | HTTP, DNS, SSH |
| Packet | A small unit of network data | One piece of a connection |
| Client | The system starting a request | Browser connecting to a site |
| Server | The system responding to a request | Web server returning a page |

When investigating network behavior, ask: "Who talked to whom, over what protocol, and what data moved?"

## TCP, UDP, and ICMP

| Protocol | Common Use | Beginner Notes |
|----------|------------|----------------|
| TCP | Reliable connections | Used by HTTP, HTTPS, SSH, many application protocols |
| UDP | Lightweight messages | Used by DNS, streaming, some game and voice traffic |
| ICMP | Network control messages | Used by tools like `ping` |

TCP is connection-oriented. UDP is message-oriented. ICMP is often used for diagnostics.

## Common Ports

Port numbers can provide clues, but they are not proof by themselves.

| Port | Common Service |
|------|----------------|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 445 | SMB |
| 3306 | MySQL |
| 5432 | PostgreSQL |

A service can run on an unusual port, and an unusual service can run on a common port. Verify what is actually speaking.

## DNS Basics

DNS translates names into records that systems can use.

Common record types:

- `A`: IPv4 address
- `AAAA`: IPv6 address
- `CNAME`: Alias to another name
- `MX`: Mail server
- `TXT`: Text record, often used for verification or policy

Beginner challenge questions:

- What name is being resolved?
- What record type is being requested?
- Does the DNS response reveal a hidden host, subdomain, or clue?

## HTTP and TLS Basics

HTTP carries web requests and responses. HTTPS is HTTP protected by TLS.

Important HTTP details:

- Method, such as `GET` or `POST`
- Path, such as `/login`
- Headers, such as `Host` or `Cookie`
- Body, such as form or JSON data
- Status code, such as `200`, `302`, or `404`

TLS helps protect confidentiality and integrity in transit. Certificate details can also reveal names, issuers, and validity periods.

## Packet Capture Mindset

Packet captures, often called PCAPs, record network traffic for later inspection.

Useful things to look for:

- Conversations between hosts
- Protocols in use
- DNS lookups
- HTTP requests and responses
- Files transferred over cleartext protocols
- Repeated failed connections
- Unusual ports or destinations

Packet captures can be noisy. Start with broad questions, then narrow down.

## A Beginner Networking Challenge Workflow

1. Identify the artifact.
   Are you given a host, a port, a log, a PCAP, or a command output?

2. List known facts.
   Write down IP addresses, ports, protocols, timestamps, and names.

3. Follow conversations.
   Group traffic by client, server, and protocol.

4. Check assumptions.
   Do not assume port `80` means normal web traffic or that encrypted traffic has no useful metadata.

5. Inspect the data safely.
   Look for readable content, headers, errors, and repeated patterns.

6. Explain the path.
   A good solution should describe how the data moved and why the evidence supports your conclusion.

## Questions To Ask Yourself

- What systems are communicating?
- Which side started the connection?
- What protocol appears to be in use?
- Is the data readable, encoded, compressed, or encrypted?
- Are there DNS requests that explain later connections?
- Are there failed attempts before a successful action?
- What evidence would I expect if my theory is correct?

## Tooling Mindset

Helpful tools include:

- Wireshark for packet capture analysis
- tcpdump for command-line packet inspection
- dig or nslookup for DNS queries
- curl for HTTP testing
- nc for basic authorized service interaction
- nmap for authorized service discovery

Tool output is evidence, not a conclusion. Read the details and confirm what they mean.

## Safe Practice Habits

- Scan or connect only to systems you are authorized to test.
- Be careful with automated tools on shared networks.
- Save original PCAPs before exporting or filtering data.
- Avoid submitting sensitive real traffic to online analysis services.
- Document commands and filters so your work can be repeated.

## Practice Prompts

Use these prompts while working through beginner networking challenges:

- Identify every unique IP address in the artifact.
- Find one DNS query and explain what happened after it.
- Follow one TCP stream and summarize the conversation.
- Identify one service by evidence other than the port number.
- Explain whether traffic content is readable, encoded, compressed, or encrypted.

## Summary

Networking challenges are about communication evidence. Focus on hosts, ports, protocols, timing, and payloads.

Remember these key points:

- Ports are clues, not proof.
- DNS often explains where later traffic goes.
- Packet captures are easier when you follow one conversation at a time.
- Encrypted traffic may still reveal useful metadata.
- There is often more than one valid route to the same finding.

Use this guide to orient yourself, then let the traffic tell the story.
