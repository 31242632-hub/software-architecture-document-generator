# Automated Synthesis of Software Architecture Design Documents from GitHub Repositories

## What this prototype does
This student-project prototype analyses **local Python source directories** and creates:
- a Markdown architecture analysis report;
- a Word (`.docx`) report;
- a JSON inventory of files, classes, functions and imports;
- a PNG module dependency diagram (requires matplotlib).

It does not yet clone GitHub URLs directly. Clone a repository with Git first, then pass the local directory to the tool. This keeps the first version reproducible and avoids handling credentials/tokens.

## Requirements
- Python 3.10 or later recommended
- pip
- Internet access only to install packages, if not already installed

## Setup in VS Code (Windows)
Open this folder in VS Code, then choose **Terminal → New Terminal**.

```powershell
python --version
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

If PowerShell blocks activation, use `py -m pip install -r requirements.txt` and run commands with `py`.

## Run on the included sample project
From the project root:

```powershell
python -m src.main --source sample_project --output generated_reports --name "Sample Project"
```

Expected console summary: 3 Python files, 1 class, several function definitions, and a generated report folder. Counts can vary slightly with parser changes.

## Run on a local repository
Clone the repository using Git, then point `--source` to the cloned folder:

```powershell
git clone <repository-url> my_repo
python -m src.main --source my_repo --output generated_reports --name "Repository Name"
```

Only Python files are analysed in this version.

## Run tests
```powershell
python -m unittest discover -s tests -v
```

## Output files
- `architecture_report.md`
- `architecture_report.docx`
- `architecture_analysis.json`
- `module_dependencies.png` (if matplotlib installed)

## Limitations and responsible interpretation
- This is static analysis, not a complete architecture recovery system.
- Only Python files are supported.
- Import relationships are heuristic and may miss package-relative or dynamic dependencies.
- The tool does not infer deployment architecture, runtime call graphs, data flows, security properties, or business requirements.
- A generated report requires human review.
- The report uses concepts associated with software architecture descriptions but does **not** claim formal or certified compliance with IEEE Std 1016. Check the official standard and your instructor's rubric before using a compliance claim.
- Do not upload confidential/private repositories to third-party services without permission.
