# These are the usual GKE variables.
PROJECT       ?= cnvlab
ZONE          ?= europe-west4
CLUSTER       ?= parri-prow

.PHONY: update-config update-plugins update-labels get-cluster-credentials

update-config:
	kubectl create configmap -n default config --from-file=config.yaml=config.yaml --dry-run -o yaml | kubectl replace configmap config -f -

update-plugins:
	kubectl create configmap -n default plugins --from-file=plugins.yaml=plugins.yaml --dry-run -o yaml | kubectl replace configmap plugins -f -

update-labels:
	kubectl create configmap -n default label-config --from-file=labels.yaml=labels.yaml --dry-run -o yaml | kubectl replace configmap plugins -f -

get-cluster-credentials:
	gcloud container clusters get-credentials "$(CLUSTER)" --project="$(PROJECT)" --zone="$(ZONE)"
