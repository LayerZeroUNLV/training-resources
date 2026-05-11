---
title: "Beginner OSINT Foundations"
order: 1
category: "osint"
description: "A beginner-friendly introduction to open-source intelligence concepts, source evaluation, and research habits."
author: "Layer Zero"
tags: ["osint", "beginner", "research", "ctf", "foundations"]
---

# Beginner OSINT Foundations

Open-source intelligence, or OSINT, is the practice of collecting and analyzing information from publicly available sources. In cybersecurity training, OSINT challenges often ask you to connect clues, verify sources, and explain how you reached a conclusion.

This guide is a reference, not a search recipe that works every time. OSINT problems can be solved through search engines, archived pages, metadata, maps, public records, social platforms, source comparison, or careful reading. The strongest solutions explain why the evidence is reliable.

> Practice this topic with OSINT challenges in the [Layer Zero Lab](https://lab.layer-zero.org). Use this page as a guide while you work, but let the challenge evidence drive your decisions.

## Prerequisites

- Basic web search comfort
- Willingness to verify information across sources
- Patience for note-taking and source tracking

## What Counts As Open Source

Open source means publicly available, not secret or unauthorized.

Examples:

- Public websites
- News articles
- Public social media posts
- Domain registration data
- Certificate transparency records
- Public code repositories
- Maps and satellite imagery
- Archived web pages
- Public documents and metadata

Public availability does not remove ethical responsibility. Stay within legal and organizational boundaries.

## Evidence Quality

Not all sources are equally reliable.

| Source Type | Strengths | Risks |
|-------------|-----------|------|
| Official website | Often authoritative for its own organization | May be outdated or incomplete |
| News article | Useful context and dates | May contain errors or summaries |
| Social post | Timely and direct | Easy to delete, fake, or misinterpret |
| Archive | Shows past versions | May not capture every page or asset |
| Metadata | Can reveal useful details | Can be stripped, edited, or misleading |

Beginner habit: record where information came from, when you accessed it, and what claim it supports.

## Search Strategy

Good OSINT work is more than typing the first phrase that comes to mind.

Useful search ideas:

- Search exact phrases in quotes.
- Search unique usernames, emails, or filenames.
- Search by image when visual clues matter.
- Search related names, old names, or abbreviations.
- Search within a specific site when appropriate.
- Compare current pages with archived versions.

If a search fails, change the question. Search for a unique clue, a broader context, or a related artifact.

## Common OSINT Clue Types

### Usernames and Handles

Usernames may appear across platforms, but do not assume every matching username belongs to the same person.

Questions:

- Is the username unique?
- Does the profile share matching details?
- Are dates, locations, or writing style consistent?
- Could this be a different person using the same handle?

### Domains and Infrastructure

Domains can reveal relationships between websites, organizations, and services.

Questions:

- What DNS records exist?
- Are there subdomains?
- Are certificates associated with related names?
- Has the site changed over time?

### Images

Images may contain visual clues and metadata.

Questions:

- Are there landmarks, signs, shadows, language, or weather clues?
- Does reverse image search find an earlier source?
- Does metadata exist?
- Could the image be cropped, edited, or reused?

### Documents

Documents can contain visible text and hidden metadata.

Questions:

- Who is listed as author?
- When was it created or modified?
- What software produced it?
- Are there comments, tracked changes, or embedded links?

## A Beginner OSINT Challenge Workflow

1. Write down the exact question.
   Know what you are trying to prove before collecting sources.

2. Extract clues.
   List names, dates, locations, handles, domains, images, phrases, and file names.

3. Search from unique to broad.
   Start with the clue most likely to identify the target, then widen if needed.

4. Verify with independent evidence.
   Avoid relying on one weak source when another source can confirm it.

5. Track sources.
   Save links, timestamps, screenshots when appropriate, and short notes.

6. Explain confidence.
   A good OSINT answer explains both the conclusion and why the evidence supports it.

## Questions To Ask Yourself

- What exact claim am I trying to prove?
- Which clue is most unique?
- Is this source primary, secondary, or copied from somewhere else?
- Could there be another explanation?
- Can I verify this from an independent source?
- What date does this evidence support?
- Am I staying within authorized and ethical boundaries?

## Tooling Mindset

Helpful tools include:

- Search engines
- Web archives
- Reverse image search
- Map and street-view tools
- DNS lookup tools
- Certificate transparency search
- Metadata tools
- Notes with source links and timestamps

Tools help collect evidence, but they do not decide truth. Your reasoning connects the sources.

## Safe Practice Habits

- Use only public and authorized sources.
- Do not attempt to access private accounts, private systems, or restricted data.
- Avoid contacting real people as part of training challenges unless the exercise explicitly authorizes it.
- Be careful with personal information and privacy.
- Separate facts, assumptions, and conclusions in your notes.

## Practice Prompts

Use these prompts while working through beginner OSINT challenges:

- Identify the most unique clue in a prompt.
- Find two independent sources that support the same fact.
- Compare a current web page with an archived version.
- Explain why a matching username is or is not enough evidence.
- Record a source link, access date, and the claim it supports.

## Summary

OSINT is structured research. The skill is not just finding information, but verifying it and explaining why it matters.

Remember these key points:

- Public information still requires ethical handling.
- Exact claims make research easier.
- One source is often not enough.
- Matching names or usernames are clues, not proof.
- Strong OSINT answers show the path from evidence to conclusion.

Use this guide to organize your research, then let source quality guide your confidence.
