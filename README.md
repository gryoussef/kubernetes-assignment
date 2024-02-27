# kubernetes-assignment

This repository contains the Kubernetes manifests for deploying my app.

## Deployment

To deploy the app, you need to have `kubectl` installed and configured to connect to your Kubernetes cluster.

Then, run the following command:

```bash
kubectl apply -f ./k8s
```
## Try it

Use `kubectl port-forward svc/my-service 8888:80` and check nginx hello world page in your browser.

## Details

This will create a Deployment, a Service, a Horizontal Pod Autoscaler, a Pod Disruption Budget, a Secret, and a ServiceAccount in your cluster.

The Deployment uses a RollingUpdate strategy with maxUnavailable: 1, ensuring that at least 2 pods are always available during updates.

The Service is of type NodePort, making the app accessible from outside the cluster.

The Horizontal Pod Autoscaler automatically scales the number of pods based on CPU utilization.

The Pod Disruption Budget ensures that at least 2 pods will remain available during voluntary disruptions.

The Secret contains the API key for the app, which is passed to the app as an environment variable.

The ServiceAccount is used by the Deployment for authorization.

# CI pipeline

I have tried to integrate [Kubescape](https://github.com/kubescape/github-action/blob/main/.github/workflows/example-scan.yaml) but did not work for some reason. it does not work also in their repository. I don't have time to investigate.

