Overview
--------

Bandit is a tool designed to find common security issues in Python code.  
It processes each file, builds an AST (Abstract Syntax Tree), and runs plugins against the AST nodes.  
Once Bandit has finished scanning, it generates a report highlighting potential vulnerabilities.

Bandit was originally developed within the OpenStack Security Project and later rehomed to PyCQA.

tool designed to find common security issues in Python code.  
It processes each file, builds an **AST (Abstract Syntax Tree)**, and runs plugins against the AST nodes.  
Once Bandit finishes scanning, it generates a report highlighting potential vulnerabilities.

Bandit was originally developed within the OpenStack Security Project and later rehomed to PyCQA.

![Bandit Example Screen Shot](https://raw.githubusercontent.com/pycqa/bandit/main/bandit-terminal.png)

---

## ✨ Features

- Scans Python code for security issues
- Provides a configurable set of rules and plugins
- Supports multiple output formats (JSON, HTML, CSV, YAML, etc.)
- Easy integration into CI/CD pipelines
- Can be run locally or as a container image

---

## 🛠️ How It Was Created and How It Works

Bandit was developed to automate secure code review in Python projects.

### 🔹 1. AST Parsing
- Bandit uses Python’s built-in `ast` module to parse `.py` files into Abstract Syntax Trees.
- The AST represents your code as a tree of nodes (functions, imports, assignments, etc).

### 🔹 2. Plugin Architecture
- Each security check is implemented as a **plugin** (a Python function).
- Plugins examine AST nodes for known issues (e.g., usage of `eval`, insecure hash functions).
- You can write your own plugins.

### 🔹 3. Processing Workflow
- For each file:
  - Build the AST.
  - Run each plugin on relevant nodes.
  - Collect findings into a report.
- Findings are categorized by severity and confidence.

### 🔹 4. Filtering and Reporting
- After scanning, results are filtered according to:
  - Severity level (low/medium/high)
  - Confidence level (low/medium/high)
- Output can be formatted in JSON, CSV, YAML, or plain text.

### 🔹 5. Extensibility
- Configuration files and command-line options control:
  - Which rules are enabled
  - Which files are excluded
  - Output format

Features
--------

- Scans Python code for security issues
- Provides a configurable set of rules and plugins
- Supports multiple output formats (JSON, HTML, CSV, YAML, etc.)
- Easy integration into CI/CD pipelines
- Can be run locally or as a container image

Show Your Style
---------------

.. image:: https://img.shields.io/badge/security-bandit-yellow.svg
    :target: https://github.com/PyCQA/bandit
    :alt: Security Status

Use our badge in your project's README!

using Markdown:

    [![security: bandit](https://img.shields.io/badge/security-bandit-yellow.svg)](https://github.com/PyCQA/bandit)

using reStructuredText:

    .. image:: https://img.shields.io/badge/security-bandit-yellow.svg
        :target: https://github.com/PyCQA/bandit
        :alt: Security Status

Installation
------------

You can install Bandit using pip:

.. code-block:: console

    pip install bandit

Alternatively, install from source:

.. code-block:: console

    git clone https://github.com/PyCQA/bandit.git
    cd bandit
    python -m pip install .

Or use the Docker image:

.. code-block:: console

    docker pull ghcr.io/pycqa/bandit/bandit

Quick Start
-----------

To scan a Python project:

.. code-block:: console

    bandit -r path/to/your/project

Basic usage examples:

- Scan a single file:

  .. code-block:: console

      bandit my_script.py

- Generate a JSON report:

  .. code-block:: console

      bandit -r my_project -f json -o report.json

- Skip certain tests:

  .. code-block:: console

      bandit -r my_project -s B101,B102

Configuration
-------------

Bandit can be customized via configuration files or command-line options:

- **.bandit**: A project-specific configuration file
- **--exclude**: Exclude directories or files
- **--ini**: Specify a configuration file
- **--confidence-level**: Filter findings by confidence
- **--severity-level**: Filter findings by severity

Example:

.. code-block:: console

    bandit -r . --exclude tests --confidence-level high --severity-level medium

References
----------

- Python AST module documentation: https://docs.python.org/3/library/ast.html
- Green Tree Snakes - the missing Python AST docs: https://greentreesnakes.readthedocs.org/en/latest/
- AST node reference: https://greentreesnakes.readthedocs.org/en/latest/nodes.html

Container Images
----------------

Bandit is available as a container image built within the Bandit repository using GitHub Actions. The image is available on GHCR:

.. code-block:: console

    docker pull ghcr.io/pycqa/bandit/bandit

Supported architectures:

* amd64
* arm64
* armv7
* armv8

To pull a specific architecture:

.. code-block:: console

    docker pull --platform=<architecture> ghcr.io/pycqa/bandit/bandit:latest

Every image is signed with sigstore cosign. You can verify it:

.. code-block:: console

    cosign verify ghcr.io/pycqa/bandit/bandit:latest \
      --certificate-identity https://github.com/pycqa/bandit/.github/workflows/build-publish-image.yml@refs/tags/<version> \
      --certificate-oidc-issuer https://token.actions.githubusercontent.com

Where `<version>` is the release version of Bandit.

Community and Contributions
---------------------------

We welcome contributions! To get started:

1. Read the [contributing guide](https://github.com/PyCQA/bandit/blob/main/CONTRIBUTING.md).
2. Check open issues and discuss improvements.
3. Submit pull requests with clear descriptions.

For questions or support:

- GitHub Issues: https://github.com/PyCQA/bandit/issues
- Discussions: https://github.com/PyCQA/bandit/discussions
- PyCQA community: https://pycqa.github.io/



