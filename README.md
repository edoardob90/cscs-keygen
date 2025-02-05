# cscs-keygen

Python script to automate fetching a new SSH keypair for CSCS infrastructure. It relies on credentials stored in a cloud-based password manager, like Bitwarden or 1Password.

## Setup

### Prerequisites

- Python 3.11+
- One of the following installation methods:
  - [Poetry](https://python-poetry.org/) for development and package management
  - [pipx](https://pypa.github.io/pipx/) for isolated system-wide installation
  - pip for traditional Python package installation
- An account with a supported password manager. Currently: [Bitwarden](https://bitwarden.com), [1Password](https://1password.com/)
  - The password manager must be configured to store the following information:
    - The username of your CSCS account
    - The password of your CSCS account
    - The configured TOPT secret of your CSCS account
- The command-line interface (CLI) of the password manager of your choice:
  - [Bitwarden](https://bitwarden.com/help/article/cli/)
  - [1Password](https://support.1password.com/command-line-getting-started/)
- (optional) A virtual environment with `venv` or `pipenv` (or any other similar utility of your choice)

> [!NOTE]
> Bitwarden's free plan does **not** include the option to store TOTP secrets. You will need to upgrade to a [paid plan](https://bitwarden.com/pricing/) to use this script with Bitwarden.

## Installation

### Using pipx (recommended for users)

For a clean, isolated installation that's available system-wide:

```bash
pipx install git+https://github.com/empa-scientific-it/cscs-keygen.git
```

To upgrade an existing installation:
```bash
pipx upgrade cscs-keygen
```

### Using Poetry (recommended for developers)

1. Clone this repository:
```bash
git clone https://github.com/empa-scientific-it/cscs-keygen.git
cd cscs-keygen
```

2. Install dependencies and the package:
```bash
poetry install
```

3. Activate the virtual environment:
```bash
poetry shell
```

> [!WARNING]
> [Since Poetry **v2.0.0**](https://python-poetry.org/docs/managing-environments/#activating-the-environment), the command `poetry shell` has been moved to an [optional plugin](https://github.com/python-poetry/poetry-plugin-shell). You can either install the plugin or use `eval $(poetry env activate)` (Bash/Zsh) or `eval (poetry env activate)` (Fish)

### Using pip

If you prefer using pip, you can install from a requirements.txt file:

```bash
# Create and activate a virtual environment (optional but recommended)
python -m venv .venv
source .venv/bin/activate  # On Windows, use `.venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt
```

## Usage

Using pipx installation:
```bash
cscs-keygen --help
```

Using Poetry:
```bash
# Inside Poetry shell
cscs-keygen --help

# Or without activating the shell
poetry run cscs-keygen --help
```

Using pip:
```bash
cscs-keygen --help
```

For more details, check out the [docs](https://github.com/empa-scientific-it/cscs-keygen/wiki) (🚧 WIP) of this project.

## Development

To set up the development environment:

```bash
# Install with development dependencies
poetry install --with dev

# Run tests
poetry run pytest

# Run linting/formatting
poetry run ruff check .
poetry run ruff format .
```

## TODO
- [ ] Add support for KeepassXC via the official CLI
