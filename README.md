# CSCI 2371 Semester Project

> Database Administration and Data Mining, Columbus State Community College
> Student project repository. Rename this repo to `csci2371-project-<username>` after you fork it, where `<username>` is your Columbus State username (for example `jsmith3`), not your last name. Usernames are unique, so this avoids collisions when students share a last name.

**Student:** _your name here_
**Domain:** _your chosen domain here_
**Platform:** Databricks Free Edition (serverless) + GitHub
**Term:** _e.g., Fall 2026_

---

## What this repository is

This is the home for your semester-long project. You will build one evolving data project across four phases: it starts as an empty schema in Databricks in Week 1 and ends as a deployed predictive model with an ethics review in Week 16. Everything you produce (SQL, notebooks, diagrams, docs, exports) lives here and is version-controlled with Git.

Because Databricks Free Edition workspaces are personal and student-owned, **the instructor grades from the artifacts you commit here**, not by running code in your workspace. Commit early, commit often, and always commit an executed HTML export of each notebook.

## Tech stack

- **Databricks Free Edition** (serverless compute, Unity Catalog, Delta Lake, Spark, MLlib, MLflow). Sign up at `https://signup.databricks.com/free`.
- **GitHub** for version control, connected to Databricks via Git folders.
- **Databricks SQL** for Phase 1 (DDL, DML, Unity Catalog governance, Delta time travel).
- No external database server is used.

## Repository structure

```
csci2371-project-<username>/
├── README.md               ← this file (fill in your name and domain)
├── docs/
│   ├── business_case.md
│   ├── phase1_design.md         ERD (Mermaid) + normalization notes
│   ├── data_dictionary.md
│   ├── recovery_demo.md         Delta time-travel recovery writeup
│   ├── phase2_pipeline.md       medallion plan + architecture diagram
│   ├── quality_report.md
│   ├── feature_dictionary.md
│   ├── phase3_modeling.md
│   ├── ethics_review.md
│   └── phase4_report.md
├── sql/
│   ├── 00_create_schema.sql     idempotent DDL (managed Delta tables)
│   ├── 01_load_data.sql         DML / COPY INTO from the raw Volume
│   └── 02_governance.sql        GRANT / REVOKE (Unity Catalog)
├── notebooks/
│   ├── 01_bronze_ingest
│   ├── 02_silver_build
│   ├── 03_data_quality
│   ├── 03_gold_features
│   ├── 04_modeling
│   └── 05_unsupervised
├── exports/                 HTML exports of executed notebooks (graded artifacts)
├── mlflow_runs/             exported MLflow run summaries (JSON) — Phase 3
├── screencast/              Phase 4 fresh-Volume reproducibility video
├── slides/                  Phase 4 presentation deck
├── data/                    gitignored — never commit raw data
└── .github/workflows/       optional GitHub Actions (e.g., SQL lint)
```

## Quick start (Week 1)

1. **Fork** the course starter repo and **rename** your copy to `csci2371-project-<username>` (use your Columbus State username, e.g., `jsmith3`).
2. Create a **Databricks Free Edition** account with your CSCC student email and run a one-cell `spark.range(10).display()` notebook to confirm serverless works.
3. In Databricks, connect this repo with **Git folders** (Repos).
4. Configure Git locally:
   ```bash
   git config --global user.name  "Your Name"
   git config --global user.email "you@students.cscc.edu"
   ```
5. Pick your **domain** from the course's Approved Project Domains, download its starter dataset, and upload the file(s) to a **Unity Catalog Volume** (for example `/Volumes/main/default/csci2371_raw/`).
6. Fill in the top of this README (name, domain, term) and commit.

## Phases, points, and submission tags

Each phase has a two-week completion window and is submitted by pushing a **Git tag** and opening a **Pull Request**.

| Phase | Focus | Window | Due | Points | Tag |
|---|---|---|---|---|---|
| 1 | Database design & administration (Databricks SQL) | Weeks 5–6 | End of Week 6 | 55 | `phase1_final` |
| 2 | Data engineering pipeline (bronze/silver/gold) | Weeks 10–11 | End of Week 11 | 65 | `phase2_final` |
| 3 | Modeling, evaluation, ethics | Weeks 13–14 | End of Week 14 | 60 | `phase3_final` |
| 4 | Final deliverable & presentation | Weeks 14–15 | End of Week 15 | 70 | `phase4_final` |

Tag and push a phase like this:

```bash
git add -A
git commit -m "Phase 1 final submission (AI: used Claude to debug DDL syntax)"
git tag phase1_final
git push origin main --tags
```

Then open a Pull Request and paste the tag URL and PR URL into the matching Blackboard assignment.

## What "done" looks like per phase

- **Phase 1:** normalized 3NF ERD, idempotent `sql/00_create_schema.sql`, data loaded from the Volume, `sql/02_governance.sql` grants matrix, a Delta time-travel recovery in `docs/recovery_demo.md`, plus reporting views and queries.
- **Phase 2:** bronze → silver → gold as Delta tables, a durable `quality_manifest` table + `docs/quality_report.md`, a gold feature table with a defined target, and an architecture diagram.
- **Phase 3:** a baseline and an improved supervised model, a k-means solution, honest test-set evaluation with a group-level breakdown, MLflow runs exported to `mlflow_runs/`, and `docs/ethics_review.md`.
- **Phase 4:** `docs/phase4_report.md`, a slide deck, a recorded talk, a 2–4 minute fresh-Volume reproducibility screencast, and HTML exports of every notebook.

## Conventions

- **HTML exports are required.** For every notebook, commit an executed export under `exports/` (Databricks: File → Export → HTML). If the export shows no cell output, the work is graded as incomplete.
- **Commit small and often.** Steady, incremental commits are expected; a single end-of-phase mega-commit loses credit.
- **Declare AI use.** Every commit message must include a one-sentence note of what AI assistance you used, if any (for example: `AI: ChatGPT explained window-function syntax`). Undisclosed verbatim AI text in writing is a violation.
- **Never commit data or secrets.** Keep raw data in `data/` (gitignored) and in your Volume. No passwords, tokens, or connection strings anywhere in the repo.
- **Branch per week** (optional but encouraged): `feature/<topic>`, then PR into `main`.

## Reproducibility

Your pipeline must re-run from a fresh Volume in your own workspace. Before each phase submission, delete your bronze schema, re-upload the raw data, and run every notebook top to bottom to a green cell. For Phase 4, record that run as `screencast/phase4_reproduce.mp4`.

## Suggested `.gitignore`

```gitignore
data/
*.csv
*.parquet
.DS_Store
.ipynb_checkpoints/
__pycache__/
*.log
```

## Academic integrity

Code, SQL, and notebooks committed here must be your own work or properly attributed. Generative AI tools are permitted for learning and debugging, but must be disclosed in commit messages as described above. See the course syllabus for the full policy.

---

*Part of the CSCI 2371 course package, Columbus State Community College.*
# csci2371-project-template
# csci2371-project-template
