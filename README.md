# Nunn Lab Proteomics Analysis Documentation

This repository contains the source code for the Nunn Lab's proteomics analysis documentation, which is built using Sphinx and hosted on Read the Docs.

## Overview

The documentation provides detailed instructions and best practices for processing proteomics data using various Nextflow workflows. It is intended to be a comprehensive resource for members of the Nunn Lab at the University of Washington.

## Local Development

To build and test the documentation locally, you will need to have Python installed. It is recommended to use a virtual environment to manage project dependencies.

1.  **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd proteomics-analysis-documentation
    ```

2.  **Create and activate a virtual environment:**

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    ```

3.  **Install the required dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Build the documentation:**

    Navigate to the `docs` directory and use the provided `Makefile` to build the HTML version of the documentation.

    ```bash
    cd docs
    make html
    ```

5.  **View the documentation:**

    Open the `docs/_build/html/index.html` file in your web browser to view the documentation.

## Contributing

Contributions to the documentation are welcome. Please feel free to open an issue or submit a pull request if you find any errors or have suggestions for improvements.
