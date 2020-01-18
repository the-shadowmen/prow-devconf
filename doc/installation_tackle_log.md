# Tackle Log

- Installation Prow from Tackle: https://pastebin.com/2kG0ZKJG
```
λ test-infra git:(master) bazel run //prow/cmd/tackle      
DEBUG: /home/jparrill/.cache/bazel/_bazel_jparrill/712a15c28bf8c295728606eaacac6899/external/bazel_toolchains/rules/rbe_repo/version_check.bzl:68:9: 
Current running Bazel is ahead of bazel-toolchains repo. Please update your pin to bazel-toolchains repo in your WORKSPACE file.
DEBUG: /home/jparrill/.cache/bazel/_bazel_jparrill/712a15c28bf8c295728606eaacac6899/external/bazel_toolchains/rules/rbe_repo/checked_in.bzl:125:9: rbe_default not using checked in configs; Bazel version 1.2.1 was picked/selected but no checked in config was found in map {"0.20.0": ["8.0.0"], "0.21.0": ["8.0.0"], "0.22.0": ["8.0.0", "9.0.0"], "0.23.0": ["8.0.0", "9.0.0"], "0.23.1": ["8.0.0", "9.0.0"], "0.23.2": ["9.0.0"], "0.24.0": ["9.0.0"], "0.24.1": ["9.0.0"], "0.25.0": ["9.0.0"], "0.25.1": ["9.0.0"], "0.25.2": ["9.0.0"], "0.26.0": ["9.0.0"], "0.26.1": ["9.0.0"], "0.27.0": ["9.0.0"], "0.27.1": ["9.0.0"], "0.28.0": ["9.0.0"], "0.28.1": ["9.0.0"], "0.29.0": ["9.0.0"], "0.29.1": ["9.0.0", "10.0.0"], "1.0.0": ["9.0.0", "10.0.0"]}
DEBUG: /home/jparrill/.cache/bazel/_bazel_jparrill/712a15c28bf8c295728606eaacac6899/external/bazel_gazelle/internal/go_repository.bzl:182:13: gazelle: gazelle: finding module path for import github.com/google/mako/clients/proto/analyzers/threshold_analyzer_go_proto: exit status 1: can't load package: package github.com/google/mako/clients/proto/analyzers/threshold_analyzer_go_proto: module github.com/google/mako@latest (v0.2.0-rc1) found, but does not contain package github.com/google/mako/clients/proto/analyzers/threshold_analyzer_go_proto
DEBUG: /home/jparrill/.cache/bazel/_bazel_jparrill/712a15c28bf8c295728606eaacac6899/external/bazel_gazelle/internal/go_repository.bzl:182:13: gazelle: gazelle: finding module path for import testdata.kb.io/api/v1: exit status 1: can't load package: package testdata.kb.io/api/v1: cannot find module providing package testdata.kb.io/api/v1
gazelle: finding module path for import testdata.kb.io/api/v2: exit status 1: can't load package: package testdata.kb.io/api/v2: cannot find module providing package testdata.kb.io/api/v2
gazelle: finding module path for import testdata.kb.io/api/v3: exit status 1: can't load package: package testdata.kb.io/api/v3: cannot find module providing package testdata.kb.io/api/v3
INFO: Analyzed target //prow/cmd/tackle:tackle (1 packages loaded, 385 targets configured).
INFO: Found 1 target...
Target //prow/cmd/tackle:tackle up-to-date:
  bazel-bin/prow/cmd/tackle/linux_amd64_stripped/tackle
INFO: Elapsed time: 2.060s, Critical Path: 0.31s
INFO: 0 processes.
INFO: Build completed successfully, 1 total action
INFO: Build completed successfully, 1 total action
Existing kubernetes contexts:
  ...
  ...
  ...
  ...
Choose context or [create new]: 
Getting active GCP account...Your active configuration is: [jparrill]
jparrill@redhat.com
Projects available to jparrill@redhat.com:
  ...
  ...
  ...
  ...
  ... 
Wow, that is a lot of projects!
Type the name of any project, including ones not in this truncated list
Your active configuration is: [jparrill]
Select project [cnvlab-xxxxxx]: 
Ensuring jparrill@redhat.com has access to cnvlab-xxxxxx...
Existing GKE clusters in cnvlab-xxxxxx:
  No clusters
Get credentials for existing cluster or [create new]: 
Cluster name [prow]: parri-prow
Your active configuration is: [jparrill]
(unset)
Available zones:
  ...
  ...
  ...
  ...
Type the name of any zone, including ones not in this truncated list
Select zone [us-east1-b]: europe-west4-a
WARNING: If `--issue-client-certificate` is specified but `--enable-basic-auth` or `--username` is not, our API will treat that as `--no-enable-basic-auth`.
WARNING: Currently VPC-native is not the default mode during cluster creation. In the future, this will become the default mode and can be disabled using `--no-enable-ip-alias` flag. Use `--[no-]enable-ip-alias` flag to suppress this warning.
WARNING: Newly created clusters and node-pools will have node auto-upgrade enabled by default. This can be disabled using the `--no-enable-autoupgrade` flag.
WARNING: Starting in 1.12, default node pools in new clusters will have their legacy Compute Engine instance metadata endpoints disabled by default. To create a cluster with legacy instance metadata endpoints disabled in the default node pool, run `clusters create` with the flag `--metadata disable-legacy-endpoints=true`.
WARNING: Your Pod address range (`--cluster-ipv4-cidr`) can accommodate at most 1008 node(s). 
This will enable the autorepair feature for nodes. Please see https://cloud.google.com/kubernetes-engine/docs/node-auto-repair for more information on node autorepairs.
Creating cluster parri-prow in europe-west4-a... Cluster is being health-checked (master is healthy)...done.                                                                       
Created [https://container.googleapis.com/v1/projects/cnvlab-xxxxxx/zones/europe-west4-a/clusters/parri-prow].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/europe-west4-a/parri-prow?project=cnvlab-xxxxxx
kubeconfig entry generated for parri-prow.
NAME        LOCATION        MASTER_VERSION  MASTER_IP      MACHINE_TYPE   NODE_VERSION    NUM_NODES  STATUS
parri-prow  europe-west4-a  1.13.11-gke.14  xx.xxx.xxx.xxx  n1-standard-1  1.13.11-gke.14  3          RUNNING
Applying admin role bindings (to create RBAC rules)...
Your active configuration is: [jparrill]
clusterrolebinding.rbac.authorization.k8s.io/prow-admin created
Deploying prow...
Apply starter.yaml from [github upstream]: 
Loading from https://raw.githubusercontent.com/kubernetes/test-infra/master/prow/cluster/starter.yaml
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
configmap/plugins configured
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
configmap/config configured
customresourcedefinition.apiextensions.k8s.io/prowjobs.prow.k8s.io created
deployment.apps/hook created
service/hook created
deployment.apps/plank created
deployment.apps/sinker created
deployment.apps/deck created
service/deck created
deployment.apps/horologium created
deployment.apps/tide created
service/tide created
ingress.extensions/ing created
deployment.apps/statusreconciler created
namespace/test-pods created
serviceaccount/deck created
rolebinding.rbac.authorization.k8s.io/deck created
rolebinding.rbac.authorization.k8s.io/deck created
role.rbac.authorization.k8s.io/deck created
role.rbac.authorization.k8s.io/deck created
serviceaccount/horologium created
role.rbac.authorization.k8s.io/horologium created
rolebinding.rbac.authorization.k8s.io/horologium created
serviceaccount/plank created
role.rbac.authorization.k8s.io/plank created
role.rbac.authorization.k8s.io/plank created
rolebinding.rbac.authorization.k8s.io/plank created
rolebinding.rbac.authorization.k8s.io/plank created
serviceaccount/sinker created
role.rbac.authorization.k8s.io/sinker created
role.rbac.authorization.k8s.io/sinker created
rolebinding.rbac.authorization.k8s.io/sinker created
rolebinding.rbac.authorization.k8s.io/sinker created
serviceaccount/hook created
role.rbac.authorization.k8s.io/hook created
rolebinding.rbac.authorization.k8s.io/hook created
serviceaccount/tide created
role.rbac.authorization.k8s.io/tide created
rolebinding.rbac.authorization.k8s.io/tide created
serviceaccount/statusreconciler created
role.rbac.authorization.k8s.io/statusreconciler created
rolebinding.rbac.authorization.k8s.io/statusreconciler created
Checking github credentials...
Store your GitHub token in a file e.g. echo $TOKEN > /path/to/github/token
Input /path/to/github/token to upload into cluster: /home/jparrill/projects/test-infra/.token
INFO[5811] User()                                        client=github
Prow will act as janitor-bot on github
Applying github token into oauth-token secret...secret/oauth-token created
Ensuring hmac secret exists at hmac-token...INFO[5813] Creating new hmac-token secret with random data... 
exists
Looking for prow's hook ingress URL... http://xx.xxx.xxx.xxx/hook
Enable which org or org/repo [quit]:     
 Enjoy your gke_cnvlab-209908_europe-west4-a_parri-prow prow instance at: http://xx.xxx.xxx.xxx/!
```
