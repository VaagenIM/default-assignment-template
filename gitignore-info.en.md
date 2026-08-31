# Gitignore Notes

This repository includes a `.gitignore` with sensible defaults for Python, `uv`, Node.js, IDEs, and common development tools.

You normally should not need to modify it.

## Environment variables / secrets

`.env` and other `.env.*` files are ignored by default.

`.env.example`, `.env.sample`, and `.env.template` are allowed.

Use these for documenting which environment variables are required:

```text
.env.example    # Commit this
.env            # Do not commit this
````

Do not put real passwords, API keys, tokens, or other secrets in `.env.example`.

If you **specifically need to submit a `.env` file as part of an assignment**, you can force Git to add it:

```bash
git add -f .env
```

Only do this if you have been explicitly asked to submit the file and it does not contain sensitive information.

## `uv`

`uv.lock` is **not** ignored and should normally be committed.

`.venv/` is ignored.

Typical project:

```text
pyproject.toml    # Commit
uv.lock           # Commit
.venv/            # Do not commit
```

## IDEs

IDE configuration is ignored:

```text
.idea/
.vscode/
```

You can use PyCharm, VS Code, Cursor, etc. without committing their local configuration.

## Python caches

Generated Python files are ignored:

```text
__pycache__/
*.pyc
.pytest_cache/
.ruff_cache/
.mypy_cache/
.pyright/
```

You do not need to manually delete these before committing.

## Jupyter

Notebook files (`.ipynb`) are **not** ignored and can be committed.

Only generated Jupyter checkpoint files are ignored:

```text
.ipynb_checkpoints/
```

## Node.js

If you use Node.js/JavaScript/TypeScript:

```text
node_modules/
```

is ignored.

Commit files such as:

```text
package.json
package-lock.json
```

but do not commit `node_modules/`.

## Build files

Common generated directories such as these are ignored:

```text
build/
dist/
out/
target/
tmp/
temp/
```

## Local databases

Common local database files are ignored:

```text
*.db
*.sqlite
*.sqlite3
```

Files such as `.csv`, `.json`, and `.yaml` are **not** globally ignored, since they may be part of an assignment.

## Logs / temporary files

Common logs and temporary files are ignored:

```text
*.log
*.tmp
*.bak
*.swp
```

## Why is Git ignoring my file?

If a file doesn't appear in:

```bash
git status
```

you can check why with:

```bash
git check-ignore -v path/to/file
```

For example:

```bash
git check-ignore -v .env
```

## Important

`.gitignore` does not remove files that have already been committed.

If you accidentally commit a password, API key, or other secret, **do not assume that simply deleting the file fixes the problem**. Rotate/revoke the secret immediately.

For normal coursework, you can generally follow this rule:

```text
Commit:
  Source code
  README/documentation
  pyproject.toml
  uv.lock
  Tests
  Notebooks
  Assignment data/files

Don't commit:
  .env
  .venv/
  __pycache__/
  .pytest_cache/
  .ruff_cache/
  .idea/
  .vscode/
  node_modules/
  Build output
  Logs
  Local databases
```
