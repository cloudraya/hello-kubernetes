# Hello Kubernetes!

### How to apply the helm chart

Deploy the `hello-kubernetes` app into the `hello-kubernetes` namespace with an "I just deployed this on Kubernetes!" message. The app is exposed via a public Load Balancer on port 80 by default - note that a LoadBalancer service typically only works in cloud provider based Kubernetes offerings.

```bash
helm install --create-namespace --namespace hello-kubernetes custom-message ./hello-kubernetes \
  --set message="I just deployed this on Kubernetes!"

# get the LoadBalancer ip address.
kubectl get svc hello-kubernetes-custom-message -n hello-kubernetes -o 'jsonpath={ .status.loadBalancer.ingress[0].ip }'