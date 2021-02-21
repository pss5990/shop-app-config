Steps To Successfully Install Istio In The Cluster

### Prerequisite
1. A running K8S cluster

### Steps

1. Download istio
<br />
curl -L https://istio.io/downloadIstio | sh -

2. Add it to PATH
<br />
export PATH=$PATH:<istio_directory>/bin

3. Install isito in your cluster. There are other configurations available as well but we have used 'demo' for no.
<br />
istioctl install --set profile=demo -y

4. Label namespace to enable it for automatic sidecar injection.
<br />
kubectl label namespace default istio-injection=enabled

5. Create Istio Gateway for your application to expose the application to the outside world.
<br /> 
kubectl apply -f shop-app-istio-gateway.yaml

<br />
installation guide -> https://istio.io/latest/docs/setup/platform-setup/gke/

### Uninstalling Istio
1. istioctl manifest generate --set profile=demo | kubectl delete --ignore-not-found=true -f -
2. kubectl delete namespace istio-system
3. kubectl label namespace default istio-injection-
