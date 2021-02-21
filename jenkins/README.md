Code to prepare GKE cluster

#### What Will We Be Installing ?
1. Jenkins

#### Prerequisite
1. Helm should be installed in your local system. Ensure helm is properly installed by running - helm version.
2. GKE cluster setup.
3. Run the command gcloud container clusters get-credentials *<cluster_name>* --region=*<gke_cluster_region>*

#### Setting Up Jenkins on GKE
1. helm repo add jenkins https://charts.jenkins.io
2. helm repo update
3. helm install *<release_name>* jenkins/jenkins
4. Get your 'admin' user password by running:
   <br />kubectl exec --namespace default -it svc/jenkins -c jenkins -- /bin/cat /run/secrets/chart-admin-password && echo
5. Setup a port forwarding to access jenkins on localhost:8080
  <br />kubectl --namespace default port-forward svc/jenkins 8080:8080
  
  
  
