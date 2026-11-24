# Contributing to DSCI 522 Palmer Penguin Analysis

Thank you for your interest in contributing to our project! Whether you are reporting a bug, proposing an analytical improvement, or submitting code and documentation updates, please follow the guidelines below so we can maintain a reproducible and collaborative workflow.

## Development Environment (Docker & Remote SSH)

All development takes place inside our shared Docker container so every contributor works in the same computational environment. Before starting, complete the initial setup in [`README.md`](README.md) (installing Docker Desktop, generating `~/.ssh/id_ed25519`, cloning the repository, and running `docker compose pull`), install either [Positron](https://positron.posit.co/) (Remote SSH built in) or [VS Code](https://code.visualstudio.com/) with the Remote - SSH extension, and verify your local Git identity (`git config --global user.name` and `git config --global user.email`).

1. Start the container from the repository root and verify that `analysis-env` is running:

```bash
docker compose up -d
docker compose ps

```

2. Open the Command Palette (`Cmd+Shift+P` on macOS or `Ctrl+Shift+P` on Windows):
- VS Code: Run Remote-SSH: Connect to Host... -> + Add New SSH Host..., enter `ssh -p 2222 root@localhost`, save it to `~/.ssh/config`, then select `localhost`.
- Positron: Run Remote SSH: Show Remote Menu -> Connect to Host and enter `root@localhost:2222`.


3. Choose Linux as the remote platform and click Continue to trust the host fingerprint.
4. Click Open Folder, replace `/root` with `/workspace`, and press Enter. Any changes saved in `/workspace` sync immediately with your local files.
5. Select the container's project interpreter before running code: `/opt/venv/bin/python` for Python (do not use `/workspace/.venv`), or the project's `renv` library activated automatically in `/workspace` (`/workspace/renv/library`) for R.
6. When finished, close the remote editor window and stop the container from your local terminal:

```bash
docker compose down

```

### Troubleshooting SSH Connections

- `~/.ssh/id_ed25519.pub` or `~/.gitconfig` is a folder: Run `docker compose down`, remove the empty directory, create the missing file, and run `docker compose up -d`.
- `Remote host identification has changed`: Run `ssh-keygen -R "[localhost]:2222"` after pulling a new container image.
- Permission denied on Linux: Uncomment `RUN echo "StrictModes no" > /etc/ssh/sshd_config.d/container.conf` in `Dockerfile` and push so GitHub Actions builds an updated image.
- Port `2222` already in use: Change the host port in `docker-compose.yml` (for example, `2223:22`) and connect using `-p 2223`.

## How to Report a Bug or Suggest a Change

1. Check existing issues: Before opening a new issue, search the [Issues](https://github.com/UBC-MDS-2026-27/DSCI-522-Palmer-Penguin-Analysis/issues) tab to ensure the bug or suggestion has not already been reported.
2. Open a GitHub Issue: Click New issue and provide a clear, descriptive title.
- For bug reports: Include steps to reproduce the issue, the expected behavior, the actual behavior (including full error tracebacks), and your operating system and container/environment details.
- For feature or analysis suggestions: Explain what change you are proposing, why it improves the project, and how it fits into the existing workflow.


## How to Submit a Pull Request

We follow a standard GitHub Flow branching model. Please do not push commits directly to the `main` branch.

1. Create a feature branch: From an up-to-date `main` branch inside this repository, create a small, focused branch with a descriptive name (for example, `fix-data-cleaning-bug` or `add-eda-visualization`).
2. Make your changes: Keep each branch scoped to one independent piece of work. Follow the project's existing directory structure, formatting conventions, and plain-English reporting standards (avoiding code-style variable names in narrative text).
3. Verify reproducibility: Ensure that all scripts and Quarto documents render cleanly from top to bottom without errors inside the Docker container (`docker compose run --rm analysis-env uv run quarto render`), and verify that temporary files (such as `.DS_Store` or `.venv/`) are not staged.
4. Open a Pull Request (PR): Push your branch to GitHub and open a PR targeting `main`. Reference the relevant GitHub Issue in your PR description (e.g., `Closes #12`) and summarize what changed and why.
5. Peer Review: Request a review from at least one teammate. Every pull request must be reviewed and approved by a human team member before merging.

## Adding or Updating Packages

1. On a feature branch, add the package inside the container using `uv add <package>` (which pins exact versions with `==` in `pyproject.toml` and updates `uv.lock`) or `renv::install()` followed by pinning `(==x.y.z)` in `DESCRIPTION` and running `renv::snapshot()`.
2. Commit the updated environment and lock files together and push your branch.
3. Wait for the Publish image to Docker Hub GitHub Actions workflow to build the multi-architecture image and commit the new `sha-` image tag to `docker-compose.yml` on your branch, then run `git pull && docker compose pull` before merging. Once merged into `main`, every teammate should run `git checkout main && git pull && docker compose pull`.

## Republishing the GitHub Pages Report

Whenever you modify the analysis or report text, re-render inside the container and copy the self-contained HTML report to `docs/index.html` before pushing:

```bash
docker compose run --rm analysis-env uv run quarto render
cp analysis/penguin-species-classification.html docs/index.html
git add analysis/ docs/index.html
git commit -m "Re-render and republish report to GitHub Pages"
git push

```

## Generative AI Policy
Contributors may use generative AI tools (such as ChatGPT, Claude, or GitHub Copilot) to assist with brainstorming, debugging error messages, drafting boilerplate configuration, or checking grammar, subject to the following rules:

- Allowed Uses & Disclosure: If generative AI tools were used to generate or substantially revise code or prose in a contribution, you must disclose which tool was used and how it was applied in your Pull Request description.
- Contributor Responsibility: Every contributor is fully responsible for verifying, testing, and understanding all code, statistical reasoning, and text they submit, regardless of whether an AI assistant helped draft it. Fabricated references or unverified claims are strictly prohibited.
- Human Ownership of Workflow: All GitHub Issues and Pull Requests must be opened, reviewed, and merged by human contributors—never autonomously by an AI agent or bot. While AI tools may be used as a secondary check on code quality, human reviewers make all final review and merge decisions.

## Attribution
The structure and contribution workflow guidelines in this document were adapted from the [Altair Contributing Guide](https://github.com/vega/altair/blob/main/CONTRIBUTING.md) and the [earthaccess Generative AI Policy](https://github.com/nsidc/earthaccess/blob/main/CONTRIBUTING.md), as referenced in the UBC Master of Data Science DSCI 522 course guidelines.

