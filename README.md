# Bio-App Project: Peptide Classification using ChemLog and ChEBI

## Description
This project demonstrates the utilization and automation of **chemlog**, a bioinformatics tool, to fetch, process, and classify chemical structures from the **ChEBI** (Chemical Entities of Biological Interest) database, specifically focusing on peptide classification.

The codebase includes an advanced programmatic approach to handle Command Line Interface (CLI) tools within Python by capturing and redirecting system standard outputs (`stdout`/`stderr`) dynamically during loop executions.

## Features
* **Installation & Setup**: Simple environment configuration for running the tool.
* **Automated Retrieval**: Downloads and filters chemical versions tailored to specific strategies.
* **Targeted Extraction**: Specifically isolates chemical data to extract and classify peptides (`--only-peptides`).
* **Output Redirection**: Manages system outputs programmatically using `StringIO` to capture and log CLI results for individual batch processing steps inside loops.

## Getting Started

### Prerequisites
To run this notebook, install the `chemlog` library within your environment:
```bash
pip install chemlog
```
```bash
python -m chemlog classify-chebi --chebi-version 239 --strategy algo --only-peptides --n-molecules 1000
from chemlog.cli import classify_chebi
import sys
from io import StringIO

# Target test peptides
peptides = ["GAS", "ACD", "GGGG"]

# Arguments configuration
args_list = ['--chebi-version', '239', '--strategy', 'algo', '--only-peptides', '--n-molecules', '1000']

for seq in peptides:
    print(f"Attempting to run batch classification for current loop (peptide: {seq})")
    
    # Redirect stdout and stderr to capture the CLI output
    old_stdout = sys.stdout
    old_stderr = sys.stderr
    redirected_stdout = StringIO()
    redirected_stderr = StringIO()
    sys.stdout = redirected_stdout
    sys.stderr = redirected_stderr
    
    try:
        # Calls the Click command's main method with the arguments list...
        pass
    finally:
        # Restore original streams
        sys.stdout = old_stdout
        sys.stderr = old_stderr
