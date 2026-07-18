# LEAP Dissertation Committee Review Guide

This guide serves as the central evaluation portal for the dissertation committee. It details the page navigation, implementation status, reproducibility verification, and operational boundaries of the LEAP package.

## 1. Quick Start & Portal Navigation
The candidate package contains a pre-compiled static Interactive Bluebook build that can be reviewed immediately:
- **Starting Point:** Open [docs/_build/index.html](docs/_build/index.html) in any web browser.
- **RACI Directory:** Navigate to [docs/_build/raci_directory.html](docs/_build/raci_directory.html) to see stakeholder assignments.
- **Compilation Report:** Navigate to [docs/_build/discovery_report.html](docs/_build/discovery_report.html) for extraction metrics.

To run the interactive web application, follow the installation commands in `../README.md`, run:
```bash
python app.py
```
And navigate to `http://127.0.0.1:5000` in your browser.

## 2. Implemented Capabilities
- **Deterministic Extraction Engine:** Scans target source files, extracts KPI comments (e.g. `# KPI:`, `-- Objective:`), and identifies math expressions.
- **MATE (Mathematical Annotation and Tagging Engine):** Renders annotated KPI formulas, associates operators/operands with business and development labels, and presents lineage details inside the Interactive Bluebook.
- **Governance Engine:** Assigns RACI ownership based on source tags and local override rules.
- **Review Queue:** Routes weak metric candidates to the review view, providing owner confirmation guidance, Copy Review Text, and Open Email Draft actions.
- **Compliance Scanner:** Evaluates rules against tested structural scenarios.

## 3. Explicit Boundaries and Limitations
- **VATE (Visual Annotation Engine):** Not implemented.
- **EBRE (Evidence-Based Rule Engine):** Not implemented.
- **AI Enrichment Posture:** Optional AI enrichment is disabled by default, operates entirely out-of-band of deterministic extraction, and is not required for correctness.
- **Compliance Boundaries:** Compliance checks are structural rule checks tested in bounded validation scenarios. They do not constitute legal compliance, regulatory certification, or audit assurance for GDPR, Saudi PDPL, NCA ECC, or SOC 2.
- **Review Workflow Limits:** The review queue provides copy, drafting, and guidance actions. Persistent review state management (e.g., resolutions, approvals, overrides, or mutes) is not implemented.

## 4. Local Execution & Privacy boundaries
- **Offline Operations:** All deterministic parser functions, governance resolutions, and HTML builds execute locally. No source code or metrics data is transmitted to external endpoints.
- **Credential Separation:** API keys are read from standard environment variables (like `OPENAI_API_KEY`) and are never stored or hardcoded.
- **Path and Data Privacy:** Local workspace directories and personal paths are excluded from packaging guides and active configurations. Stakeholder emails in RACI models use template examples (`cfo.office@enterprise.example`).

## 5. Pipeline Reproducibility Commands
To verify the extraction pipeline, run these commands from the repository root:
1. **Regenerate the Bluebook:**
   ```bash
   python run_generation.py sample_project
   ```
2. **Execute Unit Tests:**
   ```bash
   python -m pytest -q
   ```
3. **Verify Scenario Fixtures:**
   ```bash
   python data/validation/test_scenario_fixtures.py
   ```
   This validates all 38 compliance and extraction scenarios under `data/validation/generated_scenario_kpis/`.

## 6. Submission Readiness: READY_WITH_QUALIFICATIONS
The committee candidate package is ready for evaluation with the following qualifications:
- Optional AI enrichment is disabled by default.
- Compliance scanner outputs are bounded checks and do not represent legal compliance certifications.
- VATE and EBRE are not implemented.
- Persistent state management for review queue decisions is not implemented.
- Running the generation pipeline requires local Python dependencies (Sphinx, Flask, python-dotenv, click, Jinja2).
