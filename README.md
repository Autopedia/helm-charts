## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

```bash
helm repo add autopedia  https://autopedia.github.io/helm-charts
```

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run 
```
helm search repo autopedia
```  
to see the charts.

To install the labelstudio chart:

```bash
export PROJECT_NAME=my-project
curl https://autopedia.github.io/helm-charts/charts/labelstudio/values.yaml | sed "s/my-project/$PROJECT_NAME/" >  ./values/$PROJECT_NAME.values.yaml
kubectl create namespace labelstudio-$PROJECT_NAME
helm upgrade --install -f values/$PROJECT_NAME.values.yaml labelstudio-$PROJECT_NAME autopedia/labelstudio -n labelstudio-$PROJECT_NAME
```

To uninstall the chart:

```bash
helm delete labelstudio-$PROJECT_NAME -n labelstudio-$PROJECT_NAME
```