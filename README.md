# LEAP: A Code-Anchored Approach to the KPI Knowledge Gap

LEAP (Literate Programming for Automated KPI Extraction) is the research artifact for a dissertation on a persistent enterprise problem: the business meaning of a Key Performance Indicator (KPI), its mathematical definition, its implementation in code, and its governance record are often maintained separately. That separation forces repeated translation between business and technical teams, makes review difficult, and allows documentation to drift from the executable logic that produces reported values.

The dissertation investigates whether a hybrid literate-programming approach can make those forms of KPI knowledge inspectable together. LEAP combines deterministic evidence construction with AI-agent assistance: the deterministic layer identifies, structures, and preserves traceable source evidence, while the AI layer can help turn that grounded evidence into useful explanations and workflow support. LEAP then publishes an Interactive Bluebook that links the available business definition, formula, variables, source location, provenance, ownership, and review signals for a KPI. Executable source remains authoritative for what a system computes; the Bluebook is the shared, traceable representation through which stakeholders can examine that evidence.

## Research Proposition

The research proposition is not that software generation alone solves an organizational problem. It is that code-anchored KPI documentation can provide a durable boundary object between people who define and use a metric and people who implement and maintain it.

This repository lets the committee inspect the hybrid technical intervention behind that proposition:

- deterministic discovery and structuring of KPI evidence from heterogeneous source artifacts;
- AI-agent assistance that works from the structured evidence to support readable explanation and review work;
- reconstruction and presentation of formula lineage where evidence is available;
- an Interactive Bluebook that places business-facing and technical evidence in one reviewable record;
- provenance, ownership, governance, and review signals that make uncertainty visible rather than silently asserting certainty.

The dissertation evaluates this intervention through prospective hypotheses concerning documentation effort, documentation fidelity, interpretation, runtime and governance behavior, cognitive bridging, cross-functional collaboration, and adoption. The repository demonstrates the implemented system and its tested technical behaviors. It does **not** claim that the current package alone proves causal reductions in meeting duration, documentation time, misunderstandings, or organizational outcomes.

Historical meeting observations are contextual, descriptive evidence about communication burden. They do not independently show that LEAP caused a reduction in meeting duration. Likewise, final precision, recall, formula-fidelity, and human-subject claims require the separately governed adjudicated and participant-level evidence described in the dissertation.

## Committee Review

Start with the [Committee Review Guide](Committee_Read/COMMITTEE_REVIEW_GUIDE.md). It provides a short review route through the static Bluebook, the research-artifact boundaries, and reproducibility checks.

For a direct static review, open [docs/_build/index.html](docs/_build/index.html) in a browser.

## Reproduce the Technical Artifact

To set up the workspace on Python 3.10+:
```bash
# Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies in editable mode
pip install -e .
```

Generate the sample Bluebook:
```bash
python run_generation.py sample_project
```

Run the technical tests:
```bash
python -m pytest -q
python data/validation/test_scenario_fixtures.py
```

Launch the local workspace:
```bash
python app.py
```

Then open `http://127.0.0.1:5000`.

## Scope of This Package

This committee package contains the runnable research artifact, a static Bluebook build, controlled validation scenarios, and concise review material. It does not package the separate research-evidence archive or represent a claim of legal certification, universal extraction accuracy, or completed human-subject evaluation.
