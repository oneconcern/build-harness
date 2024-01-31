PYTHON := $(shell which python 2>/dev/null)
POETRY := $(shell which poetry 2>/dev/null)

PY_FILES ?= $(shell git ls-files "*.py")
PYTEST_FILES ?= tests

## Runs all Python checks
python/check: python/fmt python/lint python/test
	@exit 0

## Lint Python code
python/lint: python/typecheck
	@$(POETRY) run flake8 $(PY_FILES)
	@$(POETRY) run isort --check-only --diff $(PACKAGE)

## Typecheck Python code
python/typecheck:
	@$(POETRY) run mypy $(PY_FILES)

## Run Python unit tests
python/test:
	@$(POETRY) run pytest $(PYTEST_FILES)

## Format Python code
python/fmt:
	@$(POETRY) run isort $(PY_FILES)
	@$(POETRY) run black $(PY_FILES)

## Install Python dependencies with Poetry
python/install:
	$(call assert-set,POETRY)
	$(POETRY) install
