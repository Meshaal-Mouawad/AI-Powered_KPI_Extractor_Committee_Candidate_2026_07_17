# LEAP Demo Runbook

This runbook is for a quick local demo of the accepted LEAP enterprise KPI intelligence workspace.

## Recommended Mode

LEAP runs in deterministic offline mode by default. You do not need an OpenAI API key for the standard demo.

Use optional AI enrichment only when deliberately testing draft narrative generation:

```bash
export LEAP_ENABLE_AI=1
export OPENAI_API_KEY=your_key
```

## 1. Start From The Repo Root

```bash
cd /Users/meshaalmouawad/AI-Powered_KPI_Extractor_Interactive_Bluebook_Generator
```

## 2. Install Dependencies

```bash
python -m pip install -e .
```

## 3. Generate The Demo Workspace

```bash
python run_generation.py sample_project
```

Expected result:

- 12 governed business metrics
- average confidence around 91%
- `Workspace build successful`

## 4. Launch The Local Workspace

```bash
python app.py
```

Open:

```text
http://127.0.0.1:5000
```

## 5. Demo Flow

1. Open the workspace dashboard.
2. Show the executive attention layer.
3. Open Discovery Workspace.
4. Show Portfolio Actions and Enterprise KPI Dossiers.
5. Open RACI Directory.
6. Show Accountability Risk Signals.
7. Open a KPI dossier.
8. Show the hero summary, Business Reading, Mathematical Formulation, and Evidence & Lineage.
9. Open Search and Index as secondary utilities.

## 6. Quick Health Checks

```bash
python run_generation.py sample_project
python - <<'PY'
from app import app
client = app.test_client()
for path in ["/", "/status", "/api/stats", "/bluebook/index.html", "/bluebook/discovery_report.html", "/bluebook/raci_directory.html", "/bluebook/search.html"]:
    resp = client.get(path)
    print(path, resp.status_code)
PY
```

Expected status codes:

- `/` -> 200
- `/status` -> 200
- `/api/stats` -> 200
- `/bluebook/index.html` -> 200
- `/bluebook/discovery_report.html` -> 200
- `/bluebook/raci_directory.html` -> 200
- `/bluebook/search.html` -> 200

## 7. Important Commit Hygiene

Generation rewrites `docs/` and `docs/_build/`. If you are only running a demo after an accepted commit, restore generated changes afterward:

```bash
git restore docs docs/_build
git clean -f docs/_build
```

Keep `.ai/ui/NEXT_PHASE_PROMPTS/` local unless you intentionally want to commit handoff prompts.

