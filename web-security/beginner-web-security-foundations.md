---
title: "Beginner Web Security Foundations"
order: 1
category: "web-security"
description: "A beginner-friendly introduction to web security concepts, request analysis, and challenge-solving habits."
author: "Layer Zero"
tags: ["web-security", "beginner", "ctf", "http", "foundations"]
---

# Beginner Web Security Foundations

Web security is the practice of finding, understanding, and fixing weaknesses in websites and web applications. Beginner web challenges often ask you to inspect how a site behaves, notice where trust is misplaced, and explain why a certain action should or should not be allowed.

This guide is a reference, not a complete answer key. Web challenges can often be solved by reading page source, watching network traffic, changing a request, comparing user roles, or following clues in the application. Your job is to observe carefully and test one idea at a time.

<!-- `notes`
Practice this topic with web security challenges in the [Layer Zero Lab](https://lab.layer-zero.org).
Use this page as a guide while you work, but let the challenge evidence drive your decisions.
-->

## Prerequisites

- Basic comfort using a web browser
- Basic understanding of URLs, websites, and forms
- Willingness to take notes about what you clicked, changed, and observed

## How Web Applications Communicate

Most web applications use a request and response pattern.

| Piece | What It Means | Example |
|-------|---------------|---------|
| Client | The browser or tool making a request | Firefox, Chrome, curl |
| Server | The system responding to the request | A web application backend |
| Request | What the client asks for | `GET /profile` |
| Response | What the server sends back | HTML, JSON, redirects, errors |
| Cookie | Small data stored by the browser and sent with requests | Session identifier |
| Header | Extra request or response metadata | `Content-Type`, `User-Agent` |

A useful beginner habit is to ask: "What did my browser send, and what did the server trust?"

## Common Places To Inspect

Start with what the application gives you directly.

- Page text and visible links
- HTML source
- JavaScript files
- Network requests in browser developer tools
- Cookies and local storage
- URL paths and query parameters
- Error messages
- Differences between accounts or roles

Do not assume hidden means secure. A value hidden in HTML, JavaScript, or a browser storage area can still be visible to the user.

## Beginner Web Security Topics

### Authentication

Authentication answers the question: "Who are you?"

Examples:

- Logging in with a username and password
- Using a session cookie after login
- Resetting a password

Beginner challenge questions:

- Is the login state stored safely?
- Can the session value be guessed or modified?
- Does the application reveal too much in an error message?

### Authorization

Authorization answers the question: "What are you allowed to do?"

An application may know who you are but still fail to check whether you should access a page, file, or action.

Beginner challenge questions:

- What changes when you use a normal user account instead of an admin account?
- Can one user access another user's data by changing an ID?
- Does the server check permissions, or does only the browser hide buttons?

### Input Handling

Web applications receive input from users, URLs, forms, headers, cookies, and uploaded files. If the server trusts input too much, bugs can appear.

Examples of risky input areas:

- Search boxes
- Login forms
- Profile fields
- File names
- URL parameters
- JSON request bodies

Beginner challenge questions:

- What type of input does the application expect?
- What happens with empty, long, unusual, or unexpected input?
- Does the application show errors that reveal how it works?

### Injection

Injection happens when user input is treated as part of a command, query, or code structure.

Common examples:

- SQL injection
- Command injection
- Template injection

At a beginner level, focus on the idea: data should be treated as data. If user input changes the structure of what the server runs, that is a serious warning sign.

### Cross-Site Scripting

Cross-site scripting, often called XSS, happens when a site displays user-controlled content as executable JavaScript in another user's browser.

Beginner challenge questions:

- Where does user input appear back on the page?
- Is the input treated as text, HTML, or script?
- Does the application encode special characters safely?

### Sensitive Information Exposure

Applications sometimes leak information through comments, debug pages, backups, logs, or client-side files.

Beginner challenge questions:

- Are there comments in the HTML source?
- Are JavaScript files exposing endpoints, keys, or hints?
- Are error messages revealing file paths or stack traces?
- Are backup files or old routes still reachable?

## A Beginner Web Challenge Workflow

1. Use the application normally.
   Understand what the feature is supposed to do before testing edge cases.

2. Map the important requests.
   Watch the browser network tab and write down key paths, methods, parameters, and response codes.

3. Compare behavior.
   Try different accounts, roles, inputs, or request values and note what changes.

4. Change one thing at a time.
   If you change a cookie, URL, and form field at the same time, you may not know what mattered.

5. Look for server-side trust mistakes.
   Ask whether the server is checking the rule or whether the browser is only making the rule look enforced.

6. Verify the result.
   A useful finding should explain what changed, why it mattered, and how the application responded.

## Questions To Ask Yourself

- What feature am I testing?
- What data does the browser send to the server?
- Which values look user-controlled?
- What does the server appear to trust?
- Is this an authentication problem, an authorization problem, or an input-handling problem?
- What evidence would prove my theory wrong?
- Can I reproduce the behavior with a clean, minimal request?

## Tooling Mindset

Helpful tools include:

- Browser developer tools for source, storage, and network traffic
- Burp Suite or OWASP ZAP for intercepting and replaying requests in authorized labs
- curl for simple HTTP requests
- A text editor for notes and request comparisons

Tools should make your observations clearer. Before using a tool, decide what question you want it to answer.

## Safe Practice Habits

- Test only systems you are authorized to test.
- Keep notes about requests you modify.
- Avoid using real passwords, tokens, or sensitive organizational data in training exercises.
- Do not run automated scanners against systems unless you have permission and understand the impact.
- Prefer explaining the weakness over only getting the flag.

## Practice Prompts

Use these prompts while working through beginner web challenges:

- Find one request that changes application state.
- Identify one value controlled by the browser.
- Compare the same page while logged in and logged out.
- Find one piece of information visible in page source but not visible on the rendered page.
- Explain whether a bug is caused by missing authentication, missing authorization, or unsafe input handling.

## Summary

Web security starts with careful observation. Learn what the browser sends, what the server returns, and where trust decisions happen.

Remember these key points:

- The browser is not a security boundary.
- Hidden client-side values may still be visible or changeable.
- Authentication and authorization are different.
- Input should be handled as data, not trusted as structure or code.
- Many web challenges can be solved through more than one path.

Use this guide as a starting point, then let each application show you what to investigate next.
