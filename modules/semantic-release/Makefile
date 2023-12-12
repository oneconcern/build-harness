RELEASE := $(shell which semantic-release 2>/dev/null)

## Run semantic-release to calculate the next version, generate changelog, and push a new release
semantic-release/version:
	$(call assert-set,RELEASE)
	$(RELEASE) --vv version