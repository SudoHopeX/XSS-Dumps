# XSS-Dumps

A specialized collection of wordlists for **Cross-Site Scripting (XSS)** vulnerability testing, security research, and payload generation.


## 🎯 Purpose

This repository provides highly targeted wordlists for security professionals, penetration testers, and bug bounty hunters focusing on XSS vulnerabilities. The lists are designed to assist in **fuzzing** web applications and identifying potential injection points by systematically testing common HTML tags and event handlers that developers often forget to filter.


## 📂 Content

This repository currently contains two essential wordlists for crafting XSS payloads:

| File Name | Description | Use Case |
| :--- | :--- | :--- |
| **`html-tags.txt`** | A comprehensive list of almost all standard and common **HTML tags**. | Testing which tags (e.g., `<script>`, `<img>`, `<svg>`) are allowed or blocked by an application's input sanitization filters. |
| **`html-event-handlers.txt`** | A list of virtually all possible **HTML event handlers**. | Crucial for discovering event-based XSS vectors (e.g., `onload`, `onerror`, `onfocus`) after a tag has been successfully injected. |


## 💡 Usage

You can easily integrate these wordlists into your security toolset by cloning the repository:

```bash
git clone https://github.com/SudoHopeX/XSS-Dumps.git
```

## Examples for Testing
1. **Fuzzing for Allowed Tags:** Use a tool like Burp Suite Intruder or a custom script with the `html-tags.txt` list to insert various tags into an input field (e.g., a username or search parameter) to see which ones are reflected in the HTML source code.

2. **Testing Event Handler Bypasses:** Once you've identified a reflected or allowed tag (e.g., `<svg>`), use the `html-event-handlers.txt` list to systematically test every possible event handler as an attribute to trigger the payload:
```html
<svg/$EVENT_HANDLER$=alert(1)>
```
Where `$EVENT_HANDLER$` is replaced by entries from the wordlist (e.g., `onload`, `onerror`).

## 🤝 Contribution
Contributions are highly welcome! If you find any missing tags, event handlers, or have other XSS-related wordlists that you believe should be included, please open a Pull Request or submit an Issue.
