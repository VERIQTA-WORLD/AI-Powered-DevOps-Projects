# ==============================================================================
# Project 001 — AI-Powered CI Failure Triage Engine
# Makefile
# ==============================================================================
#
# Common development commands for Project 001.
#
# Start with:
#
#   make help
#
# This Makefile provides shortcuts for local setup, validation, testing,
# evaluation, demonstration, API execution, Docker workflows, and cleanup.
#
# The scripts/ directory remains the home for multi-step project automation.
# Make targets should delegate to those scripts where appropriate rather than
# duplicating complex shell logic here.
#
# ==============================================================================


.DEFAULT_GOAL := help

SHELL := /bin/bash

PYTHON ?= python3
VENV ?= .venv

VENV_BIN := $(VENV)/bin
PYTHON_BIN := $(VENV_BIN)/python
PIP := $(PYTHON_BIN) -m pip
PYTEST := $(PYTHON_BIN) -m pytest
RUFF := $(VENV_BIN)/ruff
MYPY := $(VENV_BIN)/mypy
UVICORN := $(VENV_BIN)/uvicorn

PACKAGE := ci_triage
SRC_DIR := src
TEST_DIR := tests
EVALUATION_DIR := evaluations
SCRIPTS_DIR := scripts
DOCKER_DIR := docker

ENV_FILE := .env
ENV_EXAMPLE := .env.example

API_HOST ?= 0.0.0.0
API_PORT ?= 8000

DOCKER_COMPOSE_FILE := $(DOCKER_DIR)/docker-compose.yml


# ==============================================================================
# PHONY TARGETS
# ==============================================================================

.PHONY: \
	help \
	setup \
	venv \
	install \
	install-dev \
	env \
	check-env \
	run \
	api \
	demo \
	test \
	test-unit \
	test-integration \
	test-security \
	test-acceptance \
	test-cov \
	evaluate \
	lint \
	format \
	format-check \
	type-check \
	check \
	docker-build \
	docker-up \
	docker-down \
	docker-logs \
	docker-test \
	clean \
	clean-python \
	clean-test \
	clean-coverage \
	clean-build \
	clean-evaluations \
	clean-all


# ==============================================================================
# HELP
# ==============================================================================

help: ## Show available Makefile commands
	@echo ""
	@echo "Project 001 — AI-Powered CI Failure Triage Engine"
	@echo ""
	@echo "Usage:"
	@echo "  make <target>"
	@echo ""
	@echo "Setup:"
	@echo "  make setup              Prepare the local development environment"
	@echo "  make venv               Create the Python virtual environment"
	@echo "  make install            Install the project"
	@echo "  make install-dev        Install project and development dependencies"
	@echo "  make env                Create .env from .env.example if missing"
	@echo "  make check-env          Validate the local environment"
	@echo ""
	@echo "Run:"
	@echo "  make run                Run the project CLI"
	@echo "  make api                Start the local API"
	@echo "  make demo               Run the project demonstration"
	@echo ""
	@echo "Testing:"
	@echo "  make test               Run the complete automated test suite"
	@echo "  make test-unit          Run unit tests"
	@echo "  make test-integration   Run integration tests"
	@echo "  make test-security      Run security tests"
	@echo "  make test-acceptance    Run acceptance tests"
	@echo "  make test-cov           Run tests with coverage"
	@echo ""
	@echo "AI Evaluation:"
	@echo "  make evaluate           Run the AI evaluation workflow"
	@echo ""
	@echo "Quality:"
	@echo "  make lint               Run Ruff lint checks"
	@echo "  make format             Format Python code with Ruff"
	@echo "  make format-check       Check formatting without modifying files"
	@echo "  make type-check         Run mypy static type checking"
	@echo "  make check              Run lint, format, types, and tests"
	@echo ""
	@echo "Docker:"
	@echo "  make docker-build       Build the project container image"
	@echo "  make docker-up          Start the project with Docker Compose"
	@echo "  make docker-down        Stop the Docker Compose environment"
	@echo "  make docker-logs        Follow Docker Compose logs"
	@echo "  make docker-test        Run tests in the Docker environment"
	@echo ""
	@echo "Cleanup:"
	@echo "  make clean              Run the project cleanup script"
	@echo "  make clean-python       Remove Python cache files"
	@echo "  make clean-test         Remove test caches"
	@echo "  make clean-coverage     Remove coverage artifacts"
	@echo "  make clean-build        Remove Python build artifacts"
	@echo "  make clean-evaluations  Remove generated evaluation results"
	@echo "  make clean-all          Remove generated local development artifacts"
	@echo ""


# ==============================================================================
# SETUP
# ==============================================================================

setup: ## Prepare the local development environment
	@bash $(SCRIPTS_DIR)/setup.sh


venv: ## Create the Python virtual environment
	@if [ ! -d "$(VENV)" ]; then \
		echo "Creating virtual environment at $(VENV)..."; \
		$(PYTHON) -m venv $(VENV); \
		echo "Virtual environment created."; \
	else \
		echo "Virtual environment already exists at $(VENV)."; \
	fi


install: venv ## Install the project
	@echo "Upgrading pip..."
	@$(PIP) install --upgrade pip
	@echo "Installing Project 001..."
	@$(PIP) install -e .
	@echo "Project installation complete."


install-dev: venv ## Install project and development dependencies
	@echo "Upgrading pip..."
	@$(PIP) install --upgrade pip
	@echo "Installing Project 001 with development dependencies..."
	@$(PIP) install -e ".[dev]"
	@echo "Development installation complete."


env: ## Create .env from .env.example if .env does not exist
	@if [ ! -f "$(ENV_EXAMPLE)" ]; then \
		echo "ERROR: $(ENV_EXAMPLE) was not found."; \
		exit 1; \
	fi
	@if [ -f "$(ENV_FILE)" ]; then \
		echo "$(ENV_FILE) already exists. Leaving it unchanged."; \
	else \
		cp $(ENV_EXAMPLE) $(ENV_FILE); \
		echo "Created $(ENV_FILE) from $(ENV_EXAMPLE)."; \
		echo "Review $(ENV_FILE) before running provider-dependent features."; \
	fi


check-env: ## Validate the local project environment
	@bash $(SCRIPTS_DIR)/check-environment.sh


# ==============================================================================
# APPLICATION
# ==============================================================================

run: ## Run the Project 001 CLI
	@if [ ! -x "$(PYTHON_BIN)" ]; then \
		echo "ERROR: Virtual environment not found."; \
		echo "Run 'make install-dev' first."; \
		exit 1; \
	fi
	@$(PYTHON_BIN) -m $(PACKAGE).main


api: ## Start the local API
	@if [ ! -x "$(UVICORN)" ]; then \
		echo "ERROR: Uvicorn is not installed in $(VENV)."; \
		echo "Run 'make install-dev' first."; \
		exit 1; \
	fi
	@$(UVICORN) api.app:app \
		--host $(API_HOST) \
		--port $(API_PORT)


demo: ## Run the project demonstration workflow
	@bash $(SCRIPTS_DIR)/run-demo.sh


# ==============================================================================
# TESTING
# ==============================================================================

test: ## Run the complete automated test suite
	@bash $(SCRIPTS_DIR)/run-tests.sh


test-unit: ## Run unit tests
	@$(PYTEST) $(TEST_DIR)/unit -m unit


test-integration: ## Run integration tests
	@$(PYTEST) $(TEST_DIR)/integration -m integration


test-security: ## Run security tests
	@$(PYTEST) $(TEST_DIR)/security -m security


test-acceptance: ## Run acceptance tests
	@$(PYTEST) $(TEST_DIR)/acceptance -m acceptance


test-cov: ## Run all tests with branch coverage
	@$(PYTEST) \
		$(TEST_DIR) \
		--cov=$(PACKAGE) \
		--cov-branch \
		--cov-report=term-missing \
		--cov-report=html \
		--cov-report=xml


# ==============================================================================
# AI EVALUATION
# ==============================================================================

evaluate: ## Run the AI evaluation workflow
	@bash $(SCRIPTS_DIR)/run-evaluations.sh


# ==============================================================================
# CODE QUALITY
# ==============================================================================

lint: ## Run Ruff lint checks
	@$(RUFF) check $(SRC_DIR) $(TEST_DIR) api $(EVALUATION_DIR)


format: ## Format Python code with Ruff
	@$(RUFF) format $(SRC_DIR) $(TEST_DIR) api $(EVALUATION_DIR)


format-check: ## Check formatting without changing files
	@$(RUFF) format --check $(SRC_DIR) $(TEST_DIR) api $(EVALUATION_DIR)


type-check: ## Run mypy static type checking
	@$(MYPY) $(SRC_DIR) api


check: lint format-check type-check test ## Run the main local quality gates
	@echo ""
	@echo "Project checks completed successfully."


# ==============================================================================
# DOCKER
# ==============================================================================

docker-build: ## Build the project container image
	@docker compose \
		-f $(DOCKER_COMPOSE_FILE) \
		build


docker-up: ## Start the project with Docker Compose
	@docker compose \
		-f $(DOCKER_COMPOSE_FILE) \
		up -d


docker-down: ## Stop the Docker Compose environment
	@docker compose \
		-f $(DOCKER_COMPOSE_FILE) \
		down


docker-logs: ## Follow Docker Compose logs
	@docker compose \
		-f $(DOCKER_COMPOSE_FILE) \
		logs -f


docker-test: ## Run the automated test suite inside the application container
	@docker compose \
		-f $(DOCKER_COMPOSE_FILE) \
		run --rm app \
		python -m pytest tests


# ==============================================================================
# CLEANUP
# ==============================================================================

clean: ## Run the project cleanup script
	@bash $(SCRIPTS_DIR)/cleanup.sh


clean-python: ## Remove Python bytecode and cache files
	@echo "Removing Python cache files..."
	@find . -type d -name "__pycache__" -prune -exec rm -rf {} +
	@find . -type f \( -name "*.pyc" -o -name "*.pyo" \) -delete
	@echo "Python cache cleanup complete."


clean-test: ## Remove test and static-analysis caches
	@echo "Removing test and analysis caches..."
	@rm -rf .pytest_cache
	@rm -rf .mypy_cache
	@rm -rf .ruff_cache
	@rm -rf .hypothesis
	@echo "Test cache cleanup complete."


clean-coverage: ## Remove generated coverage artifacts
	@echo "Removing coverage artifacts..."
	@rm -rf htmlcov
	@rm -f .coverage
	@rm -f .coverage.*
	@rm -f coverage.xml
	@rm -f coverage.json
	@echo "Coverage cleanup complete."


clean-build: ## Remove Python packaging artifacts
	@echo "Removing build artifacts..."
	@rm -rf build
	@rm -rf dist
	@find . -maxdepth 2 -type d -name "*.egg-info" -prune -exec rm -rf {} +
	@echo "Build artifact cleanup complete."


clean-evaluations: ## Remove locally generated AI evaluation results
	@echo "Removing generated evaluation results..."
	@rm -rf evaluation-results
	@rm -rf $(EVALUATION_DIR)/results
	@rm -rf $(EVALUATION_DIR)/output
	@rm -rf $(EVALUATION_DIR)/.results
	@echo "Evaluation cleanup complete."


clean-all: clean-python clean-test clean-coverage clean-build clean-evaluations ## Remove generated local artifacts
	@echo ""
	@echo "Generated local development artifacts removed."
	@echo ""
	@echo "The following are intentionally NOT removed:"
	@echo "  $(ENV_FILE)"
	@echo "  $(VENV)/"
	@echo "  evidence/screenshots/"
	@echo "  evidence/terminal-output/"
	@echo "  evidence/test-results/"
	@echo "  evidence/logs/"
	@echo ""
	@echo "Use scripts/cleanup.sh only after reviewing its documented behavior."
