# LEAP Package Contents & Guide

Welcome to the LEAP Committee Candidate Delivery. This repository contains the fully functional LEAP tool and the generated Interactive Bluebook.

### How to Run LEAP Locally
1. Ensure your environment meets the dependencies defined in `requirements.txt`.
2. Start the web interface by running:
   ```bash
   python app.py
   ```
3. Navigate to `http://localhost:5000` in your web browser.

### The Sample Project
The `sample_project/` directory contains the mock enterprise repository utilized to demonstrate LEAP's capabilities. It contains all necessary code, tests, logs, and documentation for LEAP to process and extract KPIs deterministically.

### Regenerating the Bluebook
To regenerate the static Interactive Bluebook from the source data (the `sample_project/`), run the following command from the repository root:
```bash
python run_generation.py sample_project
```
This process leverages the core LEAP engine (`bluebook_generator/`) to scan, extract, and compile the enterprise metric sources into the final documentation.

### Viewing the Generated Bluebook
The compiled Interactive Bluebook is stored statically within the repository. To view it, open:
`docs/_build/index.html`
in any modern web browser.

### Running Validation
To validate LEAP's deterministic correctness and governance rule application, run the integrated test suite:
```bash
python -m pytest -q
```

### Optional AI Enrichment
LEAP provides an optional AI enrichment engine. **This optional feature is completely disabled by default.** LEAP's deterministic processing (including governance, formula extraction, and compliance) is fully functional and runnable without it. To enable AI enrichment, a valid `OPENAI_API_KEY` and the `LEAP_ENABLE_AI=1` environment variable must be supplied.
