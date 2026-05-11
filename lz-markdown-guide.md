# Layer Zero Markdown Guide

This guide covers the markdown features supported by the Layer Zero site's custom renderer (`src/app/_components/shared/markdown.tsx`). Use it when authoring:

- Training documents in the `LayerZeroUNLV/training-resources` GitHub repo
- Internal API docs in `apps/layer-zero-site/src/app/docs/_content/`
- The `privacy` and `terms` pages

Everything in this guide works in all three contexts.

## Table of Contents

- [Standard Markdown](#standard-markdown)
- [Code Blocks](#code-blocks)
- [Custom Callouts](#custom-callouts)
  - [Note (blue)](#note-blue)
  - [Warning (yellow)](#warning-yellow)
  - [Danger (red)](#danger-red)
  - [Tip (green)](#tip-green)
  - [Info (cyan)](#info-cyan)
  - [Notes — multi-line (purple)](#notes--multi-line-purple)
- [Multi-Language Code Tabs](#multi-language-code-tabs)
- [Links and Section Anchors](#links-and-section-anchors)
- [Training-Specific Frontmatter](#training-specific-frontmatter)
- [How the Custom Syntax Works](#how-the-custom-syntax-works)
- [Common Mistakes](#common-mistakes)

## Standard Markdown

The renderer supports everything in [GitHub Flavored Markdown](https://github.github.com/gfm/) via `remark-gfm`. That includes:

- Headings (`#`, `##`, `###`)
- Bold (`**bold**`) and italics (`*italic*`)
- Ordered and unordered lists
- Tables (with header row separator)
- Blockquotes (`>`)
- Inline code (`` `like this` ``)
- Strikethrough (`~~struck~~`)
- Task lists (`- [ ]` and `- [x]`)
- Autolinked URLs

All of these get Layer Zero–themed styling automatically (dark background, monospaced body text, ternary-cyan accents on links and `docs`-mode headings).

## Code Blocks

Fenced code blocks render inside a `DocsCodeBlock` with syntax highlighting and a copy button. Always specify a language:

````markdown
```typescript
const greeting: string = "hello";
```
````

Supported languages are whatever [`react-syntax-highlighter`](https://github.com/react-syntax-highlighter/react-syntax-highlighter) accepts (`typescript`, `tsx`, `python`, `go`, `bash`, `json`, `yaml`, `rust`, etc.).

The block's title defaults to the language name. To run a fenced block as plain inline code without the heavy wrapper, just use a single backtick: `` `inline` ``.

## Custom Callouts

The renderer recognizes specially-formatted HTML comments and turns them into colored callout boxes. The general shape is:

```markdown
<!-- `<type>` Your content here. -->
```

The opening `` `<type>` `` (a backtick-wrapped keyword) is required. Without it, the comment is treated as a regular HTML comment and is not rendered.

### Note (blue)

```markdown
<!-- `note` Discord OAuth is the only supported login method. -->
```

Renders a blue panel with a 📝 NOTE header.

### Warning (yellow)

```markdown
<!-- `warning` Rotating AUTH_SECRET logs every user out immediately. -->
```

Renders a yellow panel with a ⚠️ WARNING header.

### Danger (red)

```markdown
<!-- `danger` Do not run `db:push` against production. It bypasses migration history. -->
```

Renders a red panel with a 🚨 DANGER header.

### Tip (green)

```markdown
<!-- `tip` Use `pnpm db:studio` to browse the database visually. -->
```

Renders a green panel with a 💡 TIP header.

### Info (cyan)

```markdown
<!-- `info` This endpoint is rate limited to 200 requests per minute on the `standard` tier. -->
```

Renders a cyan panel with an ℹ️ INFO header.

### Notes — multi-line (purple)

The `notes` type is special: each non-empty line of the comment becomes its own bullet, and each bullet is rendered with inline markdown (bold, italics, inline code, and links).

```markdown
<!-- `notes`
Bullets support **bold**, *italics*, and `inline code`.
Each line in the comment becomes its own bullet.
External links work: [Next.js docs](https://nextjs.org).
-->
```

Use `notes` for grouped reminders. Use plain `note` for a single line of prose.

## Multi-Language Code Tabs

To show the same example in multiple languages with tabs, use the `code` comment type and put fenced blocks inside the comment:

````markdown
<!-- `code`
```typescript
const user = await fetch("/api/v1/users/me", {
  headers: { Authorization: `Bearer ${apiKey}` },
}).then((r) => r.json());
```

```python
import requests
user = requests.get(
    "/api/v1/users/me",
    headers={"Authorization": f"Bearer {api_key}"},
).json()
```

```bash
curl -H "Authorization: Bearer $API_KEY" https://www.layer-zero.org/api/v1/users/me
```
-->
````

The plugin extracts each `` ```<lang> ... ``` `` block inside the comment and renders them in a `DocsMultiCodeBlock` with one tab per language. This is the pattern used throughout `src/app/docs/_content/` for REST API examples.

## Links and Section Anchors

Plain external links open in a new tab by default:

```markdown
[Next.js documentation](https://nextjs.org/docs)
```

Inside the in-app `/docs` page, the renderer supports an `onNavigate` callback. If a link's `href` is `#section-id` or `/docs#section-id`, clicking it scrolls to the section instead of triggering a full navigation. You do not have to configure this — it works automatically when the docs page passes `onNavigate` to the renderer. Just write the link normally:

```markdown
See the [auth section](#authentication) for details.
```

External links from inside a doc still open in a new tab.

## Training-Specific Frontmatter

Training docs (`LayerZeroUNLV/training-resources` repo) support extra YAML frontmatter parsed by `src/lib/github/training.ts`:

```yaml
---
title: Introduction to Layer Zero
description: Quick start for new members.
category: getting-started
author: Austin
tags: [orientation, onboarding]
order: 1            # Lower numbers sort first inside a category.
featured: true      # Pins this doc to the "Start Here" hero on /training.
---
```

- `order` controls the sort within a category. Lower runs first; missing values sort last.
- `featured: true` promotes the doc to the "Start Here" panel on the listing page. Only one should have it; the first match wins. If no doc has `featured: true`, the listing falls back to `getting-started/introduction`.
- `category` overrides the directory-derived category. Generally let the directory name win and omit this field.

The category named `getting-started` is always pinned to the top of the `/training` listing regardless of alphabetical order, so new contributors hit it first.

## How the Custom Syntax Works

Two pieces collaborate:

1. **`src/lib/remarkCommentPlugin.ts`** — a `remark` plugin that walks the markdown AST, finds `<!-- ... -->` comment nodes, and (if they start with a backtick-quoted type) replaces them with a `div` carrying `data-comment-type` and `data-comment-data` attributes. The plugin handles three special parse paths:
   - `` `code` `` — extracts fenced code blocks from inside the comment into a `languages` array.
   - `` `notes` `` — splits remaining content by line into a `lines` array.
   - everything else — packs remaining content into a `content` string.

2. **`src/app/_components/shared/markdown.tsx`** — the `MarkdownRenderer` intercepts those `div`s in `react-markdown`'s `components.div` override and dispatches to a typed component in the `CommentComponents` map (`note`, `notes`, `warning`, `danger`, `tip`, `info`, `code`, plus a `badge` slot that is not currently wired up to a comment syntax).

If you want to add a new callout type:

1. Add a parse branch to `remarkCommentPlugin.ts` if the data shape is non-trivial (otherwise the default `{ content }` branch works).
2. Add a component to `CommentComponents` in `markdown.tsx`.
3. Use it in markdown as `<!-- \`yourtype\` ... -->`.

## Common Mistakes

- **Forgetting the backticks around the type.** `<!-- note This won't render. -->` is a regular HTML comment and is dropped. The opening `` `note` `` is mandatory.
- **Mixing fenced blocks inside non-`code` comments.** Only `` `code` `` parses inner fenced blocks. Inside `` `note` ``, `` `tip` ``, etc., backticks are rendered as literal characters in the content string.
- **Multi-line callouts other than `notes`.** Only `notes` splits on newlines. The other callouts join the entire comment body into a single paragraph. If you need multi-line prose, use `notes` or stack multiple single-line callouts.
- **HTML inside callouts.** The callout body is rendered as a plain React `<p>` (or `<span>` inside `notes`); raw HTML inside is not parsed. Stick to plain text, except inside `notes` where bold/italic/inline-code/links work.
- **Frontmatter typos.** Training docs require valid YAML. An unquoted colon or wrong indent will silently fall back to defaults (title becomes the file path, tags become empty).
