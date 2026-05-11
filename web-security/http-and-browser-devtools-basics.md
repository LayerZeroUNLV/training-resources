---
title: "HTTP And Browser DevTools Basics"
order: 2
category: "web-security"
description: "A beginner-friendly guide to HTTP requests, responses, browser developer tools, and web challenge observation."
author: "Layer Zero"
tags: ["web-security", "http", "devtools", "browser", "beginner"]
---

# HTTP And Browser DevTools Basics

Web challenges usually come down to understanding what the browser sends, what the server returns, and where the application makes trust decisions. Browser developer tools let you inspect that conversation without guessing.

This guide focuses on the basics: URLs, methods, status codes, headers, cookies, storage, and the browser Network tab.

<!-- `notes`
Practice this topic with web security challenges in the [Layer Zero Lab](https://lab.layer-zero.org).
Review [Beginner Web Security Foundations](https://www.layer-zero.org/training/web-security/beginner-web-security-foundations) if you need the broader context first.
Use DevTools to answer specific questions, not just to click around randomly.
-->

## Prerequisites

- Basic comfort using a web browser
- A training website or lab target you are authorized to inspect
- Willingness to take notes about requests and responses

## HTTP In One Minute

HTTP is a request and response protocol.

| Piece | Meaning |
|-------|---------|
| Request | What the browser asks the server for |
| Response | What the server sends back |
| Method | The action style, such as `GET` or `POST` |
| Path | The resource being requested, such as `/login` |
| Header | Metadata sent with a request or response |
| Body | Optional data sent with a request or response |
| Status code | Number that summarizes the response result |

Example request:

```http
GET /profile HTTP/1.1
Host: example.test
Cookie: session=abc123
```

Example response:

```http
HTTP/1.1 200 OK
Content-Type: text/html

<h1>Profile</h1>
```

## Common HTTP Methods

| Method | Common Use | Beginner Notes |
|--------|------------|----------------|
| `GET` | Read or request a resource | Parameters may appear in the URL |
| `POST` | Submit data | Often used for forms and JSON APIs |
| `PUT` | Replace or update data | Common in APIs |
| `PATCH` | Partially update data | Common in APIs |
| `DELETE` | Delete data | Should require authorization |
| `OPTIONS` | Ask what methods are supported | Sometimes useful for API discovery |

Methods are clues, not guarantees. The server decides what a request actually does.

## Common Status Codes

| Code | Meaning | What To Ask |
|------|---------|-------------|
| `200` | OK | Did the server return the expected content? |
| `301` or `302` | Redirect | Where did it send the browser? |
| `400` | Bad request | Did the input shape break something? |
| `401` | Unauthorized | Is authentication missing or invalid? |
| `403` | Forbidden | Is the user authenticated but not allowed? |
| `404` | Not found | Is the path wrong, hidden, or removed? |
| `500` | Server error | Did the application reveal useful error details? |

Status codes help you understand behavior, but read the response body too.

## URL Parts

Example:

```text
https://lab.example.test:443/search?q=test&page=2#results
```

| Part | Example |
|------|---------|
| Scheme | `https` |
| Host | `lab.example.test` |
| Port | `443` |
| Path | `/search` |
| Query string | `q=test&page=2` |
| Fragment | `#results` |

The fragment is handled by the browser and is usually not sent to the server.

## Browser DevTools Areas

Most modern browsers include developer tools. The names vary slightly, but the core ideas are similar.

| Area | Use It For |
|------|------------|
| Elements or Inspector | Viewing and editing the current page structure |
| Console | Seeing JavaScript errors and running small browser-side tests |
| Network | Inspecting requests and responses |
| Application or Storage | Viewing cookies, local storage, session storage, and cache |
| Sources | Reading loaded JavaScript and source files |

For web security beginners, the Network and Storage views are usually the most important.

## Network Tab Workflow

1. Open DevTools.
2. Go to the Network tab.
3. Enable "Preserve log" if you need to keep requests across redirects.
4. Perform one action in the application.
5. Click the relevant request.
6. Inspect method, path, status, headers, cookies, query parameters, and body.
7. Repeat with one changed input or account state.

Do not try to inspect every request at once. Pick the request tied to the action you performed.

## Cookies And Storage

Cookies and browser storage often matter in beginner challenges.

| Storage Type | Sent Automatically To Server? | Common Use |
|--------------|-------------------------------|------------|
| Cookie | Yes, when domain/path rules match | Sessions, preferences, tracking |
| Local storage | No | Browser-side app data |
| Session storage | No | Temporary browser-side app data |
| Cache | Sometimes indirectly | Saved copies of resources |

Important distinction: local storage is visible to the user but is not automatically sent with every request like cookies are.

<!-- `warning` Do not treat anything stored in the browser as secret from the user. Hidden client-side data can usually be inspected or modified. -->

## Comparing Requests

Comparison is one of the strongest beginner techniques.

Try comparing:

- Logged out versus logged in
- Normal user versus admin user
- Valid input versus invalid input
- Your user ID versus another user ID in an authorized lab
- A request before and after clicking a button

Ask:

- What changed?
- What stayed the same?
- Which value appears user-controlled?
- Which value does the server appear to trust?

## Common Beginner Findings

| Observation | Possible Meaning |
|-------------|------------------|
| A hidden form field controls price, role, or user ID | The server may be trusting client-side data |
| A cookie contains readable role data | The session or authorization model may be weak |
| JavaScript contains API paths | Client-side files may reveal routes to inspect |
| Different users can access similar numbered URLs | Possible authorization issue |
| Error response reveals stack trace or SQL text | Debug information may be exposed |

These are starting points. Verify behavior before calling something a vulnerability.

## Beginner Web Workflow

1. Use the feature normally.
2. Identify the request that matches your action.
3. Write down method, path, status code, and important parameters.
4. Change one input in the application.
5. Compare the new request and response.
6. Decide whether the server or the browser enforced the rule.
7. Verify with the smallest test that proves the behavior.

## Practice Prompts

Use these prompts in an authorized lab:

- Find the request sent when logging in.
- Identify one cookie and explain when it is sent.
- Find one JavaScript file loaded by the page.
- Change a form input and observe which request field changes.
- Compare a `401`, `403`, and `404` response if the lab provides them.

## Summary

Browser DevTools are a visibility tool. They help you see the web conversation instead of guessing.

Remember these key points:

- HTTP uses requests and responses.
- Methods and status codes are clues.
- Cookies are sent to the server; local storage is not automatically sent.
- The browser is not a security boundary.
- Compare requests to find what changed.
- Verify whether the server enforces the rule.

Use DevTools to make observations, then let those observations guide your next test.
