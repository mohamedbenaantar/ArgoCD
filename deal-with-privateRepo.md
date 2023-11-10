## to deal with a private repo you need to store it's credentials in a normal kubernetes secret
using ssh private key

### 1. Generate a key pair

```sh
ssh-keygen
## Copy the public key into the remote server GITHUB
```
### 2. Create a yaml file and push the below contents to create a secret object

```sh
apiVersion: v1
kind: Secret
metadata:
  name: private-repo-ssh
  namespace: argo-cd
stringData:
  type: git
  url: git@github.com:mohamedbenaantar/<private-repoURL>
  sshPrivateKey: <Private Key Generated>

```
#### 3. Apply or Create the object

```sh
kubectl apply -f <secret-file-name>.yaml
```

### Now you can created an application from that private repo
