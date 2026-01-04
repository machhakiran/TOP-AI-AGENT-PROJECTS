# <font color="#009eff">Contributing to TOP-AI-AGENT-PROJECTS</font>

Welcome — this repository collects TOP AI agent projects, templates, demos, and integrations. Thank you for helping grow a practical, reproducible, and responsible catalog of agent work. This document is tuned to the AI-agent focus of the project: reproducibility, model/data hygiene, evaluation, and safety.

Quick Summary
- **Focus**: runnable, well-documented agent examples and templates.
- **Reproducibility**: All demos should be easily reproducible with minimal setup.
- **Structure**: Follow our folder schema and metadata for better discoverability.
- **Safety**: Adhere to ethical AI practices and data hygiene.

---

## <font color="#d12ae3">What to contribute</font>
- New agent projects (single- or multi-agent; code, notebooks, or demos).
- Templates/boilerplates for agent types (reactive, planning-based, learning agents, RL, LLM-based, etc.).
- Integrations (environments, simulators, observability / logging tools).
- Shared tooling (evaluation harnesses, metrics, benchmark suites, dataset loaders).
- Docs, reproducible experiments, visualization utilities, or lightweight datasets (or links to them).

If your contribution is large (new category, many projects, major refactor) please open an issue first to coordinate placement and naming.

---

## <font color="#ff9600">Project folder requirements (must-have)</font>
Each agent project added must include the following at the top level of its folder:

- README.md — concise description, intended use-case, quick start with exact commands, expected output, and runtime (CPU/GPU/time).
- LICENSE or a note referencing repository root LICENSE (see root LICENSE).
- requirements.txt, pyproject.toml, or environment.yml (pin critical dependency versions).
- One or more runnable examples (script or notebook) that reproduce the core behavior.
  - Provide minimal example(s) that run in <10 minutes on a modest machine where possible.
- tests/ or a smoke-test script with instructions to run them.
- metadata.yaml or metadata.json (see example below).
- small models / datasets should be included only if tiny. Prefer external hosting (Hugging Face, S3, Google Drive) with a download script.

Example metadata schema (recommended)
```yaml
title: quick-chatbot-agent
author: Your Name <you@example.com>
language: python
tags:
  - llm
  - agent
  - rl
license: MIT
datasets:
  - name: example-dialogs
    url: https://...
entrypoint: run_demo.py
requirements: requirements.txt
```

---

## <font color="#009eff">Naming & layout conventions</font>
- Folder names: lowercase, hyphen-separated (e.g., multi-agent-pursuit).
- Place one logical project per folder.
- Keep demos and notebooks near the code: demo.ipynb and run_demo.py in the project root.
- Avoid committing large binaries. Use .gitattributes or .gitignore to keep repository clean.

---

## Reproducibility & experiments
- Include seed values, environment variables, and exact dependency versions.
- Provide a minimal run command and expected output sample.
- For stochastic experiments, include evaluation scripts and deterministic seeds or checkpoints.
- If results require large compute or private data, include a small reproducible “toy” example that demonstrates the same pipeline on tiny inputs.

---

## Models, datasets & large files policy
- Don’t add large datasets or model checkpoints directly. Instead:
  - Provide a download script (download.sh / download.py) that fetches artifacts from a stable host (Hugging Face, S3, Zenodo).
  - Document the expected location/path after download.
- Clearly state dataset licenses, attribution, and any usage restrictions.
- When linking to external model weights provide their license and any fine-tuning provenance.

---

## Code style, documentation & tests
- Python: follow PEP 8, add a linter config (.flake8, pyproject.toml with [tool.black] or similar).
- JS/TS: provide ESLint/Prettier configs where relevant.
- Document complex algorithms with short docstrings and references.
- Add unit or integration tests when possible. Include a lightweight smoke test that CI can run quickly.

---

## Evaluation & metrics
- Include an evaluation script that produces metrics (accuracy, reward, latency).
- State measurement conditions (hardware, seeds).
- Where applicable, include latency and memory cost alongside performance metrics.

---

## CI / GitHub Actions recommendations
- If adding workflows, put them under .github/workflows and ensure expensive jobs are optional or use small inputs.
- Recommended checks: lint, unit tests, smoke demos. Heavy training jobs should be omitted or gated/opt-in.

---

## <font color="#d12ae3">🚀 PR Process and Checklist</font>

Before opening a Pull Request, please ensure you've checked the following:

- [ ] **Fork & Branch**: Fork the repo and create a branch like `feat/new-agent-name`.
- [ ] **Folder Structure**: Ensure your project is in its own folder with a `README.md` and `metadata.json`.
- [ ] **Dependencies**: Include a `requirements.txt` or `pyproject.toml`.
- [ ] **Reproducibility**: Provide a clear "How to Run" section with expected outputs.
- [ ] **Safety & Secrets**: Ensure no API keys or private data are committed.
- [ ] **License**: All contributions must be compatible with the MIT license.

PR description should include:
- What changed and why
- How to run the example(s) and tests
- Links to related issues or external artifacts (datasets, model hosts)

Suggested minimal PR template (add to .github/PULL_REQUEST_TEMPLATE.md if helpful):
```markdown
## Summary
Short description of change

## How to run
1. pip install -r requirements.txt
2. python run_demo.py

## Checklist
- [ ] README updated
- [ ] metadata.yaml added/updated
- [ ] smoke test included
```

---

## Security, secrets & responsible disclosure
- Never commit secrets, private keys, or API tokens.
- If you discover a security vulnerability, do not open a public issue. Contact maintainers privately (see repository contact info) or use GitHub's private security advisory.

---

## Ethics, fairness & safety
AI agents can amplify harms. When contributing:
- Include an explicit "Ethical considerations" or "Safety notes" section in the README if the agent interacts with people, makes decisions, or processes personal data.
- State potential biases, failure modes, and appropriate usage guidance.
- Avoid shipping models trained on clearly disallowed data (private or scraped personal content without consent).
- Prefer human-in-the-loop defaults for high-risk demos and clearly mark such demos as not production-ready.

---

## Licensing and attribution
- Respect upstream licenses for models, code, and datasets. Include attribution and license text where required.
- If the project uses third-party models/datasets, list their license and link to the source.

---

## Communication & review
- Maintainers will review PRs and may request changes. Please reply to review comments and push updates.
- For large or disruptive changes, maintainers may ask for staged PRs to ease review.

---

## Contributor support & contact
If you need early feedback:
- Open an issue describing your planned contribution with the following: summary, folder name, and minimal example of what you plan to add.
- For urgent or private matters, use the contact method listed in the repository (owner profile / repo settings).

---

## Code of Conduct
By contributing, you agree to the project's Code of Conduct. Be respectful, constructive, and collaborative.

---

Thank you for contributing to TOP-AI-AGENT-PROJECTS — your examples, templates, and tools make the agent community stronger and more reproducible.
