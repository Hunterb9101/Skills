---
name: contribute-python
description: "Implement Python code in the repository"
---
# Contribute Python

## Overview
Defines a repeatable harness to ensure quality python code is written to the repository.

## Definitions
- **Feature**: A single cohesive unit of functionality that can be described in a single sentence.

## Workflow
### Setup
1. This skill has been written to handle the implementation of a single feature.
  - If there are multiple features, or the feature is not coherently defined, stop.
2. Activate the virtual environment, located at `.venv`. This may be at either the repository root, or per each project in a monorepo.
  - If a `.venv` is not available, stop.

### Implement
1. Identify the key functionality and edge cases of the implementation.
2. Design and implement the tests following the [Testing Conventions](#testing).
3. Iteratively implement code to make the tests pass per [Conventions](#conventions).
  - Note that the repository may not follow all of these rules. Treat out-of-scope violated conventions as transitional architecture, and avoid expanding the violated convention further.


### Validate
1. Run `mypy .` against BOTH the `src` folder and `tests`.
2. Run `ruff check` to ensure that the code has no linting issues.
3. Run `pytest tests/` to ensure that all tests pass.

# Conventions

## Separation of Concerns

- `main.py` files are the preferred orchestration boundary for I/O and configuration concerns.
  - Avoid importing `<package_slug>.config` outside of main files.
  - Avoid I/O outside of `main.py` files or explicit I/O utility modules.

## Docstrings

- Utilize numpy-style docstrings.

## Data Structures

- Use Pydantic at external boundaries such as config, CLI input, and Optuna trial parameters. Prefer parsing flexible raw shapes into named internal contracts with targeted validation.
- Use dataclasses for internal runtime structures that are already constructed by trusted code.
- Avoid passing anonymous `dict[str, Any]` through multiple layers. If a flexible payload is needed for fast experiments or third-party kwargs, put it behind a named field such as `params`, `model_params`, or `extras`.
- Validate project-owned concepts explicitly, such as `scale`, holdout behavior, calibration flags, and required fitted artifacts. Let third-party libraries validate their own constructor-specific parameters.
