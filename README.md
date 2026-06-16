# Automated GitHub Pages Deployment Workflow

An automated CI/CD (Continuous Integration/Continuous Deployment) pipeline built with GitHub Actions. This workflow listens for code updates on the repository, detects changes specifically targeting the frontend presentation layer, spins up a virtualized runner instance, and updates the live production website hosted on GitHub Pages completely hands-free.

## Architecture & Automation Pipeline

[Image of GitHub Actions CI/CD deployment pipeline workflow showing code push, path filtering, artifact creation, and GitHub Pages deployment steps]

The deployment execution pipeline follows a strict, event-driven lifecycle:
1. **Event Interception (Path Filtering):** A developer pushes code to the `main` branch. GitHub's webhook manager parses the commit file manifest.
2. **Conditional Evaluation:** If changes are detected inside `index.html`, the workflow proceeds. If changes only affect documentation (like this README), the runner bypasses execution to conserve action minutes.
3. **Environment Provisioning:** GitHub spins up an isolated virtual machine container running the latest stable release of Ubuntu Linux.
4. **Artifact Compilation:** The workspace repository code is cloned securely into the container, bundled into a compressed deployment artifact, and shipped to the GitHub Pages production server engine.

## Repository File Tree

```text
gh-deployment-workflow/
├── .github/
│   └── workflows/
│       └── deploy.yml         # GitHub Actions configuration pipeline file (YAML)
├── index.html                 # Core website entry point ("Hello, GitHub Actions!")
└── README.md                  # Comprehensive project blueprint and documentation

Link: https://amal-krishna123.github.io/github-page-deployment/
