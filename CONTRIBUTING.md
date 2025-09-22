# Contributing to DigitalMeve

First off, thank you for considering contributing to **DigitalMeve** — the global standard for invisible proof inside any file.  
Your time and expertise help us push this standard forward and build trust worldwide.

We aim for a welcoming, transparent, and professional environment.  
This document explains how you can contribute effectively.

---

## 📖 Table of Contents
1. [Code of Conduct](#code-of-conduct)
2. [Types of Contributions](#types-of-contributions)
3. [Getting Started](#getting-started)
4. [Development Workflow](#development-workflow)
5. [Architecture Decision Records (ADRs)](#architecture-decision-records-adrs)
6. [Pull Request Process](#pull-request-process)
7. [Issue Reporting](#issue-reporting)
8. [Style Guides](#style-guides)
9. [Security and Responsible Disclosure](#security-and-responsible-disclosure)
10. [Community and Support](#community-and-support)

---

## 1. Code of Conduct
Participation in this project requires adherence to our [Code of Conduct](CODE_OF_CONDUCT.md).  
We expect all contributors to foster a respectful, professional, and inclusive environment.

---

## 2. Types of Contributions
We welcome many forms of contributions:

- **Bug reports** → Help us improve reliability.
- **Feature requests** → Suggest enhancements aligned with the standard.
- **Documentation** → Improve clarity, add diagrams, examples, or translations.
- **Implementations** → Reference code in various languages (not official but helpful).
- **Security reviews** → Report vulnerabilities responsibly.
- **Community support** → Answer questions, share knowledge, spread adoption.

---

## 3. Getting Started
- Fork the repository and clone your fork locally.
- Install dependencies (if any) as described in `README.md`.
- Familiarize yourself with the [STANDARD.md](STANDARD.md) and [ARCHITECTURE.md](ARCHITECTURE.md).
- All contributions should align with the philosophy of **privacy-first, interoperability, and open standardization**.

---

## 4. Development Workflow
1. **Branching**
   - Create a feature branch:  
     `git checkout -b feature/my-new-feature`
   - Use descriptive names (e.g., `fix/sha256-validation`, `docs/add-pricing`).

2. **Commits**
   - Write clear, atomic commits.
   - Follow the [Conventional Commits](https://www.conventionalcommits.org/) spec (e.g., `feat: add DNS binding support`).

3. **Tests**
   - Provide tests or examples whenever relevant.
   - Ensure nothing sensitive (like private keys) is committed.

4. **Linting & CI**
   - Code should pass linting rules.
   - PRs must pass automated checks before merging.

---

## 5. Architecture Decision Records (ADRs)
All significant technical or governance decisions must be documented as **ADRs** under `/ADRs`.

- Use the template: `ADR-0001-template.md`
- Include: context, decision, rationale, alternatives considered, consequences.
- Every PR that changes the standard requires at least one ADR entry.

---

## 6. Pull Request Process
- Ensure PRs are **focused and minimal**. One feature/fix per PR.
- Reference the related issue (e.g., `Closes #42`).
- Update documentation (README, STANDARD, FAQ, etc.) if needed.
- PRs require at least **one approval** from a maintainer before merging.
- Security-related changes require a **mandatory audit**.

---

## 7. Issue Reporting
When reporting an issue:

- Use the provided issue templates (`bug_report.md`, `spec_change_request.md`).
- Provide a clear title and detailed description.
- Include steps to reproduce (for bugs).
- Suggest potential solutions if possible.
- Avoid disclosing vulnerabilities publicly — see [Security](#security-and-responsible-disclosure).

---

## 8. Style Guides
- **Documentation** → Use clear, professional English. Prefer Markdown with headings, lists, and code blocks.
- **Diagrams** → Place in `/diagrams` (SVG or PNG, no proprietary formats).
- **Examples** → Place in `/examples` with descriptive filenames.
- **Commit messages** → Use imperative mood (“add feature”, not “added feature”).
- **Code style** → Follow language-specific best practices.

---

## 9. Security and Responsible Disclosure
If you discover a vulnerability:

1. **Do not open a public issue.**
2. Report privately via [SECURITY.md](SECURITY.md).
3. Provide as much detail as possible for reproduction.
4. We will acknowledge receipt within **48h** and aim to provide a fix or mitigation timeline.

We value security researchers and will credit contributions where appropriate.

---

## 10. Community and Support
- **Discussions**: Use GitHub Discussions for Q&A and proposals.
- **Meetings**: Occasional community calls will be announced via Issues.
- **Contact**: For general inquiries, email [support@digitalmeve.org](mailto:support@digitalmeve.org).

---

## ✅ Summary
Contributing to DigitalMeve means:
- Respecting the Code of Conduct.
- Writing clear, tested, and documented changes.
- Following ADR and PR processes for transparency.
- Always putting **security and trust** first.

Thank you for helping shape **DigitalMeve — the invisible proof standard**.
