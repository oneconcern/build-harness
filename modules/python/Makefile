PYTHON := $(shell which python 2>/dev/null)
POETRY := $(shell which poetry 2>/dev/null)

PY_FILES ?= $(shell git ls-files "*.py")
PYTEST_FILES ?= tests

## Runs all Python checks
python/check: python/fmt python/lint python/test
	@exit 0

## Lint Python code
python/lint: python/typecheck
	@flake8 $(PY_FILES)
	@isort --check-only --diff $(PACKAGE)

## Typecheck Python code
python/typecheck:
	@mypy $(PY_FILES)

## Run Python unit tests
python/test:
	@pytest $(PYTEST_FILES)

## Format Python code
python/fmt:
	@isort $(PY_FILES)
	@black $(PY_FILES)

## Install Python dependencies with Poetry
python/install:
	@$(call assert-set,POETRY)
	@$(POETRY) install
