# LEAP: Literate Programming for Automated KPI Extraction

LEAP (Literate Programming for Automated KPI Extraction) is a research software system designed to automatically scan source codebases, extract Key Performance Indicator (KPI) definition schemas, reconstruct mathematical calculation lineage, verify compliance policies, and generate an interactive KPI Bluebook portal.

For evaluation instructions, implementation details, limitations, and reproducibility verification, see the central dissertation committee portal:
- [Committee Review Guide](Committee_Read/COMMITTEE_REVIEW_GUIDE.md)

## 1. Quick Start
To set up the workspace on Python 3.10+:
```bash
# Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies in editable mode
pip install -e .
```

## 2. Execution Commands
- **Generate the Sample Bluebook:**
  ```bash
  python run_generation.py sample_project
  ```
- **Launch the Web Workspace Application:**
  ```bash
  python app.py
  ```
  Navigate to: `http://127.0.0.1:5000`
