# Contributing to DSCI 522 Palmer Penguin Analysis

Thank you for your interest in contributing to our project! Whether you are reporting a bug, proposing an analytical improvement, or submitting code and documentation updates, please follow the guidelines below so we can maintain a reproducible and collaborative workflow.

## How to Report a Bug or Suggest a Change
1. Check existing issues: Before opening a new issue, search the [Issues](https://github.com/UBC-MDS-2026-27/DSCI-522-Palmer-Penguin-Analysis/issues) tab to ensure the bug or suggestion has not already been reported.
2. Open a GitHub Issue: Click New issue and provide a clear, descriptive title.
   - For bug reports: Include steps to reproduce the issue, the expected behavior, the actual behavior (including full error tracebacks), and your operating system and Python/environment details.
   - For feature or analysis suggestions: Explain what change you are proposing, why it improves the project, and how it fits into the existing workflow.

## How to Submit a Pull Request
We follow a standard GitHub Flow branching model. Please do not push commits directly to the `main` branch.

1. Create a feature branch: From an up-to-date `main` branch inside this repository, create a small, focused branch with a descriptive name (for example, `fix-data-cleaning-bug` or `add-eda-visualization`).
2. Make your changes: Keep each branch scoped to one independent piece of work. Follow the project's existing directory structure, formatting conventions, and plain-English reporting standards (avoiding code-style variable names in narrative text).
3. Verify reproducibility: Ensure that all scripts and Quarto documents render cleanly from top to bottom without errors in the project's virtual environment, and verify that temporary files (such as `.DS_Store` or `.venv/`) are not staged.
4. Open a Pull Request (PR): Push your branch to GitHub and open a PR targeting `main`. Reference the relevant GitHub Issue in your PR description (e.g., `Closes #12`) and summarize what changed and why.
5. Peer Review: Request a review from at least one teammate. Every pull request must be reviewed and approved by a human team member before merging.

## Generative AI Policy
Contributors may use generative AI tools (such as ChatGPT, Claude, or GitHub Copilot) to assist with brainstorming, debugging error messages, drafting boilerplate configuration, or checking grammar, subject to the following rules:

- Allowed Uses & Disclosure: If generative AI tools were used to generate or substantially revise code or prose in a contribution, you must disclose which tool was used and how it was applied in your Pull Request description.
- Contributor Responsibility: Every contributor is fully responsible for verifying, testing, and understanding all code, statistical reasoning, and text they submit, regardless of whether an AI assistant helped draft it. Fabricated references or unverified claims are strictly prohibited.
- Human Ownership of Workflow: All GitHub Issues and Pull Requests must be opened, reviewed, and merged by human contributors—never autonomously by an AI agent or bot. While AI tools may be used as a secondary check on code quality, human reviewers make all final review and merge decisions.

## Attribution
The structure and contribution workflow guidelines in this document were adapted from the [Altair Contributing Guide](https://github.com/vega/altair/blob/main/CONTRIBUTING.md) and the [earthaccess Generative AI Policy](https://github.com/nsidc/earthaccess/blob/main/CONTRIBUTING.md), as referenced in the UBC Master of Data Science DSCI 522 course guidelines.