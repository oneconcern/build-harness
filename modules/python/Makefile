PYTHON := $(shell which python 2>/dev/null)
POETRY := $(shell which poetry 2>/dev/null)

PY_FILES ?= $(shell git ls-files "*.py")
PYTEST_FILES ?= tests

## Runs all Python checks
python/check: python/fmt python/lint python/test
	@exit 0

## Lint Python code
python/lint: python/typecheck
	@echo "${GREEN}Running flake8 lint checks${RESET}"
	@flake8 $(PY_FILES)
	@isort --check-only --diff $(PACKAGE)

## Typecheck Python code
python/typecheck:
	@echo "${GREEN}Running mypy typing checks${RESET}"
	@mypy $(PY_FILES)

## Run Python unit tests
python/test:
	@echo "${GREEN}Running python tests${RESET}"
	@pytest $(PYTEST_FILES)

## Format Python code
python/fmt:
	@echo "${GREEN}Running isort auto-format${RESET}"
	@isort $(PY_FILES)
	@echo done
	@echo "${GREEN}Running black auto-format${RESET}"
	@black $(PY_FILES)

## Format Python code
python/check-fmt:
	@echo "${GREEN}Running isort format checks${RESET}"
	@isort --check $(PY_FILES)
	@echo done
	@echo "${GREEN}Running black format checks${RESET}"
	@black --check $(PY_FILES)

## Install Python dependencies with Poetry
python/install:
	@$(call assert-set,POETRY)
	@$(POETRY) install
