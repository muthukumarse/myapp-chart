## Connect GKE to deploy helm chart manually
- Assume that, you have kubectl CLI installed
- get the kubeconfig standard way
  - `gcloud container clusters get-credentials silent-oxygen-376712-gke --region asia-southeast1`
- Check you able to run below command to check the nodes created above
  - `kubectl get nodes`
  - `kubectl get pods -A`
  ![GKE Connection](./evidence/connect-gke.png)

- Deploy Helm chart manaully to Test
![Helm Install](./evidence/deploy-helm-chart-manually.png)

- Check the Deployment over Google Console
![Deployment](./evidence/connect-gke.png)

- Do port-forward to check the Service
  ```
  gcloud container clusters get-credentials silent-oxygen-376712-gke --region asia-southeast1 --project silent-oxygen-376712 \
  && kubectl port-forward $(kubectl get pod --selector="app=myapp" --output jsonpath='{.items[0].metadata.name}') 8080:8080
  ```
  ![Port Forward](./evidence/port-forward.png)

- Browse in local
![Test the Site](./evidence/browse-site.png)

- Updated `tag` in [values.yaml](./values.yaml) to Test the change.

## Over CD (Github Action)
- 