HELM_PLATFORM ?= $(OS)-amd64
HELM ?= helm
HELM_REPO_PATH ?= ./$(REPO_NAME)
APP_NAME ?= $(REPO_NAME)
APP_ENV ?= dev
APP_NAMESPACE ?= $(REPO_NAME)

## Upgrade installed helm chart
helm/upgrade:
	@$(HELM) secrets upgrade \
		--install \
		--namespace $(APP_NAMESPACE) \
		--values $(HELM_REPO_PATH)/values.yaml \
		--values $(HELM_REPO_PATH)/values.$(APP_ENV).yaml \
		--set imageTag=$(VERSION) \
		--set appEnv=$(APP_ENV) \
		--wait \
		--timeout=10m \
		$(APP_NAME) \
		$(HELM_REPO_PATH)