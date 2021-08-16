# Helm

## Dependency

### Add dependency - Required to download dependencies for chart

#### Get dependencies in https://artifacthub.io/ & copy it to Chart.yaml

helm dependency list - list dependencies in Chart.yaml

helm dependency build helm-chart-test(CHART_NAME) - download the dependencies and it will be available in charts folder

helm dependency update helm-chart-test - update the dependencies and it will be available in charts folder

### Get

helm get hooks <CHART_NAME> - Get list of hooks for the specific chart 

helm get manifest <CHART_NAME> - Get all kubernetes objects in the chart

helm get notes <CHART_NAME> - Print notes available in NOTES.txt

helm get values <CHART_NAME> - Print only user updated (or) defined value

helm get values <CHART_NAME> -a - Print all values defined in k8s yaml file

### History 
helm history <CHART_NAME> - displays all revision happened in helm

helm history <CHART_NAME> -o json -  displays all revision happened in json

helm history <CHART_NAME> --max 1 - Display latest chart with max length

### Install
helm install <release> <CHART_PATH> - install all k8s object in helm

helm install <release> <CHART_PATH> --set service.type=NodePort - set mentioned property & install it. This changes won't be updated in Values (or) Chart yaml files

helm install bitnami/redis --version 14.8.8 --repo https://charts.bitnami.com/bitnami - Install 3rd party repo. Get details from https://artifacthub.io/

helm install my-app --debug --dry-run <HELM_FOLDER> - It generates template

### Lint
helm lint ./helm-chart-test/ - Validate helm template

helm lint helm-chart-test/ --strict - To validate & show warning if any.

### List
helm ls -h - List all commands in ls

helm list (or) helm ls - List all installed Charts in current namespaces.

helm ls --all-namespaces - List installed charts in all namespaces

helm ls --all-namespaces --max 1 - Display latest chart with max length

helm ls --all-namespaces --max 1 --failes - Display latest chart with max length failed status

### Package
helm package <CHART_PATH> - Package helm chart & save in current directory. It can b pushed to repo.

helm package <CHART_PATH> --destination <PATH> - Save it to specific path

helm package <CHART_PATH> --destination <PATH> --version 0.1 - Save it to specific path with version

### Plugins
https://helm.sh/docs/community/related/

helm plugin install https://github.com/databus23/helm-diff

helm diff upgrade mynginx helm-chart-test/ --values helm-chart-test/values.yaml

### Pull - Pull directly from repo
helm pull redis --version 14.8.8 --repo https://charts.bitnami.com/bitnami - Chart is downloaded as tar

helm pull redis --version 14.8.8 --repo https://charts.bitnami.com/bitnami --untar - Chart is xtracted

helm pull redis --version 14.8.8 --repo https://charts.bitnami.com/bitnami --untar --untardir - Download to specific location.

### Repo - Add repo & specify repo while pulling instead of repo url
helm repo add bitnami https://charts.bitnami.com/bitnami - helm repo add <REPO_NAME> <URL>

helm repo ls

helm install bitnami bitnami/redis --version 14.8.7 - helm install <REPO_NAME> <REPO_NAME>/<APP>

helm repo remove bitnami

### Rollback
helm rollback mynginx 1 - helm rollback <RELEASE> [REVISION]

helm history <RELEASE> - Provides description about rollback info

helm rollback mynginx 1 --force --bo-hooks

### Show
helm show chart helm-chart-test/ - Show info of the chart

### Template
helm template test ./helm-chart/ - helm template <IN> <HCP> --> Apply helm template changes & generate k8s yaml

helm template emp ./helm-chart/ > helm-generated.yaml - helm template <IN> ./<HCP> helm-generated.yaml --> Apply 
helm values, chart.yaml & create actual k8s yaml files is generated to yaml file

### UPGRADE
helm upgrade my-app <CHART_PATH> 

### Helm 3 built in objects
1. Release
2. Charts
3. Files - If we need to add files. Refer template/config.yaml