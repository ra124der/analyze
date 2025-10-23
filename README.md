# Data Processing Pipeline

This repository hosts a data processing pipeline designed to convert Excel data, process it using Python, and publish the results automatically via GitHub Pages. The pipeline emphasizes robust data handling, code quality, and continuous integration/delivery (CI/CD).

## Project Structure

- `data.xlsx`: The source Excel file containing raw data.
- `execute.py`: A Python script responsible for processing `data.csv` and generating `result.json`.
- `.github/workflows/ci.yml`: GitHub Actions workflow that automates the data conversion, script execution, code linting, and deployment.
- `index.html`: A simple, responsive web page providing an overview of the project and links to the generated `result.json`.
- `README.md`: This document.
- `LICENSE`: The MIT License for the project.

## Features

-   **Automated Data Conversion**: Converts `data.xlsx` to `data.csv` as part of the CI/CD pipeline, ensuring `execute.py` always works with a fresh CSV.
-   **Robust Data Processing**: `execute.py` is designed to handle and process tabular data efficiently, compatible with Python 3.11+ and Pandas 2.3+. It aggregates data and outputs a structured JSON result.
-   **Code Quality**: Integrated with [Ruff](https://ruff.rs/) for fast Python linting and code formatting checks within the CI/CD pipeline.
-   **Continuous Integration/Delivery (CI/CD)**: A GitHub Actions workflow automates the entire process from code push to result publication.
-   **GitHub Pages Deployment**: The generated `result.json` is automatically published to GitHub Pages, making the processed data easily accessible via a public URL.

## Getting Started

To set up and run this project locally or deploy it to your own GitHub repository, follow these steps:

### Prerequisites

-   Python 3.11+
-   Pandas 2.3+
-   `openpyxl` (for `.xlsx` file handling)
-   `ruff` (for linting)

You can install the necessary Python packages using pip:
```bash
pip install pandas~=2.3 openpyxl ruff
```

### Local Setup

1.  **Clone the repository**:
    ```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
    ```
2.  **Prepare `data.csv`**:
    First, ensure `data.xlsx` is in the root directory. Then, convert it to `data.csv`:
    ```bash
python -c "import pandas as pd; df = pd.read_excel('data.xlsx'); df.to_csv('data.csv', index=False)"
    ```
    This step creates `data.csv` which `execute.py` will read.
3.  **Run the Python script**:
    ```bash
python execute.py > result.json
    ```
    This will generate `result.json` in your local directory.
4.  **Run Ruff linter**:
    ```bash
ruff check .
    ```

### GitHub Actions Workflow

The `.github/workflows/ci.yml` file defines the CI/CD pipeline, which automatically performs the following actions on every push to the `main` branch:

1.  **Checkout repository**: Fetches the latest code.
2.  **Set up Python**: Configures Python 3.11.
3.  **Install dependencies**: Installs `pandas`, `ruff`, and `openpyxl`.
4.  **Convert `data.xlsx` to `data.csv`**: Generates `data.csv` from `data.xlsx`.
5.  **Run Ruff Linter**: Checks Python code for style and potential errors.
6.  **Execute Python script**: Runs `execute.py` and redirects its output to `result.json`.
7.  **Deploy to GitHub Pages**: Publishes `result.json` to GitHub Pages, making it accessible at a URL like `https://your-username.github.io/your-repo/result.json`.

You can monitor the workflow's progress and view logs in your repository's "Actions" tab.

## Contributing

Feel free to open issues or submit pull requests. Please adhere to the existing code style and ensure all tests (including Ruff checks) pass.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.