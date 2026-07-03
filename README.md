# NEX

**NEX** is a terminal-based assistant built with [Rich](https://rich.readthedocs.io/). It provides an AI-powered, context-aware command-line interface that integrates seamlessly with your local environment and LLM backends.

## Quickstart (Developer Setup)

### 1. Clone the repository

```bash
git clone git@github.com:ChipNexus/nex.git
cd nex
```

### 2. Set up dependencies

Make sure you have [`uv`](https://docs.astral.sh/uv/getting-started/installation/) installed.

```bash
uv venv
uv sync
```

### 3. Install the package in editable mode

```bash
uv pip install -e .
```

### 4. Configure environment variables

Create a `.env` file in the project root with your API settings:

```bash
export LLM_PROVIDER=...
export LLM_PROVIDER_REGION=...
export LLM_API_KEY=...
export LLM_MODEL=...
```

> The app automatically loads `.env` values using **pydantic-settings**.

## Running NEX (`dev` mode)

Run NEX from the terminal:

```bash
uv run python -m nex
```

Or, if installed as a console script:

```bash
uv run nex
```

## Packaging Instructions

Make sure dependencies (including workspace MCPs) are installed:

```bash
uv sync
```

To build executable in onedirectory mode (good for debugging + faster startup time)

```bash
uv run pyarmor gen --pack run_nex_onedir.spec -r run_nex.py src
```

To build in onefile mode (for distribution)

```bash
uv run pyarmor gen --pack run_nex_onefile.spec -r run_nex.py src
```

Note that onefile mode is essentially a compressed archive of the onedirectory build, wrapped in an executable file.  When run, it first unpacks to a tmp directory. This can make initial application launch slow. As of 28JAN2026, it takes roughly 9 seconds.
