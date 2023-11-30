PYTHON := $(shell which python 2>/dev/null)

## Runs all Python checks
python/check: python/fmt python/lint python/test
	@echo "Checking all python code"

## Lint Python code
python/lint: python/typecheck
	find . -type f -name "*.py" | xargs -n 1 flake8

## Typecheck Python code
python/typecheck:
	find . -type f -name "*.py" | xargs -n 1 mypy

## Run Python unit tests
python/test:
	@echo "Testing python code"

## Format Python code
python/fmt:
	@echo "Formatting python code"

## Install Python dependencies with Poetry
python/install:
	@echo "Installing python dependencies"
