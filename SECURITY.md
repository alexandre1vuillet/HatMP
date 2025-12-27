# Security Policy

## Supported Versions

The following versions of this project are currently receiving security updates:

| Versions | Supported          |
|----------|--------------------|
| 1.x.x    | :white_check_mark: |


## Report a vulnerability

The security of our application is a top priority. If you discover a security vulnerability, we thank you for helping us protect our users.


### How to Report

**Please DO NOT report security vulnerabilities via public GitHub issues.**

Instead, please email: **[alexandre.vuillet1@orange.fr]**

Include it in your report:
- A detailed description of the vulnerability
- Steps to reproduce the issue
- Affected versions
- Potential impact
- Any suggestions for a fix, if you have any

### Expected Response

- **Acknowledgment of receipt**: within 48 hours
- **Initial assessment**: within 5 business days
- **Regular updates**: every 7 days until resolution
- **Resolution**: varies depending on severity (critical < 7 days, high < 30 days)

### Responsible Disclosure

We follow the coordinated disclosure principle:
1. You report the vulnerability privately
2. We work together on a fix
3. We release the fix
4. We then publish the details of the vulnerability

## Tauri Security Best Practices

### Tauri Configuration

Our Tauri application follows these security principles:

#### 1. Context Isolation
- The JavaScript context is isolated from the Rust backend
- Use of Tauri's secure IPC system
- No direct access to the file system from the frontend

### 3. CSP (Content Security Policy)
Our application uses a strict CSP defined in `tauri.conf.json`.

### Dependency

#### Frontend (HTML/CSS/JS)
- NPM dependencies are checked with `npm audit`
- Regular updates of dependencies
- No use of `eval()` or `innerHTML` with unsanitized content

#### Backend (Rust)
- Cargo dependencies are checked with `cargo audit`
- Strict semantic versions are used
- Security warnings are reviewed regularly

### Input Validation

All user input is:
- Validated on the frontend
- Re-validated on the Rust backend
- Escaped before display
- Limited in size and format

### Secure Storage

- Sensitive data uses the system keyring via `tauri-plugin-store`
- No storage of secrets in localStorage
- Encryption of sensitive local data

## Security Audit

We regularly perform:
- Static code analysis (Clippy for Rust, ESLint for JS)
- Dependency audits
- Manual security testing
- Code review for sensitive changes

## Security Updates

Security fixes are published:
- Via GitHub Releases
- With a detailed changelog
- Accompanied by a notification to users
- With an automatic Tauri update system

## Known vulnerabilities

### glib 0.18.5 - VariantStrIter Iterator Implementation

**Status**: Temporarily accepted
**CVE/Advisory**: Design issue in Iterator and DoubleEndedIterator
**Background**: Transitive dependency via Tauri 2.9.5 → gtk/webkit2gtk → glib 0.18.5

**Mitigation**:
- Our application code uses glib 0.20.12 (patched version)
- The vulnerability only affects GTK bindings on Linux
- Our application does not directly use `glib::VariantStrIter`

**Planned resolution:**
- Automatic update in the next major release of Tauri
- Weekly monitoring via Dependabot

**Last review:** December 27, 2025

## Resources

- [Tauri Security Best Practices](https://tauri.app/v1/guides/security/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Rust Security Guidelines](https://anssi-fr.github.io/rust-guide/)

*** Translated with www.DeepL.com/Translator (free version) ***

