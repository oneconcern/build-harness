PYTHON := $(shell which python 2>/dev/null)
PACKAGE ?= src
## Runs all Python checks
python/check: python/fmt python/lint python/test
	@echo "Checking all python code"

## Lint Python code
python/lint: python/typecheck
	@flake8 $(PACKAGE)

## Typecheck Python code
python/typecheck:
	@mypy -p $(PACKAGE)

## Run Python unit tests
python/test:
	@echo "Testing python code"

## Format Python code
python/fmt:
	@echo "Formatting python code"

## Install Python dependencies with Poetry
python/install:
	@echo "Installing python dependencies"
