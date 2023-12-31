PYTHON := $(shell which python 2>/dev/null)
POETRY := $(shell which poetry 2>/dev/null)

PACKAGE ?= src
## Runs all Python checks
python/check: python/fmt python/lint python/test
	@exit 0

## Lint Python code
python/lint: python/typecheck
	@flake8 $(PACKAGE)
	@isort --check-only --diff $(PACKAGE)

## Typecheck Python code
python/typecheck:
	@mypy -p $(PACKAGE)

## Run Python unit tests
python/test:
	@pytest -v --log-level=DEBUG --junit-xml=tests/junit/results.xml --cov=$(PACKAGE) --cov-report=html --cov-report=xml --cov-report=term --durations=10 tests/unit

## Format Python code
python/fmt:
	@isort $(PACKAGE)
	@black $(PACKAGE)

## Install Python dependencies with Poetry
python/install:
	$(call assert-set,POETRY)
	$(POETRY) install
