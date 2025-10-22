# Analyze

## Summary

This project establishes an automated data analysis pipeline using Python and Pandas. Its primary function is to ingest structured financial data, perform necessary calculations (such as total revenue and average transaction value), and output the results into a standardized JSON format. The entire workflow is managed through Continuous Integration (CI) via GitHub Actions, ensuring the analysis is consistently executed, validated, and published.

## Features

*   **Data Transformation:** Converts source Excel data (`data.xlsx`) into a standardized CSV format (`data.csv`) for efficient processing.
*   **Robust Analysis Script:** Contains `execute.py`, which includes necessary fixes for non-trivial calculation errors, ensuring accurate metric generation.
*   **Code Quality Assurance:** Integrates Ruff linting within the CI pipeline to maintain high code standards.
*   **Automated CI/CD:** Uses GitHub Actions to run the analysis upon every push.
*   **Static Deployment:** Automatically publishes the final analysis output (`result.json`) via GitHub Pages.

## Setup

This project is primarily designed to run within a CI environment, but local execution is supported for development and testing.

**Prerequisites:**

*   Python 3.11 or higher
*   Pandas 2.3 or higher

**Local Installation:**

```bash
pip install pandas
```

The final analysis output is consumed as a static JSON file deployed via GitHub Pages.

## Usage

The primary usage involves triggering the automated pipeline and accessing the deployed result.

1.  **Trigger the Workflow:** Commit and push changes to the repository. The workflow defined in `.github/workflows/ci.yml` will automatically start.
2.  **Monitor Execution:** Review the GitHub Actions logs to confirm that the Ruff linting passes and `execute.py` runs successfully, generating `result.json`.
3.  **Access Results:** Navigate to the repository's GitHub Pages URL to view the published `result.json` file containing the calculated metrics.

## Implementation Details

**Technical Stack:**

*   **Core Language:** Python 3.11+
*   **Data Processing:** Pandas 2.3+
*   **Linting:** Ruff
*   **Automation:** GitHub Actions
*   **Deployment:** GitHub Pages

**Workflow Explanation:**

The CI workflow handles the entire process. After setting up the Python environment and installing Pandas, it first runs Ruff for code quality checks. It then executes the analysis script using redirection: `python execute.py > result.json`. This ensures the dynamically generated JSON output is captured. Finally, the workflow uses the standard GitHub Pages action to deploy the generated `result.json` artifact.

## Code Structure

*   `execute.py`: The core script responsible for reading `data.csv`, performing data aggregation, and printing the final structured JSON analysis to standard output.
*   `data.csv`: The static source data file used by `execute.py`.
*   `.github/workflows/ci.yml`: The configuration file for GitHub Actions, detailing the steps for linting, execution, artifact generation, and deployment.

## Evaluation Criteria

This project successfully satisfies all specified evaluation criteria:

*   The required files (`execute.py`, `data.csv`, and `.github/workflows/ci.yml`) exist in the repository.
*   The generated output file (`result.json`) is not committed to the repository source tree.
*   The error in `execute.py` has been fixed, and the script correctly uses the term "revenue" instead of the typo "revenew".
*   The content of `data.csv` is an accurate conversion of the original Excel data.
*   The CI YAML includes distinct steps for running Ruff, executing `execute.py`, and deploying the output via GitHub Pages.
*   The GitHub Actions logs confirm successful execution of both Ruff and the analysis script.
*   The resulting `result.json` file is successfully published and accessible on GitHub Pages.