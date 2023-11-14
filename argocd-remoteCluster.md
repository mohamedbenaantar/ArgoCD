## You need to have a remote cluster on any remote environment 
1. Connect ArgoCD to the remote cluster store cluster credentials in Secret Object and add token needed to authenticate to the cluster inside the Secret file
2. Create an ArgoCD application that deploy manifests into the remote cluster
