# Layer Zero Training Resources

Training documents in this repo are published on the Layer Zero website:

[https://www.layer-zero.org/training](https://www.layer-zero.org/training)

The site uses a custom Markdown renderer. For the full renderer reference, see [lz-markdown-guide.md](./lz-markdown-guide.md).

## Writing Goals

Layer Zero training docs should help learners build cybersecurity skill through practice and reasoning.

Good training docs should:

- Be beginner-friendly unless the title clearly says otherwise.
- Teach concepts and workflows, not only answers.
- Encourage learners to observe evidence, form hypotheses, and test one idea at a time.
- Point learners to hands-on practice in the [Layer Zero Lab](https://lab.layer-zero.org).
- Avoid becoming complete walkthroughs or answer keys unless the document is explicitly meant for facilitators.

## File Organization

Root-level Markdown files with front matter are treated as `getting-started` documents by the website. Use the root for orientation, setup, methodology, and broad resource pages.

```text
introduction.md
setting-up-your-environment.md
how-to-approach-ctf-challenges.md
tools-and-resources.md
```

Root-level training URLs use this shape:

```text
https://www.layer-zero.org/training/[slug]
```

Example:

```text
https://www.layer-zero.org/training/setting-up-your-environment
```

Place topic-specific training documents in a category folder:

```text
cryptography/beginner-cryptography-foundations.md
forensics/beginner-digital-forensics-foundations.md
web-security/beginner-web-security-foundations.md
```

Category training URLs use this shape:

```text
https://www.layer-zero.org/training/[category]/[slug]
```

Example:

```text
https://www.layer-zero.org/training/cryptography/beginner-cryptography-foundations
```

Use lowercase file names with hyphens. The file name without `.md` becomes the slug.

## Front Matter

Every training document should start with YAML front matter:

```yaml
---
title: "Article Title Here"
order: 1
category: "category-name"
description: "A brief description of what this article covers."
author: "Your Name"
tags: ["tag1", "tag2", "tag3"]
---
```

Optional featured document:

```yaml
---
title: "Introduction"
order: 1
featured: true
category: "getting-started"
description: "Start here for Layer Zero training."
author: "Layer Zero"
tags: ["introduction", "getting-started"]
---
```

Front matter notes:

- `title` is the display title.
- `description` appears in training listings and previews.
- `order` controls sorting inside a category. Lower numbers appear first. Missing values sort last.
- `featured: true` promotes a document to the training page's "Start Here" area. Only one document should use it.
- Root-level documents are automatically grouped as getting-started pages by the website.
- `category` can override the directory-derived category. Use it when an explicit override is needed.
- `tags` should be short, lowercase topic labels.

## Basic Document Template

````md
---
title: "Article Title Here"
order: 1
category: "category-name"
description: "A brief description of what this article covers."
author: "Your Name"
tags: ["tag1", "tag2", "tag3"]
---

# Article Title Here

Introduction paragraph explaining what this article covers and why it matters.

<!-- `notes`
Practice this topic in the [Layer Zero Lab](https://lab.layer-zero.org).
Use this page as a guide while you work, but let the challenge evidence drive your decisions.
-->

## Prerequisites

- Prerequisite 1
- Prerequisite 2

## Section One

Your content here. You can use **bold**, *italic*, and `inline code`.

```python
print("Hello, Layer Zero!")
```

## Section Two

You can use tables:

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data     | Data     | Data     |

## Summary

Wrap up the key takeaways here.
````

## Supported Markdown

The renderer supports GitHub Flavored Markdown, including:

- Headings
- Bold and italics
- Ordered and unordered lists
- Tables
- Blockquotes
- Inline code
- Strikethrough
- Task lists
- Autolinked URLs

Use fenced code blocks with a language name whenever possible:

````md
```bash
file challenge.bin
strings challenge.bin | head
```
````

Supported languages are whatever `react-syntax-highlighter` supports, including common values such as `bash`, `python`, `javascript`, `typescript`, `json`, `yaml`, `go`, and `rust`.

## Custom Callouts

The Layer Zero renderer turns specially formatted HTML comments into styled callout boxes.

The general format is:

```md
<!-- `type` Content goes here. -->
```

Supported single-line callout types:

```md
<!-- `note` Use this for neutral context. -->
<!-- `tip` Use this for helpful suggestions. -->
<!-- `info` Use this for extra background. -->
<!-- `warning` Use this for important caution. -->
<!-- `danger` Use this for high-risk actions or serious warnings. -->
```

Important callout rules:

- The callout type must be wrapped in backticks.
- Single-line callouts render plain text. Markdown links inside them are not parsed.
- Use `notes` when you need multiple lines, bullets, or inline Markdown links.

Example `notes` callout:

```md
<!-- `notes`
Practice this topic in the [Layer Zero Lab](https://lab.layer-zero.org).
Check the [Layer Zero Discord](https://discord.gg/ftmmWdnGmC) for CTF updates.
Use this document as a reference, not as a complete answer key.
-->
```

Recommended training-doc use:

- Use `notes` near the top of a document for lab and resource links.
- Use `warning` for safety cautions.
- Use `tip` for plain-text learning hints.
- Avoid overusing callouts. If everything is highlighted, nothing is.

## Multi-Language Code Tabs

The renderer supports tabbed code examples through a `code` comment block:

````md
<!-- `code`
```python
print("hello")
```

```bash
echo "hello"
```
-->
````

Use this when showing the same idea in multiple languages or tools. For most beginner training docs, normal fenced code blocks are simpler and easier to read.

## Links

Use normal Markdown links:

```md
[Layer Zero Lab](https://lab.layer-zero.org)
```

Training document links should use the public category and slug format:

```md
[Beginner Cryptography Foundations](https://www.layer-zero.org/training/cryptography/beginner-cryptography-foundations)
```

Section links can use normal anchors:

```md
[Jump to the summary](#summary)
```

## Content Guidance

Prefer this structure for beginner foundation docs:

- Short introduction
- Lab/resource callout
- Prerequisites
- Core concepts
- Common clues or patterns
- Beginner workflow
- Questions to ask yourself
- Tooling mindset
- Safe practice habits
- Practice prompts
- Summary

When writing cybersecurity content:

- Be clear about authorization and safe practice.
- Avoid encouraging activity against systems the learner does not own or have permission to test.
- Teach reasoning before tools.
- Include multiple possible approaches when useful.
- Keep examples small enough for beginners to inspect.
- Avoid presenting one command or tool as the only correct solution.

## Common Mistakes

- Missing front matter.
- Invalid YAML in front matter, especially unquoted colons.
- Forgetting `order`, which can make a document sort later than expected.
- Using `featured: true` on more than one document.
- Forgetting backticks in callout syntax, such as `<!-- note ... -->`.
- Putting Markdown links inside single-line callouts instead of using `notes`.
- Omitting the language from fenced code blocks.
