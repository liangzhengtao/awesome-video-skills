# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please report it responsibly.

### How to Report

1. **Do NOT open a public issue** for security vulnerabilities.
2. Email your findings to the maintainers (see the repository for contact info).
3. Include a detailed description of the vulnerability.
4. Include steps to reproduce if applicable.

### What to Expect

- **Acknowledgment** within 48 hours.
- **Status update** within 7 days.
- **Resolution** as soon as possible, depending on complexity.

## Scope

This project contains markdown skill files and configuration. While the files themselves are not executable software, we take security seriously:

- **No secrets**: Skill files must never contain API keys, passwords, tokens, or credentials.
- **No malicious content**: All code examples must be safe, educational, and clearly documented.
- **No external data collection**: Skills should not direct AI assistants to send data to unauthorized third parties.
- **Dependency safety**: Any referenced tools or packages should be well-known, actively maintained, and from trusted sources.

## Safe Code Examples

When contributing scripts or code examples:

- Use placeholder values (e.g., `YOUR_API_KEY`, `your-email@example.com`)
- Clearly document what credentials or configuration the user needs to provide
- Warn about destructive operations (file deletion, format conversion, etc.)
- Prefer read-only or reversible operations in examples

## Acknowledgments

We thank all security researchers who responsibly disclose vulnerabilities.
